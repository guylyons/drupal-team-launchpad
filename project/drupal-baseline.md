# Drupal Baseline for Team Lead Review

Date: 2026-05-27
Owner: Drupal Module Developer
Related task: T004 Finalize Drupal baseline within DDEV

## Recommendation

Target Drupal 11 for the baseline.

No current project constraint requires Drupal 10. The existing DDEV and coding-standard files already align with Drupal 11:

- `.ddev/config.yaml` uses `type: drupal11`.
- `phpcs.xml.dist` sets `drupal_core_version` to `11`.
- `project/site-brief.md` defaults to Drupal 11 unless constraints require Drupal 10.

Drupal 10 should remain a fallback only if a future hosting, contributed-module, integration, or migration constraint makes Drupal 11 impractical.

## DDEV Config Review

Reviewed file: `.ddev/config.yaml`

| Area         | Current value | Review note                                                                                   |
| ------------ | ------------- | --------------------------------------------------------------------------------------------- |
| Project name | `drupal-team` | Conservative local project name. Rename only if the final site/project name changes.          |
| DDEV type    | `drupal11`    | Matches the recommended Drupal 11 target.                                                     |
| Docroot      | `web`         | Matches Composer Drupal project convention and existing repo assumptions.                     |
| PHP version  | `8.3`         | Suitable for Drupal 11 and conservative for current local development.                        |
| Web server   | `nginx-fpm`   | Standard DDEV Drupal setup.                                                                   |
| Database     | MySQL `8.0`   | Suitable default unless hosting dictates MariaDB or another version.                          |
| Composer     | `2`           | Correct for Drupal Composer workflows.                                                        |
| Node.js      | `22`          | Matches `.fnmrc`, `.node-version`, and `package.json` engine range.                           |
| Corepack     | `true`        | Useful with `packageManager: pnpm@9.15.4`; host-side pnpm remains the default unless changed. |

No DDEV service additions are recommended yet. Add committed `.ddev/docker-compose.*.yaml` files only when the Drupal app actually needs services such as Solr, Redis, Mailpit customization, or external integration mocks.

## Composer Scaffold Recommendation

Do not scaffold the full Drupal application until the Team Lead accepts the baseline and confirms any hosting or integration constraints.

When accepted, start from Drupal's Composer-managed project template for Drupal 11 and preserve the existing repo planning/tooling files:

```bash
# Use DDEV for PHP/Composer once the app is being created.
ddev start

# Scaffold into a temporary directory because this repository is not empty.
mkdir -p .tmp/drupal-recommended-project
ddev composer create-project drupal/recommended-project:^11 .tmp/drupal-recommended-project --no-interaction

# Then merge the generated Drupal app files into this repo deliberately,
# preserving existing project/, agents/, docs/, README, license, formatting,
# PHPCS, pnpm, fnm, and DDEV files. Remove .tmp/ after the merge.
```

Expected resulting Drupal app shape:

```text
composer.json
composer.lock
config/sync/
web/core/
web/modules/custom/
web/themes/custom/
web/sites/default/
```

Recommended Composer baseline after scaffold:

- Use `drupal/core-recommended` through the recommended-project template.
- Keep `drupal/core-composer-scaffold` so Drupal scaffold files are Composer-managed.
- Keep `drupal/core-project-message` unless the Team Lead wants quieter Composer output.
- Add Drush only when the team needs command-line Drupal operations.
- Retain PHP_CodeSniffer plus Drupal Coder for custom PHP, module, theme, install, profile, and test code.
- Do not overwrite existing repo tooling blindly; merge intentionally and review the Composer script/config differences.

## fnm, pnpm, and Theme Tooling Expectations

Current files reviewed:

- `.fnmrc`: `22`
- `.node-version`: `22`
- `.npmrc`: strict package-manager and frozen-lockfile expectations
- `package.json`: `packageManager: pnpm@9.15.4`, Node `>=22 <27`, pnpm `>=9 <10`
- `pnpm-lock.yaml`: present
- `project/theme-tooling.md`: no Gulp; direct pnpm scripts and Drupal libraries first

Expectations:

- Use `fnm use` before running Node tooling.
- Use `pnpm install --frozen-lockfile`; do not introduce `package-lock.json` or `yarn.lock`.
- Run Prettier through `pnpm format:check` / `pnpm format`.
- Keep theme asset tooling minimal: Drupal libraries, plain CSS, and small Drupal behaviors first.
- Add stylelint, eslint, PostCSS, Sass, or bundling only when real theme requirements justify them and after Team Lead/Themer review.
- Do not add Gulp, Vite, Webpack, Sass, or Storybook for the baseline.

## Tradeoffs

- Choosing Drupal 11 now aligns with current Drupal direction and existing repo configuration, but a future hosting/contrib constraint could force Drupal 10.
- Keeping DDEV minimal avoids premature service maintenance, but later integrations may require additional DDEV services.
- Waiting to scaffold Drupal avoids overwriting this planning repository, but it means Team Lead review still precedes the full application skeleton.
- Keeping Node tooling host-side with fnm/pnpm is simple for theme work, while DDEV remains the source of truth for PHP/Drupal/database workflows.

## Open Questions for Team Lead

- Is there any hosting constraint that limits PHP, database, or Drupal major version support?
- Are any required contributed modules or integrations known to be incompatible with Drupal 11?
- Should the final DDEV project name remain `drupal-team` or change when the site name is known?
- Should Drush be included in the initial Composer scaffold, or added only once Drupal operations require it?
- Does the target hosting environment use MySQL 8.0, MariaDB, or another database/version?

## Verification

Tooling verification is recorded in the T004 handoff after checks are run. Team Lead acceptance is still required for the Drupal 11 baseline and scaffold tradeoffs.
