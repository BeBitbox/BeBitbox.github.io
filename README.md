# BeBitbox.github.io

Source for [www.bitbox.be](https://www.bitbox.be), the website of BitBox, an IT-consultancy firm. It's a Jekyll site using the Minima theme, deployed automatically via GitHub Pages.

## Getting started

Requires Ruby and [Bundler](https://bundler.io/).

```bash
# Install dependencies
bundle install

# Run local development server (http://localhost:4000)
bundle exec jekyll serve

# Build the site to _site/
bundle exec jekyll build
```

## Project structure

- `_config.yml` — site-wide settings (title, author, theme, plugins)
- `_posts/` — blog posts in Markdown, filename format: `YYYY-MM-DD-slug.markdown`
- `_includes/` — reusable HTML snippets (header, social icons)
- `images/` — static images referenced in posts and pages
- `_site/` — generated output (not committed to git)

## Writing a blog post

Add a new file to `_posts/` named `YYYY-MM-DD-slug.markdown` with front matter:

```yaml
---
layout: post
title:  "Post Title"
date:   YYYY-MM-DD HH:MM:SS +0100
permalink: /custom-url/
---
```

Images go in `images/` and are referenced as `/images/filename.png` in posts.

## Deployment

The site is built and published automatically by GitHub Pages whenever changes are pushed to the default branch.
