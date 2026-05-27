# Drupal Operations Command Guide

Date: 2026-05-27
Owner: Drupal Module Developer

This guide gives human contributors and AI coding agents a shared command vocabulary for routine Drupal work. It assumes the Drupal app will be Composer-managed with docroot `web/`, local services will run in DDEV, and configuration will export to `config/sync/` once Drupal is installed.

The current repository is still a launchpad, not a scaffolded Drupal app. Treat Drupal-specific commands below as the default runbook after the app exists and Drush is installed.

## Execution Defaults

Use DDEV for commands that need PHP, Composer packages, Drupal bootstrap, the database, the web container, or service containers:

```bash
ddev composer ...
ddev drush ...
ddev exec vendor/bin/phpcs
ddev exec vendor/bin/phpunit
```

Use the host for repository-level Node and formatting commands unless the project later decides otherwise:

```bash
fnm use
pnpm install --frozen-lockfile
pnpm format:check
pnpm lint
```

If DDEV is not running, start it first:

```bash
ddev start
```

## Drush Fit

Drush is the standard Drupal command-line tool for cache rebuilds, database updates, configuration import/export, state inspection, one-time scripts, and module/theme operations. It should be added to the Drupal app with Composer when routine Drupal operations begin:

```bash
ddev composer require drush/drush
```

After Drush exists, prefer `ddev drush ...` over host `vendor/bin/drush ...` so the command runs with the same PHP version, settings, database, and service environment as the local site.

Open clarification: the user mentioned "Josh or similar." This is likely a reference to Drush or a Drupal routine-command helper, but the intended tool is not confirmed. Until clarified, document and use Drush as the default Drupal CLI rather than adding speculative automation.

## Routine Drupal Command Matrix

| Task                           | Default command                                               | Notes                                                                        |
| ------------------------------ | ------------------------------------------------------------- | ---------------------------------------------------------------------------- |
| Start local services           | `ddev start`                                                  | Run before Drupal/Composer/database operations.                              |
| Stop local services            | `ddev stop`                                                   | Use when done or before changing DDEV config.                                |
| Install PHP dependencies       | `ddev composer install`                                       | Use after pulling Composer changes.                                          |
| Validate Composer metadata     | `ddev composer validate --no-check-publish`                   | Repo-level fallback before scaffold: `composer validate --no-check-publish`. |
| Audit PHP dependencies         | `ddev composer audit`                                         | Run before merging dependency updates.                                       |
| Require a contributed module   | `ddev composer require drupal/MODULE_NAME`                    | Do not edit `composer.json` manually unless there is a clear reason.         |
| Update one contributed module  | `ddev composer update drupal/MODULE_NAME --with-dependencies` | Review `composer.lock` carefully.                                            |
| Update Drupal core             | `ddev composer update drupal/core-* --with-dependencies`      | Run database updates, cache rebuild, and tests after.                        |
| Enable a module                | `ddev drush pm:enable MODULE_NAME -y`                         | Export config afterward if config changed.                                   |
| Uninstall a module             | `ddev drush pm:uninstall MODULE_NAME -y`                      | Confirm content/config dependencies first. Export config afterward.          |
| Run database updates           | `ddev drush updatedb -y`                                      | Use after code or dependency updates that add update hooks.                  |
| Import config                  | `ddev drush config:import -y`                                 | Pulls `config/sync/` into the active site.                                   |
| Export config                  | `ddev drush config:export -y`                                 | Review exported YAML before committing.                                      |
| Check config status            | `ddev drush config:status`                                    | Useful before/after import/export.                                           |
| Rebuild cache                  | `ddev drush cache:rebuild`                                    | Run after enabling modules, imports, routing/service changes.                |
| One-time login link            | `ddev drush user:login`                                       | For local admin access only.                                                 |
| Drupal status                  | `ddev drush status`                                           | Confirms bootstrap, database, paths, and versions.                           |
| Coding standards               | `ddev exec vendor/bin/phpcs --standard=phpcs.xml.dist`        | Repo-level fallback before scaffold: `composer lint:php`.                    |
| Fix coding standards           | `ddev exec vendor/bin/phpcbf --standard=phpcs.xml.dist`       | Review automated fixes.                                                      |
| Run PHP tests                  | `ddev exec vendor/bin/phpunit`                                | Use more specific test suites when configured.                               |
| Format docs/frontend assets    | `pnpm format`                                                 | Runs on host by default.                                                     |
| Check docs/frontend formatting | `pnpm format:check`                                           | Run before commit.                                                           |

