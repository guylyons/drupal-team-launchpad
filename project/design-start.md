# Design Start Guide

Date: 2026-05-27
Owner: Designer / UX Lead
Related task: T003 Define visual direction and component inventory

## Purpose

This guide gives the next designer, themer, or agent a fast UX starting point without pretending discovery is complete. It translates the current brief, content strategy, Drupal baseline, and theme tooling plan into implementable design planning assets.

Use this before wireframes, theme scaffolding, or component implementation.

## First 30 Minutes Checklist

1. Read these in order:
   - `AGENTS.md`
   - `project/site-brief.md`
   - `project/content-strategy.md`
   - `project/decisions.md`
   - `project/theme-tooling.md`
   - `project/technical-standards.md`
   - `agents/designer-ux-lead.md`
2. Identify what is known vs unknown:
   - audience
   - top user tasks
   - launch content
   - brand/design assets
   - browser/device support
   - accessibility/compliance constraints
3. Choose one design deliverable, not a full system:
   - navigation model
   - homepage wireframe notes
   - listing/detail pattern
   - component spec for one content type
   - token starter for theme scaffolding
4. Record open questions in `project/decisions.md` if they affect durable direction.
5. Add handoff notes in `project/handoffs.md` when another role needs to act.

## UX Intake Questions

Ask these before final IA or visual decisions. If the user cannot answer, keep the item as an assumption or open question.

### Audience and Tasks

- Who is the primary audience and what are they trying to do in one visit?
- Which audience has the highest launch priority?
- What should users be able to find from the homepage without search?
- What language does the audience use for the main offerings or topics?
- What task should be faster, clearer, or more trustworthy than on the current site?

### Content and Governance

- Which content exists now, and where is it stored?
- Which pages/content types must launch on day one?
- Who can create, review, approve, publish, and archive content?
- What content gets stale quickly and needs review dates or owner fields?
- Are downloads, media, events, forms, or external resources launch-critical?

### Brand and Constraints

- Is there an existing logo, color palette, typography system, or design system?
- Are there public-sector, legal, privacy, or accessibility requirements beyond WCAG 2.2 AA?
- Which browsers, devices, or assistive technologies must be supported?
- Are there hosting, analytics, personalization, search, CRM, or identity constraints?

## IA and Navigation Starter

Start from the candidate sitemap in `project/content-strategy.md`, then validate it against user tasks.

### Minimum IA Deliverable

```text
Primary navigation labels:
Secondary/utility navigation labels:
Footer navigation groups:
Homepage primary user path:
Top listing pages:
Top detail page types:
Search/filter needs:
Known redirects or legacy paths:
Open IA questions:
```

### IA Heuristics

- Use audience language, not internal department labels.
- Keep primary navigation short enough to scan on mobile.
- Avoid creating a content type only because a navigation section exists.
- Prefer clear landing pages for major sections over mega-menu complexity until content volume proves the need.
- Design search and filtering only when content volume and metadata justify them.
- Include Privacy, Terms if needed, and Accessibility statement in footer planning.

## Initial Component Inventory

This is a starter inventory for Drupal planning, not a final visual system. Keep components reusable, content-driven, and feasible with Drupal templates, blocks, fields, Views, and libraries.

| Component             | Purpose                                           | Likely Drupal source                         | States/variants to design                                      | Notes                                                         |
| --------------------- | ------------------------------------------------- | -------------------------------------------- | -------------------------------------------------------------- | ------------------------------------------------------------- |
| Site header           | Brand, primary navigation, utility actions        | Theme region, menu blocks                    | desktop, mobile menu closed/open, active trail, focus          | Avoid custom JS until menu behavior is confirmed.             |
| Footer                | Secondary navigation, legal links, contact/social | Theme region, menu blocks, custom block      | default, long link labels, missing optional items              | Keep footer editable where practical.                         |
| Page title block      | Orient users on each page                         | Drupal page title/block or template          | standard, long title, no summary                               | Preserve heading hierarchy.                                   |
| Hero / intro band     | Introduce landing pages and key paths             | Fields or block on landing pages             | with/without CTA, with/without media, long copy                | Do not require every page to have a hero.                     |
| Content card / teaser | Reusable preview in listings and related content  | View mode for nodes/media                    | image/no image, long title, topic/date metadata, focus         | Needs realistic title and summary lengths.                    |
| Listing page          | Browse news/resources/events/services             | Views + exposed filters if justified         | empty, loading if AJAX used, filtered, paginated, no results   | Prefer non-AJAX until need is proven.                         |
| Detail article body   | Read long-form content                            | Node templates, text formats, media embeds   | headings, lists, quotes, tables, embeds                        | Needs content style guidance and accessible media.            |
| CTA / promo           | Direct users to next action                       | Block, reusable entity, paragraph, or fields | primary/secondary, external/internal link, no supporting text  | Model after content strategy decision; avoid overengineering. |
| Form pattern          | Contact, signup, feedback, account flows          | Drupal forms/webform if added                | default, required, error, success, help text                   | Error handling and labels are design requirements.            |
| Alert/status message  | System feedback                                   | Drupal status messages                       | status, warning, error, info, dismissible if needed            | Must not rely on color alone.                                 |
| Breadcrumb            | Orientation on deeper pages                       | Drupal breadcrumb block                      | desktop, mobile, long labels                                   | Confirm if useful once sitemap depth is known.                |
| Pagination            | Move through long listings                        | Views/core pager                             | default, current, disabled, focus                              | Include accessible labels.                                    |
| Search result         | Help users compare results                        | Search/View result view mode                 | excerpt/no excerpt, highlighted terms if supported, no results | Search requirements are still open.                           |

