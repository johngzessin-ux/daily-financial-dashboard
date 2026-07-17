# CLAUDE.md

This file provides guidance to Claude Code (claude.ai/code) when working with code in this repository.

## What this repository is

A single-page static financial news digest, published as `index.html`. There is no build system, package manager, framework, server, or test suite — the entire "app" is one self-contained HTML file with inline `<style>`. `README.md` is a one-line project label with no additional detail.

The page is a "morning research digest" for financial advisor conversations, generated fresh each trading day and committed directly to `index.html`. The commit history shows the intended lifecycle: an initial placeholder ("This dashboard hasn't run yet...") is replaced by a full digest on each scheduled run, then overwritten again on the next run (see the `Daily update: <date>` commits). There's no archival of past days within the repo structure — each update replaces the prior day's content in place.

## Working with `index.html`

The document is organized as a fixed sequence of `<section>` blocks, each covering one topic area, currently:

1. Private Investments
2. Equities
3. Fixed Income
4. Geopolitical Events

Each section follows the same internal structure — preserve it when adding or updating content:

```html
<section>
  <h2>N. Section Title</h2>
  <div class="item">
    <b>Headline / takeaway sentence.</b>
    Body copy giving context, numbers, and why it matters for an FA conversation.
    <div class="src">Source: <a href="URL">Publisher — "Article Title"</a> (Date)</div>
  </div>
  <!-- more .item blocks -->
</section>
```

- Every `.item` must cite a source via a `.src` div with a real, working link — do not fabricate sources or figures.
- A `.item` may optionally include a `.video-wrap` with a YouTube `<iframe>` embed and a `.video-label` caption crediting the source (see the Geopolitical Events section for the pattern).
- The `<title>` and the `<div class="sub">` in the header both encode the digest date (e.g. "July 13, 2026") — update both together when refreshing content for a new day.
- All styling is inline in the single `<style>` block in `<head>`; there are no external stylesheets or assets to manage.

## Conventions

- Keep everything in one file: no external CSS/JS files, no build step, no dependencies.
- Content should stay factual and sourced — this is read by financial advisors as prep material, not marketing copy.
- No commands to build, lint, or test: there is nothing to compile and no test suite exists. Verifying a change means opening `index.html` in a browser and checking it renders correctly.
