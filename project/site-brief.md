# Site Brief

## Working Premise

This is a new Drupal site. The exact organization, audience, brand, and launch requirements are not defined yet. Until those are clarified, the team should build reusable planning assets and avoid irreversible assumptions.

## Site Goals

To be completed by the Team Lead with input from the user.

```text
Organization/site owner:
Primary audience:
Secondary audiences:
Top user tasks:
Top site owner goals:
Launch deadline:
Required integrations:
Required compliance/accessibility constraints:
Hosting/deployment constraints:
Existing content source:
```

## Initial Product Principles

- Make the site easy to edit without developer help.
- Use Drupal configuration and contributed modules before custom code.
- Keep custom module code small, tested, and clearly justified.
- Build a theme that supports real content, not just mockups.
- Make accessibility part of the build, not a launch cleanup task.
- Treat content modeling as a core architecture decision.

## Initial Drupal Assumptions

These are defaults, not final decisions:

- Drupal 11 unless project constraints require Drupal 10.
- Composer-managed build.
- DDEV local development with docroot `web/`.
- fnm-managed Node.js using the version in `.fnmrc` / `.node-version`.
- pnpm for Node/package scripts; do not introduce npm/yarn lockfiles.
- Custom module path: `web/modules/custom/`.
- Custom theme path: `web/themes/custom/`.
- Config export path: `config/sync/`.

## Open Questions

- What is the site for?
- Who owns the content after launch?
- What existing systems need integration?
- Is there an existing brand/design system?
- Are there legal, privacy, public-sector, or accessibility requirements beyond WCAG 2.2 AA?
- What content must exist at launch?
- What does success look like 30 days after launch?