## Component Spec Template

Use this template for each component before implementation.

```text
Component name:
User need:
Used on:
Content source / Drupal source:
Required fields:
Optional fields:
Variants:
States:
Responsive behavior:
Keyboard behavior:
Accessibility notes:
Editorial guidance:
Drupal implementation notes:
Dependencies:
Open questions:
```

## Design Token Starter

Use tokens to communicate intent to the themer. Do not invent a final brand palette until brand inputs exist.

### Token Categories

```text
Color:
- color-bg-page
- color-bg-surface
- color-text-primary
- color-text-secondary
- color-link
- color-link-hover
- color-border
- color-focus-ring
- color-status-info
- color-status-success
- color-status-warning
- color-status-error

Typography:
- font-family-base
- font-family-heading
- font-size-step--1
- font-size-step-0
- font-size-step-1
- font-size-step-2
- font-size-step-3
- line-height-tight
- line-height-base
- line-height-relaxed

Spacing:
- space-2xs
- space-xs
- space-sm
- space-md
- space-lg
- space-xl
- space-2xl

Layout:
- layout-max-width
- layout-content-width
- layout-gutter
- layout-section-gap

Shape and effects:
- radius-sm
- radius-md
- shadow-subtle, only if needed
```

### Token Rules

- Name tokens by purpose, not visual value.
- Keep token count small until real components require more.
- Include focus, error, warning, and success colors from the start.
- Confirm color contrast before handing values to the themer.
- Prefer CSS custom properties in the custom theme baseline.

## Responsive Checklist

Design and review at these minimum widths unless the project defines another matrix:

- narrow mobile around 320px
- common mobile around 390px
- tablet around 768px
- small desktop around 1024px
- wide desktop around 1440px

For each component, specify:

- what stacks, wraps, hides, or changes order
- whether media is cropped, resized, or removed
- how long titles and labels behave
- how navigation opens, closes, and traps/returns focus if needed
- whether tables, filters, cards, and forms remain usable on touch devices
- whether important actions remain visible without horizontal scrolling

## State Checklist

Every interactive or dynamic component needs the applicable states below.

- default
- hover, where hover exists
- focus-visible
- active/current
- disabled/unavailable
- loading/progress, only if the interaction can wait
- empty/no content
- error/validation failed
- success/completion
- offline or external-service unavailable, if integrations exist
- permission denied/not authenticated, if roles affect access

Drupal-specific states to remember:

- unpublished content indicators for editors
- contextual links/local tasks if visible to authenticated users
- status messages after forms
- Views empty text
- access denied and not found pages
- maintenance mode page

## Accessibility Review Checklist

Target WCAG 2.2 AA unless changed in `project/decisions.md`.

- Page has one clear `h1`; headings form a useful outline.
- Link and button text is descriptive out of context.
- Focus order matches visual/task order.
- Focus indicator is visible against adjacent colors.
- Color contrast meets AA for text and meaningful UI indicators.
- Meaning is not conveyed by color, icon, placement, or animation alone.
- Form fields have persistent labels, clear help text, and specific error text.
- Required/optional fields are explained consistently.
- Images have alt text guidance; decorative images can be marked decorative.
- Motion is reduced or disabled with `prefers-reduced-motion`.
- Components work with keyboard only.
- Mobile touch targets are comfortably sized and spaced.
- Error, empty, loading, and success states are understandable by screen reader users.

## UX Review Heuristics

Use these during design critique and implementation review.

1. Can a new user tell what the site is and what to do next within a few seconds?
2. Does the navigation reflect user goals rather than organization structure?
3. Are labels plain, specific, and consistent with the content strategy?
4. Does each page have one primary job?
5. Are cards, lists, and teasers comparable at a glance?
6. Are editors asked for only fields that have a user, SEO, governance, or display purpose?
7. Does the design survive missing images, long titles, empty listings, and short summaries?
8. Can Drupal implement this with configuration, fields, Views, blocks, Twig, and libraries before custom code?
9. Does the responsive behavior preserve priority instead of merely shrinking the desktop design?
10. Are accessibility requirements visible in the design handoff, not left for QA?

## Handoff Requirements

Before the themer implements a component, provide:

- component name and user need
- content source and field mapping
- required/optional content
- variants and states
- responsive behavior
- accessibility notes
- example content lengths
- dependencies on Writer, Module Developer, or Team Lead decisions

Before the Module Developer builds fields or content architecture, provide:

- whether the component reflects an editorial concept, display pattern, or both
- which fields are user-facing vs editorial/admin only
- whether reused content should be a node, block, paragraph, media item, taxonomy term, or simple field
- which relationships, listings, filters, or sort orders are required

## Open Questions

- What is the final brand/design-token source?
- What browser/device support matrix should design and theming target?
- Which content lengths should be used for early component stress tests?
- Will search, filtering, forms, events, or downloads be launch-critical?
- Does the project need component previews outside Drupal, or are Drupal-rendered examples enough?

## Verification Notes

- Reviewed against `project/site-brief.md`, `project/content-strategy.md`, `project/technical-standards.md`, `project/theme-tooling.md`, `project/decisions.md`, and `agents/designer-ux-lead.md`.
- Kept all guidance Drupal-implementable and avoided final visual design assumptions.
- No Drupal app code was added.
- Ran `pnpm format:check`, `composer validate --no-check-publish`, and `composer lint:php`; all passed after `composer install` restored missing PHP tooling.
