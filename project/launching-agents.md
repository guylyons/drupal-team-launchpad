# Launching The Team

These role files are written so a Hermes/Codex/Claude-style coding agent can be started with a clear brief.

## Recommended Agent Prompt Pattern

```text
You are working in this repository as the {ROLE}.
Read AGENTS.md, project/site-brief.md, project/workflow.md, project/technical-standards.md, project/decisions.md, project/backlog.md, and agents/{ROLE_FILE}. Then take task {TASK_ID}. Keep changes small, document assumptions, and update project/handoffs.md if another role depends on your output.
```

## Example Hermes One-Shot Commands

Run these from the repository root. Use worktree mode for agents that will edit code concurrently once this becomes a real Drupal app.

```bash
hermes chat -q "You are the Team Lead / Integrator. Read AGENTS.md and agents/team-lead.md. Review project/backlog.md and prepare the next three ready tasks."

hermes chat -q "You are the Drupal Module Developer. Read AGENTS.md and agents/drupal-module-developer.md. Take T004 from project/backlog.md and propose the Drupal baseline/local dev stack."

hermes chat -q "You are the Drupal Themer. Read AGENTS.md and agents/drupal-themer.md. Take T005 from project/backlog.md and draft the theme scaffold plan."

hermes chat -q "You are the Writer / Content Strategist. Read AGENTS.md and agents/writer-content-strategist.md. Take T002 from project/backlog.md and draft a candidate sitemap/content model."

hermes chat -q "You are the Designer / UX Lead. Read AGENTS.md and agents/designer-ux-lead.md. Take T003 from project/backlog.md and draft the component inventory/design token starting point."

hermes chat -q "You are the Designer / UX Lead. Read AGENTS.md, project/site-brief.md, project/content-strategy.md, project/design-start.md, project/decisions.md, project/theme-tooling.md, and agents/designer-ux-lead.md. Review one page flow or component for IA, responsive states, accessibility, and Drupal implementation handoff gaps."
```

## Parallel Work Guidance

Do not run parallel editing agents against the same files unless each has a clear ownership boundary. Safe early split:

- Writer edits `project/content-*` docs.
- Designer edits `project/design-*` docs.
- Module Developer edits `project/drupal-architecture.md` or future `web/modules/custom/`.
- Themer edits `project/theme-plan.md` or future `web/themes/custom/`.
- Team Lead edits backlog, decisions, and handoffs.

## First Useful Sequence

1. Team Lead fills missing brief questions with the user.
2. Writer drafts sitemap/content model.
3. Designer drafts component inventory and visual direction.
4. Module Developer proposes Drupal baseline and content architecture.
5. Themer proposes theme scaffold and component implementation approach.
6. Team Lead reconciles conflicts and converts the plan into implementation tasks.
