# Decisions Log

Record durable project decisions here. Use this file instead of burying decisions in chat, code comments, or role notes.

## Accepted Decisions

- Local development uses DDEV.
- Node version management uses fnm.
- Node/package tooling uses pnpm, not npm or yarn.
- Repository formatting uses Prettier.
- Repository source is licensed under MIT.
- Drupal coding standards are checked with PHP_CodeSniffer plus Drupal Coder using `phpcs.xml.dist`.
- Theme tooling starts without Gulp; use direct pnpm scripts and Drupal libraries unless real asset-pipeline needs emerge.
- The custom theme should start from Drupal core Starterkit, with Olivero used only as a reference theme.
- Drupal baseline targets Drupal 11 unless a hosting, contributed-module, integration, or migration constraint requires Drupal 10.
- DDEV baseline uses project name `drupal-team`, docroot `web`, PHP 8.3, MySQL 8.0, Composer 2, Node.js 22, and Drupal 11 project type.

## Open Questions

- What is the site name and purpose?
- Who are the primary and secondary audiences?
- What content must be ready for launch?
- What existing content or systems need migration/integration?
- What hosting environment will run the site?
- What brand/design assets already exist?
- What is the final custom theme machine name and display name?
- What browser/device support matrix should the theme target?
- What content length examples should be used to stress-test components?
- Are Drupal-rendered component examples sufficient, or does the team need a separate component preview tool?

## Assumptions In Use

- Drupal will be Composer-managed.
- Custom code will be minimized.
- Accessibility target is WCAG 2.2 AA unless changed.
- The team should plan before creating Drupal app code.
