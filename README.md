<p align="center">
  <img src="docs/assets/logo.svg" alt="Drupal Team Launchpad logo" width="180">
</p>

# Drupal Team Launchpad

<p align="center">
  <a href="#quick-start"><img alt="Quick start" src="https://img.shields.io/badge/quick_start-DDEV-blue"></a>
  <img alt="Drupal" src="https://img.shields.io/badge/Drupal-10%2F11-0678BE">
  <img alt="Node" src="https://img.shields.io/badge/Node-fnm-339933">
  <img alt="Package manager" src="https://img.shields.io/badge/package_manager-pnpm-F69220">
  <img alt="Formatting" src="https://img.shields.io/badge/formatting-Prettier-F7B93E">
</p>

A batteries-included starter workspace for Drupal teams that need to start new projects fast without skipping the work that keeps projects maintainable.

It gives your team a ready-to-use operating model, role briefs, Drupal standards, local dev defaults, formatting, Git hygiene, and an initial backlog so developers, themers, writers, designers, and AI coding agents can start from the same page.

## Why this exists

Most Drupal projects lose time before the first meaningful feature ships:

- local development conventions are undecided
- frontend tooling gets added inconsistently
- content strategy and design decisions are separated from Drupal architecture
- custom modules appear before the team proves they are needed
- agents or contributors start making assumptions in different directions

Drupal Team Launchpad makes the defaults explicit.

It is not a Drupal distribution. It is a project starter and team operating system for getting a real Drupal build moving cleanly.

## Batteries included

### Team scaffolding

Role briefs for a complete Drupal delivery team:

- Team Lead / Integrator
- Drupal Module Developer
- Drupal Themer
- Writer / Content Strategist
- Designer / UX Lead

Each role gets mission, responsibilities, standards, handoff needs, and verification expectations.

### Drupal project conventions

Default assumptions are already captured:

- Drupal 11 by default, with Drupal 10 fallback if constraints require it
- Composer-managed Drupal build
- `web/` docroot
- custom modules in `web/modules/custom/`
- custom themes in `web/themes/custom/`
- config export in `config/sync/`
- DDEV for local Drupal/PHP/database work
- fnm for Node version management
- pnpm for Node dependencies and scripts
- Prettier for formatting
- LF line endings via `.gitattributes`

### Planning docs

The `project/` directory includes:

- site brief
- technical standards
- team workflow
- backlog
- decisions log
- handoffs log
- agent launch prompts

These are intentionally plain Markdown so teams can use them in GitHub, issues, pull requests, Obsidian, or an AI coding workflow.

### Tooling baseline

Included repo config:

- `.ddev/config.yaml`
- `.fnmrc`
- `.node-version`
- `.nvmrc`
- `.npmrc`
- `.prettierrc.json`
- `.prettierignore`
- `.gitattributes`
- `.gitignore`
- `package.json`
- `pnpm-lock.yaml`

## Quick start

### 1. Clone or use as a template

```bash
git clone git@github.com:YOUR-ORG/drupal-team-launchpad.git my-drupal-site
cd my-drupal-site
```

Or create a new repository from this one as a GitHub template.

### 2. Use the expected Node version

```bash
fnm use
corepack enable
pnpm install --frozen-lockfile
```

The repo pins Node with `.fnmrc`, `.node-version`, and `.nvmrc` for compatibility with common workflows. `fnm` is the preferred version manager.

### 3. Start DDEV

```bash
ddev start
```

DDEV is configured for:

- Drupal 11
- docroot `web/`
- PHP 8.3
- MySQL 8.0
- nginx-fpm
- Composer 2
- Node 22 inside DDEV

### 4. Create the Drupal application

This repository starts as a team/project scaffold. When you are ready to create the Drupal app, use a Composer-managed Drupal project with `web/` as docroot.

A typical next step is:

```bash
ddev composer create-project drupal/recommended-project .
```

Before running that in an existing repo, review the generated files and decide how you want to merge Composer's scaffold with this starter. Do not blindly overwrite project docs or tooling config.

### 5. Fill in the project brief

Start here:

```text
project/site-brief.md
project/decisions.md
project/backlog.md
```

The first useful task is not code. It is making the site purpose, audience, launch constraints, and ownership explicit.

## Repository structure

```text
.
├── AGENTS.md                         # top-level team/agent operating guide
├── agents/                           # role briefs
│   ├── team-lead.md
│   ├── drupal-module-developer.md
│   ├── drupal-themer.md
│   ├── writer-content-strategist.md
│   └── designer-ux-lead.md
├── project/                          # planning and coordination docs
│   ├── site-brief.md
│   ├── technical-standards.md
│   ├── workflow.md
│   ├── backlog.md
│   ├── decisions.md
│   ├── handoffs.md
│   └── launching-agents.md
├── .ddev/                            # DDEV local dev config
├── docs/assets/                      # README/logo assets
├── package.json                      # pnpm + Prettier baseline
└── pnpm-lock.yaml
```

Expected Drupal app layout after Composer scaffold:

```text
composer.json
config/sync/
web/modules/custom/
web/themes/custom/
web/sites/default/
```

## Working with the team docs

Start every new project by filling out:

1. `project/site-brief.md`
2. `project/decisions.md`
3. `project/backlog.md`

Then assign work by role:

- Writer drafts sitemap, content model, metadata, page briefs, and real content samples.
- Designer defines IA, component inventory, design tokens, responsive behavior, and accessibility states.
- Module Developer proposes Drupal architecture, content types, config, custom module needs, and backend verification.
- Themer plans and implements Twig, libraries, CSS, frontend behavior, and accessibility details.
- Team Lead keeps assumptions, handoffs, and decisions visible.

## Using AI agents

This scaffold is designed to work well with Hermes, Claude Code, Codex, OpenCode, or any coding agent that can read files and edit a repo.

Use prompts like:

```text
You are the Drupal Themer for this repository. Read AGENTS.md, project/site-brief.md, project/workflow.md, project/technical-standards.md, project/decisions.md, project/backlog.md, and agents/drupal-themer.md. Take T005 from project/backlog.md. Keep changes small, document assumptions, and update project/handoffs.md if another role depends on your output.
```

More launch prompts are in:

```text
project/launching-agents.md
```

## Quality bar

A task is not done until the contributor or agent documents:

- what changed
- how it was verified
- what assumptions remain
- whether another role needs a handoff

Preferred checks once the Drupal app exists:

```bash
ddev composer validate
ddev composer audit
ddev exec vendor/bin/phpcs
ddev exec vendor/bin/phpunit
fnm use
pnpm install --frozen-lockfile
pnpm format:check
pnpm test
pnpm lint
```

Run PHP, Drupal, database, and web-container checks through DDEV. Run pnpm/fnm commands on the host unless your project later decides otherwise.

## What this is not

This is not:

- a Drupal distribution
- a theme framework
- a replacement for project discovery
- a pile of custom code
- an excuse to let agents invent requirements

It is a clean launchpad for Drupal teams that want speed without chaos.

## Recommended first issues

If you are turning this into a real site, create issues for:

1. Fill in site brief and launch constraints
2. Confirm Drupal version and hosting target
3. Scaffold Composer Drupal app
4. Define content model and sitemap
5. Define visual direction and component inventory
6. Scaffold custom theme
7. Decide accessibility testing approach
8. Decide deployment/config workflow

## License

Add your project license here before publishing.
