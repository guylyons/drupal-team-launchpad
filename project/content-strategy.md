# Content Strategy Candidates

## Purpose

This is a first-pass sitemap and content model candidate for Drupal planning. It is not a final information architecture or requirements document. The site purpose, audience, brand, content ownership, launch scope, and integrations are still unknown.

## Assumptions and Unknowns

### Assumptions in use

- Drupal architecture should follow content needs, not page mockups.
- Content types should describe editorial concepts, not layouts.
- Editors should be able to maintain common pages without developer help.
- Accessibility target is WCAG 2.2 AA unless the project chooses a stricter standard.
- Custom code should be avoided unless configuration and contributed modules cannot meet a confirmed need.

### Explicit unknowns

- Site name and organization/site owner.
- Primary and secondary audiences.
- Primary user tasks and site owner goals.
- Launch deadline and launch content scope.
- Existing content sources, migration needs, and content quality.
- Required integrations such as CRM, newsletter, commerce, events, search, analytics, or identity.
- Brand voice, visual direction, imagery standards, and design system.
- Legal, privacy, accessibility, multilingual, or public-sector requirements beyond the current defaults.
- Content governance: owner, reviewer, approver, archiving policy, and post-launch maintenance capacity.

## Candidate Sitemap

Use this as a neutral starting structure until the site purpose is known.

```text
Home
About
  Mission / Overview
  Team / Leadership
  Contact
What We Do / Services / Programs
  Listing page
  Detail pages
Resources / Insights
  Listing page
  Article pages
  Guide / Download pages
News / Updates
  Listing page
  News item pages
Events
  Listing page
  Event detail pages
Get Involved / Work With Us
  Primary conversion page
  Form or contact path
Search
Privacy / Terms / Accessibility statement
```

### Sitemap notes

- Labels such as "What We Do," "Services," "Programs," and "Get Involved" are placeholders until the site purpose and audience language are known.
- If the site is mainly informational, "Resources" and "News" may be enough and "Events" may be removed.
- If the site is service-oriented, service/program detail pages may become the primary content type.
- If the site is campaign, product, or community oriented, this sitemap will need revision before Drupal fields are finalized.

## Candidate Content Types and Fields

Fields below are editorial candidates. Field names are plain-language labels, not final Drupal machine names.

### Basic page

Use for stable evergreen pages such as About, Contact, Privacy, and Accessibility statement.

Candidate fields:

- Title, required.
- Short summary, recommended for previews and metadata.
- Main body, required when the page has substantive content.
- Optional call to action: label, link, and short supporting text.
- Related content, optional.
- Metadata title, optional override.
- Metadata description, recommended.
- Review date, recommended for governance.
- Content owner, recommended if ownership is known.

### Landing page

Use for major navigation destinations that introduce a section and guide users to child content. This is an editorial concept, not a layout promise.

Candidate fields:

- Title, required.
- Introduction / page summary, required.
- Featured links or related items, optional.
- Primary call to action, optional.
- Supporting content references, optional.
- Metadata title and description.
- Review date and content owner.

### Article / Insight

Use for authored editorial content, thought pieces, updates with lasting value, or resource-style writing.

Candidate fields:

- Title, required.
- Deck / short summary, required for listings.
- Body, required.
- Author or source, optional until publishing model is known.
- Publication date, required if used in chronological listings.
- Topic terms, optional pending taxonomy decision.
- Audience terms, optional pending audience decision.
- Featured image, optional, with alt text guidance.
- Related content, optional.
- Metadata title and description.

### News item

Use for timely announcements where date and organizational context matter.

Candidate fields:

- Title, required.
- Summary, required for listings.
- Body, required.
- Publication date, required.
- News type, optional taxonomy candidate.
- Contact or source, optional.
- Related links, optional.
- Metadata title and description.
- Archive/review date, recommended.

### Event

Use only if events are confirmed as launch content or likely near-term content.

Candidate fields:

- Title, required.
- Summary, required for listings.
- Description, required.
- Start date/time, required.
- End date/time, optional but recommended.
- Location: online, physical, or hybrid.
- Registration link or instructions, optional.
- Event type, optional taxonomy candidate.
- Related content, optional.
- Metadata title and description.
- Archive behavior, required before implementation.

### Service / Program / Offering

Use only if the site needs structured pages for things the organization offers.

Candidate fields:

