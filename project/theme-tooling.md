# Theme Tooling Plan

## Recommendation

Do not add Gulp now.

Start with Drupal core Starterkit and plain Drupal libraries:

- Base theme source: Drupal core Starterkit-generated custom theme.
- Theme path: `web/themes/custom/site_theme` until the real project/site name is known.
- Asset loading: Drupal `.libraries.yml`, attached globally only for site-wide base assets and narrowly for component/page-specific assets.
- CSS: plain modern CSS first, organized by base/layout/component/utility files.
- JavaScript: small ES modules or plain Drupal behaviors only when interaction requires it.
- Formatting: existing Prettier setup for Markdown, YAML, JSON, PHP, and Twig.
- PHP standards: existing PHP_CodeSniffer + Drupal Coder baseline.

## Why Not Gulp

Gulp would add a task runner before we have evidence that we need one. For this project stage, it would mostly duplicate what pnpm scripts can already do with fewer moving parts.

Avoiding Gulp keeps the build easier to debug:

- no extra task-runner API
- no hidden stream/plugin failures
- no watch pipeline to maintain
- no second abstraction over CSS/JS commands

If we later need asset compilation, add direct pnpm scripts first. Example future needs:

- Sass compilation
- PostCSS/autoprefixing
- CSS minification outside Drupal aggregation
- bundling JS dependencies
- Storybook or component documentation

Even then, prefer explicit CLI scripts through pnpm before adding Gulp, Vite, Webpack, or another build layer.

## Starting Theme

Use Drupal core Starterkit, not Olivero as the custom theme base.

Olivero is useful as a reference implementation for accessible Drupal markup patterns, but it is a finished core theme, not a clean project starter. Subtheming or copying Olivero usually brings assumptions we will spend time undoing.

Starterkit gives us a boring custom theme scaffold that belongs to the project:

```bash
# After the Drupal app exists under web/:
php web/core/scripts/drupal generate-theme site_theme \
  --name "Site Theme" \
  --path themes/custom \
  --starterkit stable9
```

Run this through DDEV if Drupal/PHP dependencies are containerized:

```bash
ddev exec php web/core/scripts/drupal generate-theme site_theme \
  --name "Site Theme" \
  --path themes/custom \
  --starterkit stable9
```

If the final site name is known before scaffolding, replace `site_theme` and `Site Theme` with that name.

## Proposed Theme File Shape

```text
web/themes/custom/site_theme/
├── site_theme.info.yml
├── site_theme.libraries.yml
├── site_theme.theme
├── css/
│   ├── base/
│   ├── layout/
│   ├── components/
│   └── utilities/
├── js/
│   └── behaviors/
└── templates/
    ├── layout/
    ├── content/
    └── components/
```

Keep component names tied to editorial/design concepts, not implementation details from one page mockup.

## Initial Library Policy

Use a small global library for base styles only:

- typography defaults
- design tokens/custom properties
- base element styles
- global layout primitives
- focus styles

Attach component libraries only where needed. Do not put every component stylesheet into a global bundle by default.

## CSS Policy

Use modern CSS before introducing preprocessors:

- CSS custom properties for tokens
- cascade layers if useful
- logical properties for spacing/layout
- `@media (prefers-reduced-motion: reduce)` for motion safety
- container queries only when browser support requirements allow them

Add Sass only if the design system becomes large enough to justify it. Do not add Sass just for nesting; native CSS nesting support is broadly available in modern browsers, but browser support requirements still need confirmation.

## JavaScript Policy

Default to no JavaScript.

When needed:

- implement as Drupal behaviors
- avoid global selectors when a component root is available
- support once-style attachment to avoid duplicate behavior binding
- preserve keyboard operation
- document any dependency in `.libraries.yml`

## Tooling To Add Later, Only When Needed

Recommended order:

1. `stylelint` for CSS quality once real CSS exists.
2. `eslint` only when custom JS becomes non-trivial.
3. `postcss` only if the browser support matrix requires transforms.
4. visual/regression tooling only after components stabilize.
5. Storybook only if multiple people are actively building/reviewing components outside Drupal.

## Open Questions

- What is the final site/theme name?
- What browsers/devices must be supported?
- Is there an existing brand system or design token source?
- Will the team need component previews outside Drupal?
- Are we allowed to rely on Drupal aggregation/minification in the target hosting environment?
