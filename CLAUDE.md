# CLAUDE.md

This file provides guidance to Claude Code (claude.ai/code) when working with code in this repository.

## What this repo is

A **GitHub profile README** for the user **Bij4n** — the special repository whose
name matches the GitHub username, so it must be named `Bij4n/Bij4n`. GitHub renders
this repo's `README.md` at the top of `https://github.com/Bij4n`. There is no
application, build step, or test suite: the deliverables are `README.md` and the
banner asset, and "deploying" means pushing to the default branch. The change is
live the moment GitHub renders it.

The visual theme is **quiet and professional** — subtle, no costume. The banner is a
self-contained, theme-aware SVG wordmark (`banner.svg`): the name set in a neutral
system sans, a thin rule, and muted captions, with a `prefers-color-scheme` media
query so text adapts to light/dark. No animation, no third-party services. Body copy
is plain GitHub-flavored prose; the tech stack is a plain-text list (no badge grid);
the only badges are the small social chips in **Connect**, locked to one neutral slate
(`2d333b`, white logo, `flat-square`). Keep the palette restrained — neutral greys, no
bright accent colors. (The earlier Matrix digital-rain theme has been retired;
its `matrix.svg` and generator script are gone.)

## Rendering constraints (the important part)

GitHub renders the README with **GitHub Flavored Markdown (GFM)** through a strict
sanitizer. This governs almost every editing decision:

- **No `<script>`, no CSS `<style>`, no `style=` attributes, no `class`/`id`.** They
  are silently stripped. You cannot style with CSS — visual variety comes from
  images, badges, emoji, and the small set of allowed HTML tags.
- **Allowed HTML is a whitelist**: `<p>`, `<div>`, `<h1>`–`<h6>`, `<img>`, `<a>`,
  `<table>`, `<details>`/`<summary>`, `<sub>`/`<sup>`, `<br>`, `<picture>`, etc.
  `align="center"` on a block element is the main layout lever that survives.
- **Centering / layout** is done with `<p align="center">` or `<div align="center">`
  wrapping content — not CSS.
- **Light/dark theming** uses `<picture>` with `media="(prefers-color-scheme: dark)"`
  or the `#gh-dark-mode-only` / `#gh-light-mode-only` image-URL fragment trick, since
  there is no CSS.
- **Mermaid diagrams** render inside ```` ```mermaid ```` fenced blocks.

When unsure whether a tag survives, prefer markdown over HTML; reach for HTML only for
centering, images, tables, and collapsible `<details>` sections.

## Common building blocks

These are conventions for profile READMEs, not files in this repo — reach for them
when adding sections:

- **Badges**: `shields.io` (`https://img.shields.io/badge/...`) for tech/skill chips
  and `for-the-badge`/`flat` styles. Keep `logo=` slugs valid (simple-icons names).
- **Stats widgets**: third-party services rendered as images, e.g.
  `github-readme-stats.vercel.app`, `streak-stats`, `github-readme-activity-graph`.
  These phone home to a third party on every profile view — only add ones you trust,
  and remember the `?username=` must be updated to the real username.
- **Dynamic content** (latest blog posts, recent activity) requires a GitHub Actions
  workflow in `.github/workflows/` that rewrites `README.md` on a schedule and commits
  the result. There is no such workflow yet; add one only if dynamic sections are
  requested.

## Before considering a change done

There is no linter or test. Verify by:

1. Confirming every `YOUR_USERNAME` / placeholder is replaced.
2. Checking that any HTML used is on the GFM whitelist (it won't error — it just
   vanishes silently if not).
3. Previewing the rendered markdown (GitHub's preview tab, or a GFM-accurate
   previewer) rather than trusting raw source, since the sanitizer changes output.