- Title, required.
- Plain-language summary, required.
- Who it is for, required if audiences are known.
- What the user can do here / next step, required.
- Eligibility, cost, timing, or requirements, optional and project-dependent.
- Primary contact or action link, optional.
- Related resources, optional.
- Topic or service category terms, optional.
- Metadata title and description.
- Review date and content owner, recommended.

### Person / Team member

Use only if people profiles are required and maintained.

Candidate fields:

- Name, required.
- Role/title, recommended.
- Short biography, optional.
- Contact details, optional and privacy-dependent.
- Photo, optional, with alt text guidance.
- Team/department term, optional.
- Sort order or weight, optional if manual ordering is needed.

### Reusable CTA / Promo candidate

Use only if editors need reusable calls to action across many pages. Avoid this if a simple link field is enough.

Candidate fields:

- Title/internal label, required.
- Public heading, optional.
- Supporting text, optional.
- Link label and URL, required.
- Audience or topic terms, optional.
- Usage notes, optional for editors.

## Taxonomy Candidates

Only create taxonomy where it supports navigation, filtering, permissions, reporting, or editorial workflow.

- Topic: broad subject areas for articles, resources, services, and news. Unknown until site purpose is known.
- Audience: useful if content differs by user group. Unknown until audiences are known.
- Content format: article, guide, download, video, external link. Useful only if Resources needs filtering.
- Service / program category: useful if offerings exist and users browse by need.
- Event type: useful only if events exist and need filtering.
- Organization / team: useful for people, ownership, or departmental publishing.
- Workflow status or review priority: usually better handled by editorial workflow fields/configuration than public taxonomy.

## Metadata and Editorial Workflow Notes

- Plan metadata early: every indexable page should have a clear title and description source.
- Require summaries for content that appears in listings or social previews.
- Do not make many fields required until editorial value is proven.
- Include review dates for evergreen pages, services/programs, and policy-style content.
- Track content owner if the organization can name one; otherwise keep ownership as an open governance question.
- Candidate workflow states: Draft, Needs review, Approved, Published, Archived. This needs Module Developer feasibility review before implementation.
- Candidate roles: Author, Editor, Approver, Administrator. Final roles depend on governance.
- Archive behavior is unknown for time-based content. Events and news need a policy before build.
- Migration is unknown. If existing content exists, perform inventory before finalizing fields.

## Accessibility and Content Concerns

- Use descriptive page titles and headings that form a useful outline.
- Link text should make sense out of context; avoid "click here" and vague repeated labels.
- Images need meaningful alt text guidance and a way to mark decorative images.
- Do not rely on color, placement, or imagery alone to communicate meaning.
- Keep summaries concise and human-readable for cards, search results, and metadata.
- Avoid PDF-first publishing unless there is a confirmed legal or operational reason.
- Forms, downloads, media, captions, transcripts, and multilingual needs remain unknown.
- Content length examples are needed before final component styling.

## Review Questions

### For Designer / UX Lead

- Does the candidate sitemap support a clear navigation model without overcommitting to unknown audience needs?
- Which landing pages need design exploration first?
- What content lengths are needed for cards, teasers, hero areas, navigation labels, and calls to action?
- Are any proposed content concepts too layout-specific or too vague for design work?
- What empty states, listing states, search/filter states, and error states should be designed early?

### For Drupal Module Developer

- Are the candidate content types feasible with Drupal core fields and configuration?
- Which fields should be shared across content types, and which should remain type-specific?
- Which candidates would require contributed modules or custom code?
- Should reusable CTAs/promos be content entities, paragraphs, blocks, or simple fields?
- What workflow, moderation, revision, scheduling, and archive behavior can be handled with configuration?
- What decisions are needed before content architecture is implemented in Drupal?

## Verification Notes

- Checked against `project/site-brief.md`, `project/technical-standards.md`, `project/workflow.md`, `project/decisions.md`, and `agents/writer-content-strategist.md`.
- Kept unknown site purpose, audience, brand, launch scope, and governance explicit.
- No Drupal app code was added.
- Ran `pnpm format:check`; it passed.
- Ran `composer validate --no-check-publish`; it passed.
- Ran `composer lint:php`; it did not complete because `phpcs` is not installed or not available on PATH in this worktree.
- Designer and Drupal Module Developer review is required before using this as implementation guidance.
