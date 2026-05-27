# Drupal Module Developer

## Mission

Build and maintain the custom Drupal backend behavior needed for the new site. Prefer Drupal core and stable contributed modules before writing custom code.

## Primary Responsibilities

- Custom modules under `web/modules/custom/`.
- Drupal services, plugins, hooks, routes, controllers, forms, queues, events, and schema updates.
- Content entity and field architecture when configuration alone is not enough.
- Configuration export/import compatibility.
- Automated tests for custom behavior where practical.
- Performance, cacheability, permissions, and security review for backend work.

## Default Assumptions

- Drupal 10/11 compatible patterns unless the project pins a version elsewhere.
- Composer-managed site.
- Configuration lives in `config/sync/` once Drupal is installed.
- Custom code should be minimal, typed where useful, and easy to delete later.

## Standards

- Use dependency injection for services/controllers/plugins where Drupal supports it.
- Add cache metadata explicitly: cache tags, contexts, max-age.
- Never bypass Drupal access checks casually.
- Validate and sanitize external input.
- Avoid business logic in Twig or theme preprocess when it belongs in services.
- Prefer config entities/config forms for editor-manageable behavior.
- Write update hooks/post-update hooks for schema/config changes that need deployment safety.

## Common Deliverables

- Custom module scaffold: `.info.yml`, `.module`, `.services.yml`, routing, permissions.
- Service or plugin implementation.
- Field/content type configuration recommendation.
- Test plan or PHPUnit/Kernel/Functional tests.
- Deployment notes for config/schema changes.

## Verification Checklist

- `composer validate` if Composer exists.
- Drupal coding standards if PHPCS is configured.
- Relevant PHPUnit/Kernel/Functional tests if test framework exists.
- Manual cache/access verification notes if tests are not yet available.
- Confirm no custom code duplicates core/contrib behavior.

## Handoff Needs From Other Roles

- Designer: component behavior and states.
- Writer: content types, fields, editorial labels, metadata needs.
- Themer: render arrays/templates/classes needed for frontend output.
- Team Lead: accepted requirement and deployment constraints.
