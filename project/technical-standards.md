# Technical Standards

## Drupal Defaults

- Prefer core and mature contributed modules before custom code.
- Keep configuration exportable and reviewable.
- Use DDEV for local development.
- Use Composer for PHP dependencies.
- Use fnm for Node version management.
- Use pnpm for Node dependencies and scripts; do not add npm/yarn lockfiles.
- Avoid placing business logic in the theme layer.
- Avoid placing presentation decisions in custom modules.
- Use Drupal APIs for entity access, rendering, caching, routing, forms, and services.

## Custom Module Standards

- Path: `web/modules/custom/{module_name}`.
- Include `.info.yml` for every module.
- Use services and dependency injection where appropriate.
- Add permissions for privileged behavior.
- Add routes/controllers/forms only when configuration cannot satisfy the requirement.
- Include cache metadata on render arrays.
- Include update/post-update hooks for deployment-sensitive changes.
- Document why the module exists.

## Theme Standards

- Path: `web/themes/custom/{theme_name}`.
- Use `.libraries.yml` for assets.
- Keep Twig templates readable and mostly logic-free.
- Use preprocess functions for shaping variables, not for hidden business rules.
- Use semantic HTML.
- Support responsive layouts from the first implementation.
- Keep JavaScript small and Drupal behavior-compatible.

## Content Standards

- Content types should describe editorial concepts, not layouts.
- Fields should be reusable where useful but not abstract to the point of confusion.
- Taxonomy should exist only where it supports navigation, filtering, permissions, or editorial workflow.
- Required fields must have an editorial reason.
- Page titles, summaries, and metadata should be planned early.

## Accessibility Standards

- Target WCAG 2.2 AA unless the project chooses a stricter standard.
- Preserve heading order.
- Use descriptive links and buttons.
- Provide visible keyboard focus.
- Do not rely on color alone.
- Respect reduced motion.
- Design and test empty/error/loading states.

## Verification Standards

When tooling exists, run it. If tooling does not exist yet, document manual checks.

Preferred current checks:

```bash
composer validate
composer audit
composer lint:php
composer format:php
fnm use
pnpm install --frozen-lockfile
pnpm format:check
pnpm lint
pnpm format
```

Preferred future Drupal app checks after Composer scaffold exists:

```bash
ddev composer validate
ddev composer audit
ddev exec vendor/bin/phpcs
ddev exec vendor/bin/phpunit
```

Run commands through DDEV when they depend on PHP, Drupal, database services, or the web container. Run pnpm/fnm commands on the host unless the project later decides otherwise.

For routine Drupal operations after the app is scaffolded, follow `project/drupal-operations.md`. It is the command runbook for Composer updates, Drush, database updates, configuration import/export, cache rebuilds, module enable/uninstall, security audit, coding standards, and AI-agent execution notes.

Do not claim a check passed unless it was run.
