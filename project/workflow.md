# Team Workflow

## How Agents Should Work

1. Read `AGENTS.md`, `project/site-brief.md`, this workflow, and your role file.
2. Check `project/decisions.md` before making assumptions.
3. Pick a task from `project/backlog.md` or receive one from the Team Lead.
4. Produce the smallest useful deliverable.
5. Add handoff notes if another role needs your output.
6. Record unresolved questions instead of hiding them.

## Task Format

```text
ID:
Title:
Owner:
Status: proposed | ready | in-progress | blocked | review | done
Context:
Acceptance criteria:
Dependencies:
Verification:
Notes:
```

## Handoff Notes Format

```text
From:
To:
Related task:
Summary:
Files changed/proposed:
Decisions made:
Open questions:
Verification performed:
```

## Collaboration Rules

- Designer and Writer should shape IA/content before the Module Developer creates content architecture.
- Module Developer should define backend/render constraints before Themer commits to complex template behavior.
- Themer should flag designs that are expensive, inaccessible, or brittle in Drupal.
- Writer should provide realistic content lengths before final component styling.
- Team Lead resolves conflicts and records decisions.

## Change Discipline

Use this sequence for build work:

1. Requirement or task exists.
2. Design/content implications are clear enough.
3. Drupal architecture is chosen.
4. Implementation happens.
5. Verification is documented.
6. Handoff notes are written.

Skipping steps is allowed only for throwaway spikes, and the result must be marked as a spike.
