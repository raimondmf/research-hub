# CLAUDE.md

This file provides guidance to Claude Code (claude.ai/code) when working with code in this repository.

## Project Overview

InfoSec Research Hub (www.isegur.com) — a Jekyll static site providing research documentation on AI-assisted development governance, agentic safety, cyber hygiene, tabletop exercises, and AI API security. Content is mapped against international standards (NIST AI RMF, ISO 42001, Google SAIF, CSA AI Controls, MITRE ATLAS, OWASP).

Forked from the [Feeling Responsive](https://github.com/Phlow/feeling-responsive) Jekyll theme (Foundation CSS framework).

## Build & Development Commands

```bash
# Install dependencies
bundle install

# Serve locally (development config — recommended)
bundle exec jekyll serve --config _config.yml,_config_dev.yml

# Build site without serving
bundle exec jekyll build
```

Ruby version: 3.0 (see `.ruby-version`)

## Deployment

- **Branch:** `gh-pages` is the main and deploy branch
- **Method:** GitHub Actions workflow (`.github/workflows/jekyll.yml`) builds Jekyll and deploys to Pages
- **Domain:** Custom domain `www.isegur.com` (CNAME file at repo root, DNS configured via Squarespace)
- **Source setting in GitHub:** Must be set to "GitHub Actions" (not "Deploy from a branch") under Settings > Pages

The Actions workflow is required because the site uses `jekyll-asciidoc`, which is not supported by the classic GitHub Pages builder.

## Architecture

- **Theme:** Feeling Responsive (Foundation CSS, Kramdown markdown, Rouge syntax highlighting)
- **Plugins:** jekyll-paginate, jekyll-gist, jekyll-asciidoc
- **Frontpage:** Uses a 4-widget layout (`medium-6 large-3` grid) defined in `pages/pages-root-folder/index.md`

### Key Directories

- `_config.yml` — Primary site configuration (URLs, plugins, defaults)
- `_config_dev.yml` — Development overrides (localhost URLs, expanded Sass, no analytics)
- `_data/` — Site data (navigation.yml, authors.yml, socialmedia.yml, language.yml)
- `_includes/` — HTML partials (header, footer, sidebar, widget templates)
- `_layouts/` — Page templates (default, page, page-fullwidth, frontpage, blog, video)
- `_sass/` — Sass partials: `_01` colors → `_02` typography → `_03` media queries → `_04` global → `_05` normalize → `_06`–`_11` components/layout
- `pages/` — Section landing pages (ai-governance, tabletop, cyber-hygiene, api-security, info, contact)
- `AIGovernanceFramework/` — Research content: governance framework (Agentics.md) and practical guide (README.md)

### Navigation

Defined in `_data/navigation.yml`. Current structure:
- Home | Frameworks (AI Governance, API Security) | Initiatives (Cyber Hygiene, Tabletop) | Blog | About | Contact

### Adding New Content

- **New section page:** Create `pages/<section-name>.md` with `layout: page-fullwidth`, add to `_data/navigation.yml`
- **New blog post:** Create `_posts/<category>/YYYY-MM-DD-title.md`
- **Frontpage widget:** Edit `pages/pages-root-folder/index.md` front matter (widget1–widget4)
