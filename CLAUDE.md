# CLAUDE.md

This file provides guidance to Claude Code (claude.ai/code) when working with code in this repository.

## Project Overview

Static website for **FUSION MENA**, a B2B marketing and merchant acquisition company. The site is a **Webflow export** — all HTML, CSS, and JS are generated from Webflow's visual builder.

## Development

**Local server**: VS Code Live Server on port 5502 (configured in `.vscode/settings.json`)

There is no build step, package manager, or test suite. To preview changes, open any HTML file in a browser or use Live Server.

**Domain**: fusionmena.com (set via `CNAME` file)

## Architecture

This is a 4-page static site with no backend:

- `index.html` — Homepage with hero, services overview, talent sourcing showcase, merchant acquisition section, partner logos grid
- `contact.html` — Contact form powered by **FormSpree** (`https://formspree.io/f/xnnaropy`)
- `work.html` — Portfolio/case studies page
- `project.html` — Individual project detail template

### CSS

Three stylesheets loaded in order:
1. `css/normalize.css` — Browser reset
2. `css/webflow.css` — Webflow framework (grid system, responsive utilities, form handling)
3. `css/fusionmena.webflow.css` — All custom styles for this site

**Color variables**: `--dark-slate-gray`, `--tan`, `--white-smoke` and others defined in `:root`

**Responsive breakpoints**: 991px, 767px, 479px (Webflow standard)

### JavaScript

- `js/webflow.js` — Webflow runtime (interactions, animations, form handling). Do not edit directly.
- Inline `<script>` in `index.html` handles a custom scroll animation for the talent sourcing section
- jQuery 3.5.1 loaded from Webflow CDN

### External Dependencies (CDN)

- **Phosphor Icons** — Icon library loaded from unpkg
- **Google Fonts** — Vollkorn, Roboto Condensed, Roboto
- **jQuery 3.5.1** — From Webflow CDN

## Key Conventions

- Webflow uses `w-` prefixed classes for its framework (`w-row`, `w-col-6`, `w-hidden-small`, etc.). Custom classes have no prefix.
- Responsive visibility is controlled via `w-hidden-main`, `w-hidden-medium`, `w-hidden-small`, `w-hidden-tiny`.
- Images use responsive `srcset` with Webflow naming: `-p-500`, `-p-800`, `-p-1080` suffixes.
- The contact form submits to FormSpree — no backend needed. Success/error states are handled by Webflow's built-in form classes (`w-form-done`, `w-form-fail`).

## Git Commit Style

Recent commits use short lowercase descriptions: `spellingfix`, `mobilefix5`, `wording fixes`.
