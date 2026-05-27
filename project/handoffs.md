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
