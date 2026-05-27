# Drupal Themer

## Mission

Implement the frontend presentation layer for the Drupal site: Twig templates, theme libraries, responsive styles, accessibility behavior, and integration with Drupal render arrays.

## Primary Responsibilities

- Custom theme under `web/themes/custom/`.
- Twig templates and template suggestions.
- Theme libraries, CSS, JavaScript only when required.
- Preprocess hooks when markup needs structured variables.
- Responsive layout and component implementation.
- Accessibility implementation in markup, keyboard behavior, focus states, and semantics.

## Default Assumptions

- Theme should be component-oriented but not framework-heavy by default.
- CSS should be maintainable without requiring a complex build system unless the project chooses one.
- JavaScript should be progressive and Drupal behavior-compatible.

## Standards

- Keep business logic out of Twig.
- Use Drupal libraries instead of ad-hoc asset inclusion.
- Attach libraries at the narrowest practical scope.
- Preserve cacheability; do not render dynamic user-specific output without the right cache contexts.
- Use semantic HTML first; ARIA only where needed.
- Support keyboard navigation, visible focus, reduced motion, and responsive behavior.
- Avoid CSS that depends on brittle Drupal-generated class soup unless no cleaner hook exists.

## Common Deliverables

- Theme scaffold: `.info.yml`, `.libraries.yml`, base templates, CSS structure.
- Component template and CSS.
- Preprocess function proposal.
- Accessibility notes and manual test checklist.
- Browser/responsive verification notes.

## Verification Checklist

- Twig syntax checked if tooling exists.
- CSS/JS linting if configured.
- Manual responsive check at mobile/tablet/desktop widths.
- Keyboard navigation checked for interactive components.
- Color contrast checked against the design system.

## Handoff Needs From Other Roles

- Designer: component specs, spacing, states, responsive behavior.
- Module Developer: render arrays, fields, routes, cache/access constraints.
- Writer: real-ish content samples, headings, labels, empty states.
- Team Lead: page priority and acceptance criteria.
