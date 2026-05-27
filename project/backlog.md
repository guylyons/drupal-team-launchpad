# Backlog

## Ready Soon

### T001: Define site owner, audience, and launch goals

Owner: Team Lead
Status: proposed

Context: The team needs a real brief before implementation.

Acceptance criteria:

- `project/site-brief.md` has organization, audience, goals, launch constraints, and integrations filled in.
- Open questions are moved to `project/decisions.md`.

Verification:

- User has reviewed and accepted the brief.

### T002: Draft initial sitemap and content model candidates

Owner: Writer / Content Strategist
Status: review

Context: Drupal architecture should follow content needs.

Acceptance criteria:

- Candidate sitemap exists.
- Candidate content types and fields are listed.
- Unknowns are marked explicitly.

Verification:

- Designer and Module Developer review for feasibility.

### T003: Define visual direction and component inventory

Owner: Designer / UX Lead
Status: review

Context: Themer needs implementable component specs.

Acceptance criteria:

- Initial component list exists.
- Design tokens are proposed.
- Responsive and accessibility notes are included.
- UX onboarding, state, and handoff checklists are documented.

Verification:

- Themer reviews for frontend feasibility.
- Team Lead confirms the design starter is useful before converting it into implementation tasks.

### T004: Finalize Drupal baseline within DDEV

Owner: Drupal Module Developer
Status: review

Context: Local development is DDEV, Node is managed by fnm, and frontend tooling uses pnpm. Drupal version and Composer scaffold still need final confirmation.

Acceptance criteria:

- Drupal version target is confirmed, defaulting to Drupal 11 unless constraints require Drupal 10.
- DDEV config is reviewed for docroot, PHP version, database, Node version, and project name.
- Initial Composer project scaffold recommendation is written.
- pnpm/fnm expectations are documented for any theme build tooling.

Verification:

- Team Lead accepts constraints and tradeoffs.

### T005: Theme scaffold plan

Owner: Drupal Themer
Status: review

Context: Theme implementation should wait for baseline decisions but can be planned now.

Acceptance criteria:

- Theme name/path proposed.
- CSS/JS organization proposed.
- Base template/component approach documented.

Verification:

- Theme tooling plan added in `project/theme-tooling.md`.
- Designer and Module Developer review handoff assumptions.

### T006: Document routine Drupal operations for agents

Owner: Drupal Module Developer
Status: done

Context: Human and AI contributors need concrete, provider-neutral commands for common Drupal operations before app scaffolding begins.

Acceptance criteria:

- Composer updates, Drupal database updates, configuration import/export, cache rebuilds, module enable/uninstall, security audit, coding standards, DDEV vs host execution, and Drush usage are documented.
- Hermes, Codex, and Claude command guidance is provider-neutral and concrete.
- The uncertain "Josh or similar" request is recorded as an open clarification rather than implemented speculatively.

Verification:

- Documentation review plus repository checks recorded in `project/handoffs.md`.

## Parking Lot

- Accessibility test tooling decision.
- Content migration source discovery.
- Hosting/deployment target.
- Analytics/privacy requirements.
- Search requirements.
- Multilingual requirements.
- Browser/device support matrix.
- Existing brand/design system source.
