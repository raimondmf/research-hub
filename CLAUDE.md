# CLAUDE.md

This file provides guidance to Claude Code (claude.ai/code) when working with code in this repository.

## Project Overview

This is the InfoSec Research Hub (isegur.com) — a Jekyll static site deployed via GitHub Pages on the `gh-pages` branch. It uses the "Feeling Responsive" theme (Foundation CSS framework). The site provides research documentation on AI-assisted development governance, agentic safety, cyber hygiene, tabletop exercises, and AI API security, mapped against international standards (NIST AI RMF, ISO 42001, Google SAIF, CSA AI Controls, MITRE ATLAS, OWASP).

## Build & Development Commands

```bash
# Install dependencies
bundle install

# Serve locally (production config)
bundle exec jekyll serve

# Serve locally (development config — recommended)
bundle exec jekyll serve --config _config.yml,_config_dev.yml

# Build site without serving
bundle exec jekyll build
```

Ruby version: 3.0.6 (see `.ruby-version`)

## Architecture

- **Branch model:** `gh-pages` is the main/deploy branch (GitHub Pages serves from this branch directly)
- **Theme:** Feeling Responsive (Foundation CSS framework, Kramdown markdown, Rouge syntax highlighting)
- **Plugins:** jekyll-paginate, jekyll-gist, jekyll-asciidoc

### Key Directories

- `_config.yml` — Primary site configuration (URLs, plugins, defaults, SEO)
- `_config_dev.yml` — Development overrides (localhost URLs, expanded Sass, no analytics)
- `_data/` — Site data files (navigation, authors, social media, translations)
- `_includes/` — HTML partials (header, footer, sidebar, navigation)
- `_layouts/` — Page layout templates (default, page, frontpage, blog, video)
- `_posts/design/` — Blog posts (theme demo/design examples)
- `_sass/` — Sass partials (Foundation components + custom styles `_01` through `_11`)
- `pages/` — Static pages (index, contact, search, documentation)
- `AIGovernanceFramework/` — Research content: AI governance framework documentation and control matrices

### Content Structure

- Pages use YAML front matter with layout, title, teaser, header options
- Posts go in `_posts/` with `YYYY-MM-DD-title.md` naming
- Navigation is configured in `_data/navigation.yml`
- Author profiles in `_data/authors.yml`

### Custom Sass Layer (in order of inclusion)

`_01` colors → `_02` typography → `_03` media queries → `_04` global settings → `_05` normalize → `_06`–`_11` components/layout/elements
