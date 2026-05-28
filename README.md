<p align="center">
  <img src="docs/assets/logo.svg" alt="Drupal Team Launchpad logo" width="180">
</p>

# Drupal Team Launchpad

A small, boring Drupal 11 workspace for human and AI-assisted site work.

It includes DDEV, Composer, Drush, pnpm, Prettier, Drupal coding standards, role briefs, planning docs, and copy-paste Hermes commands. The Drupal app lives in `web/`.

## Quick start

```bash
./scripts/dev        # install dependencies and run checks
./scripts/dev --ddev # also start DDEV
```

Then open the local site:

```bash
ddev launch
```

Useful shortcuts:

```bash
pnpm check                         # repo formatting + Composer validation + PHP coding standards
pnpm agent:next                    # print a Hermes Team Lead review command
pnpm hermes:check                  # print a Hermes battle-test command
pnpm hermes:update-core            # print a Hermes Drupal core update command
pnpm hermes:update-package drupal/pathauto
pnpm hermes:module drupal/pathauto # require + enable a contributed module
```

## Daily commands

```bash
ddev start
pnpm check
ddev drush status
ddev drush cache:rebuild
```

Drupal/PHP/database commands should run through DDEV. Host-side docs and formatting commands can run directly with pnpm/fnm.

## Drupal maintenance

Update Drupal core:

```bash
ddev start
ddev composer validate --no-check-publish
ddev composer audit
ddev composer update 'drupal/core-*' --with-dependencies
ddev drush updatedb -y
ddev drush cache:rebuild
ddev drush config:status
pnpm check
```

Update one contributed package:

```bash
ddev start
ddev composer update drupal/MODULE_NAME --with-dependencies
ddev drush updatedb -y
ddev drush cache:rebuild
ddev drush config:status
pnpm check
```

Require and enable a module:

```bash
ddev start
ddev composer require drupal/MODULE_NAME
ddev drush pm:enable MODULE_NAME -y
ddev drush updatedb -y
ddev drush cache:rebuild
ddev drush config:export -y
ddev drush config:status
pnpm check
```

More operations detail is in `project/drupal-operations.md`.

## Working with AI agents

Keep prompts narrow: one role, one task, explicit verification.

Examples:

```bash
pnpm agent:next
pnpm hermes:check
pnpm hermes:update-core
pnpm hermes:update-package drupal/pathauto
```

The generated commands tell Hermes to read the runbooks, use DDEV for Drupal work, run checks, and stop/report instead of inventing requirements.

Role briefs live in `agents/`:

- `agents/team-lead.md`
- `agents/drupal-module-developer.md`
- `agents/drupal-themer.md`
- `agents/writer-content-strategist.md`
- `agents/designer-ux-lead.md`

## Project map

```text
AGENTS.md                 team operating rules
agents/                   role briefs
project/                  brief, backlog, decisions, handoffs, runbooks
.ddev/                    local Drupal services
config/sync/              expected exported config location, if adopted
web/                      Drupal docroot
scripts/dev               setup/check/start helper
scripts/hermes-command    copy-paste Hermes command generator
composer.json             Drupal/PHP dependencies and PHPCS scripts
package.json              pnpm scripts and formatting tools
```

## Rules that matter

- Keep changes small and reviewable.
- Record durable decisions in `project/decisions.md`.
- Add handoff notes in `project/handoffs.md` when another role depends on the work.
- Prefer Drupal configuration and mature contributed modules before custom code.
- Use Starterkit for a future custom theme; use Olivero only as a reference.
- Do not claim checks passed unless they were actually run.

## Quality bar

Before calling work done, report:

- files changed
- commands run and results
- assumptions still open
- handoffs needed

Baseline check:

```bash
pnpm check
```

For Drupal changes, also run the relevant DDEV/Drush commands from `project/drupal-operations.md`.

## License

MIT. See `LICENSE`.
