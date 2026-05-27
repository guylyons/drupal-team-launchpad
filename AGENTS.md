# Drupal Site Team Workspace

This repository is organized for a small autonomous team building a new Drupal site.

## Team

- Team Lead / Integrator: `agents/team-lead.md`
- Drupal Module Developer: `agents/drupal-module-developer.md`
- Drupal Themer: `agents/drupal-themer.md`
- Writer / Content Strategist: `agents/writer-content-strategist.md`
- Designer / UX Lead: `agents/designer-ux-lead.md`

## Operating Rules

1. Keep work small and reviewable. Prefer one feature, content section, or design decision per change.
2. Every agent must read:
   - `project/site-brief.md`
   - `project/technical-standards.md`
   - `project/workflow.md`
   - their own role file under `agents/`
3. Do not invent final requirements. If a decision is missing, write it in `project/decisions.md` as an open question or assumption.
4. Drupal code should be boring and maintainable: custom code only where configuration, contributed modules, or theme layer changes are insufficient.
5. Preserve separation of concerns:
   - Module developer owns custom modules, plugins, schema, services, hooks, APIs, tests.
   - Themer owns Twig, libraries, preprocess, responsive styling, accessibility implementation.
   - Writer owns content model guidance, page copy, labels, metadata, editorial workflows.
   - Designer owns UX, information architecture, visual system, components, interaction behavior.
6. All changes should include verification notes: what was changed, how it was checked, and what remains uncertain.

## Expected Project Shape

The Drupal application is expected to live under `web/` if this becomes a Composer Drupal project. Until then, planning and agent coordination lives in this repo.

Suggested future layout:

```text
composer.json
config/sync/
web/modules/custom/
web/themes/custom/
docs/
agents/
project/
```

## Definition of Done

A task is done only when:

- The implementation or document is committed-ready.
- Relevant standards have been followed.
- Accessibility and editorial impact have been considered.
- Tests, linting, or manual verification are documented.
- Handoff notes are added where another role depends on the work.
