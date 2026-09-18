---
hide:
  - navigation
---

<div class="nu-hero" markdown>
<div class="nu-hero__rule"></div>

# NewUU Documentation Template

<p class="nu-hero__lead" markdown>
The documentation template of the **School of Engineering, New Uzbekistan
University**. Clone it, replace the content, and the design is already done —
colours, typography, components and accessibility are decided and written down.
</p>

[Start here](guide/index.md){ .md-button .md-button--primary }
[See every component](guide/components.md){ .md-button }

</div>

## What you get

<div class="grid cards" markdown>

-   :material-palette-outline: **A decided visual system**

    ---

    NewUU navy and green, a navy-tinted neutral ramp, and a light and a dark
    scheme that were designed separately rather than one being a filter of the
    other. Every choice is recorded in [DESIGN-DECISIONS.md][dd].

-   :material-view-grid-outline: **A component vocabulary**

    ---

    Tables, a three-step admonition ladder, keyboard keys, step sequences, card
    grids, tabs, code blocks and status pills — each with copy-paste source on
    the [Components](guide/components.md) page.

-   :material-translate: **Three languages**

    ---

    English, Russian and Uzbek through `mkdocs-static-i18n`, with fallback to
    English for pages that are not translated yet.

-   :material-wheelchair-accessibility: **Accessible by construction**

    ---

    Every colour that carries text meets WCAG AA against its own background, and
    severity is never signalled by colour alone.

</div>

## Start a new documentation repository

<div class="steps" markdown>

1.  **Use this repository as a template.** On GitHub, press *Use this template*
    → *Create a new repository*, inside the `NewUU-engineering` organisation.

2.  **Change the five values** under `CHANGE THESE` at the top of `mkdocs.yml`:
    `site_name`, `site_description`, `site_url`, `repo_url`, `repo_name`.

3.  **Replace the content.** Delete `docs/guide/` and `docs/example/`, write your
    own pages, and rewrite `nav`.

4.  **Push to `main`.** The `Deploy docs` workflow publishes to GitHub Pages by
    itself. Enable Pages once, from the `gh-pages` branch.

</div>

!!! note "The template keeps the design decisions, not your content"

    `docs/guide/` and `docs/example/` exist to show what is available. Once your
    own documentation is written, delete them — the theme does not depend on
    them.

  [dd]: https://github.com/NewUU-engineering/newuu-docs-template/blob/main/DESIGN-DECISIONS.md
