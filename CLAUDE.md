# CLAUDE.md

This file provides guidance to Claude Code (claude.ai/code) when working with code in this repository.

## What this project is

Static website for BitBox (www.bitbox.be), an IT-consultancy firm. Built with Jekyll using the Minima theme, deployed via GitHub Pages. The goal is to have a professional tech blog. The language on the site is in English

## Commands

```bash
# Install dependencies
bundle install

# Run local development server (http://localhost:4000)
bundle exec jekyll serve

# Build site to _site/
bundle exec jekyll build
```

## Architecture

- `_config.yml` — site-wide settings (title, author, theme, plugins, Google Analytics)
- `_posts/` — blog posts in Markdown, filename format: `YYYY-MM-DD-slug.markdown`
- `_includes/` — reusable HTML snippets (header, social icons)
- `images/` — static images referenced in posts and pages
- `_site/` — generated output, not committed to git

## Blog post conventions

Front matter required for posts:

```yaml
---
layout: post
title:  "Post Title"
date:   YYYY-MM-DD HH:MM:SS +0100
permalink: /custom-url/
---
```

Images go in `images/` and are referenced as `/images/filename.png` in posts.
