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
From: Writer / Content Strategist
To: Designer / UX Lead, Drupal Module Developer
Related task: T002 Draft initial sitemap and content model candidates
Summary: Added a first-pass content strategy planning document with explicit unknowns, a candidate sitemap, candidate content types and fields, taxonomy candidates, editorial workflow notes, accessibility/content concerns, and review questions.
Files changed/proposed: `project/content-strategy.md`, `project/backlog.md`, `project/handoffs.md`
Decisions made: None. This is candidate planning only; final site purpose, audiences, brand, governance, launch scope, and Drupal architecture remain open.
Open questions: Designer should review navigation shape, content density, and state/design needs. Drupal Module Developer should review feasibility, shared fields, workflow/moderation options, reusable CTA modeling, and whether any proposed structure requires contributed modules or custom code.
Verification performed: Manual content review against the site brief, technical standards, workflow, decisions log, and Writer role guidance. Ran `pnpm format:check` and `composer validate --no-check-publish`; both passed. Ran `composer lint:php`; it did not complete because `phpcs` is not installed or not available on PATH in this worktree.

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

Date: 2026-05-27
From: Drupal Module Developer
To: Team Lead, Hermes/Codex/Claude operators
Related task: T006 Document routine Drupal operations for agents
Summary: Added a Drupal operations command guide for routine Composer, Drush, database update, configuration, cache, module, security audit, coding standards, and verification workflows. Added provider-neutral guidance for Hermes, Codex, and Claude. Updated references in README, launch prompts, technical standards, decisions, and backlog.
Files changed/proposed: `project/drupal-operations.md`, `README.md`, `project/launching-agents.md`, `project/technical-standards.md`, `project/decisions.md`, `project/backlog.md`, `project/handoffs.md`
Decisions made: Use DDEV for Drupal/PHP/database operations; use host fnm/pnpm for repository formatting by default; treat Drush as the default Drupal CLI once the app is scaffolded.
Open questions: Confirm whether the user's "Josh or similar" request means Drush or another Drupal command/orchestration tool.
Verification performed: Ran `composer install` to restore missing PHP tooling, then `composer validate --no-check-publish`, `composer lint:php`, and `pnpm format:check`; all passed.
