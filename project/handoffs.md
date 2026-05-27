# Handoffs

Use this file for cross-role coordination notes.

## Template

```text
Date:
From:
To:
Related task:
Summary:
Files changed/proposed:
Decisions made:
Open questions:
Verification performed:
```

## Active Handoffs

Date: 2026-05-27
From: Drupal Themer / Team Lead
To: Designer / UX Lead, Drupal Module Developer
Related task: T005 Theme scaffold plan
Summary: Added a theme tooling plan recommending no Gulp for the baseline, Drupal core Starterkit as the custom theme starting point, and direct pnpm scripts/Drupal libraries before any heavier asset pipeline.
Files changed/proposed: `project/theme-tooling.md`, `project/decisions.md`, `project/backlog.md`, `README.md`
Decisions made: Start without Gulp. Use Drupal core Starterkit for the initial custom theme scaffold. Treat Olivero as a reference, not a base theme.
Open questions: Final theme name, browser/device support, existing brand/design-token source, need for component previews outside Drupal, and whether target hosting allows relying on Drupal aggregation/minification.
Verification performed: Ran `pnpm format:check`, `composer validate --no-check-publish`, and `composer lint:php` after edits.

Date: 2026-05-27
From: Drupal Module Developer
To: Team Lead, Drupal Themer, Writer / Content Strategist
Related task: T004 Finalize Drupal baseline within DDEV
Summary: Documented the recommended Drupal 11 baseline, reviewed existing DDEV/PHP/database/Node settings, outlined a conservative Composer scaffold approach for a non-empty repository, and confirmed fnm/pnpm expectations for future theme tooling.
Files changed/proposed: `.ddev/config.yaml` reviewed; `project/drupal-baseline.md`, `project/decisions.md`, `project/backlog.md`, `project/handoffs.md`
Decisions made: Recommend Drupal 11 by default; keep DDEV docroot `web`, PHP 8.3, MySQL 8.0, Composer 2, Node.js 22, project name `drupal-team`; do not scaffold the full Drupal app until Team Lead accepts baseline constraints.
Open questions: Hosting/database constraints; any Drupal 11-incompatible contrib/integration requirements; final DDEV project name; whether Drush belongs in the initial scaffold or later.
Verification performed: Ran `composer install` and `pnpm install --frozen-lockfile` to restore missing local dependencies, then ran `composer validate --no-check-publish`, `composer lint:php`, and `pnpm format:check`.