## Safe Module Update Runbook

Use this sequence for a contributed module update. Replace `MODULE_NAME` with the Composer package suffix, for example `pathauto` for `drupal/pathauto`.

```bash
ddev start
ddev composer validate --no-check-publish
ddev composer audit
ddev composer update drupal/MODULE_NAME --with-dependencies
ddev drush updatedb -y
ddev drush cache:rebuild
ddev drush config:status
pnpm format:check
```

If the update changes configuration, export and review it:

```bash
ddev drush config:export -y
git diff -- config/sync composer.json composer.lock
```

Before committing, run available project checks and record anything unavailable:

```bash
ddev composer validate --no-check-publish
ddev composer audit
ddev exec vendor/bin/phpcs --standard=phpcs.xml.dist
pnpm format:check
```

## Config Change Runbook

When making Drupal admin UI changes locally:

```bash
ddev drush config:status
ddev drush config:export -y
git diff -- config/sync
```

When applying another contributor's exported config:

```bash
ddev composer install
ddev drush updatedb -y
ddev drush config:import -y
ddev drush cache:rebuild
ddev drush config:status
```

Do not commit active-site-only changes. Durable Drupal configuration should be exported to `config/sync/` unless a documented deployment reason says otherwise.

## Security Audit Baseline

Run Composer audit for PHP package advisories:

```bash
ddev composer audit
```

After Drupal is scaffolded, add a project decision for any additional security tooling, such as Drupal security advisory monitoring, hosting/platform scans, or CI dependency review. Do not treat `composer audit` as a complete Drupal security review.

## Provider-Neutral Agent Guidance

Any AI coding agent should execute commands through the repository shell it has available and should report exact commands and results. Agents must not claim a check passed unless they ran it.

### Hermes

Hermes can run shell commands directly. A useful instruction pattern is:

```text
Read project/drupal-operations.md. For Drupal/PHP/database work, use DDEV commands such as `ddev composer ...` and `ddev drush ...`. For repo formatting, use host `pnpm ...`. Run the relevant verification commands and report exact results.
```

Example routine update prompt:

```text
Update contributed module drupal/MODULE_NAME. Follow project/drupal-operations.md, use DDEV for Composer/Drush commands, export config only if it changes, run available checks, and commit the result with verification notes.
```

### Codex

Codex-style CLI agents can use the same runbook. A useful instruction pattern is:

```text
You are working in a Drupal/DDEV repository. Read project/drupal-operations.md before running commands. Use `ddev composer` for Composer, `ddev drush` for Drupal operations, and host `pnpm` for repository formatting. Keep changes small and include command output summaries in the final response.
```

### Claude / Claude Code

Claude Code-style agents can use the same command matrix. A useful instruction pattern is:

```text
Follow project/drupal-operations.md. Prefer concrete command execution over proposed steps. Use DDEV for PHP, Composer, Drush, database updates, config import/export, and cache rebuilds. Use host pnpm/fnm for Node formatting. Stop and report if Drush, DDEV, Composer dependencies, or the Drupal app scaffold are missing.
```

## Missing Tooling Behavior

If a command is unavailable, report the exact failure and the likely missing prerequisite. Common examples:

- `ddev: command not found`: DDEV is not installed on the host.
- `Command "drush" is not defined` or `ddev drush` fails: Drush is not installed yet or Drupal is not scaffolded.
- `vendor/bin/phpcs: No such file or directory`: Composer dependencies are not installed.
- `Cannot bootstrap Drupal`: Drupal is not installed, settings are missing, or the database is unavailable.

Do not paper over missing tooling by inventing success. Either install dependencies when that is in scope or record the failed check in the handoff.
