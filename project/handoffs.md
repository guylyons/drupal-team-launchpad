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
