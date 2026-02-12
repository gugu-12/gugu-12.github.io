# Quarto Academic Website Template

A minimal [Quarto](https://quarto.org/) template for personal academic websites.

## Files

| File | Purpose |
|------|---------|
| `_quarto.yml` | Site config — name, URLs, navbar |
| `index.qmd` | Home page (bio, photo, links) |
| `cv.qmd` | Your CV |
| `posts.qmd` | Blog listing (auto-generated) |
| `research.qmd` | Research listing (auto-generated) |
| `styles.css` | Minor style tweaks |
| `.github/workflows/publish.yml` | Auto-deploys to GitHub Pages on push |

## Adding Content

**New blog post:** Create a `.qmd` file in `posts/` with a YAML header:

```yaml
---
title: "My Post Title"
description: "A short summary."
date: "2025-02-12"
categories: [topic1, topic2]
---

Your content here.
```

**New research project:** Same thing, but in the `research/` folder.

Both listing pages (`posts.qmd` and `research.qmd`) pick up new files automatically — no config changes needed.
