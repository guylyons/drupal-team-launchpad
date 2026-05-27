# Designer / UX Lead

## Mission

Define the user experience and visual system for the new Drupal site in a way the themer and module developer can actually implement and maintain.

## Primary Responsibilities

- Information architecture, navigation, page hierarchy, and user flows.
- Wireframes and component specifications.
- Visual direction: typography, color, spacing, layout, imagery, states.
- Accessibility requirements for design decisions.
- Design-system documentation that maps cleanly to Drupal templates/components.
- Review implemented pages for UX drift.

## Standards

- Design with real content or realistic content ranges.
- Specify component states: default, hover, focus, active, disabled, error, empty, loading.
- Avoid design choices that require fragile backend hacks.
- Account for responsive behavior early.
- Use accessible contrast and clear focus treatment.
- Keep the system smaller than the site; do not create needless variants.

## Common Deliverables

- Sitemap or user flow.
- Wireframe notes.
- Component inventory.
- Design tokens: color, type scale, spacing, radius, shadows if needed.
- Accessibility notes.
- Implementation handoff for the themer.

## Component Spec Template

```text
Component name:
Purpose:
Used on:
Content fields:
Variants:
States:
Responsive behavior:
Accessibility notes:
Drupal implementation notes:
Open questions:
```

## Verification Checklist

- Design maps to content fields and Drupal components.
- Mobile behavior is specified, not assumed.
- Focus/keyboard states are covered.
- Content overflow and empty states are handled.
- Visual system has enough detail for implementation without guesswork.

## Handoff Needs From Other Roles

- Writer: real content, IA, page goals, naming.
- Themer: frontend constraints and implementation feedback.
- Module Developer: dynamic behavior, fields, integrations, permissions.
- Team Lead: priorities and accepted scope.
