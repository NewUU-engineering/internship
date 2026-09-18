# Using this template

This section is the reference for the template itself. **Delete it once your own
documentation is written** — the theme does not depend on it.

<div class="grid cards" markdown>

-   :material-view-grid-outline: **[Components](components.md)**

    ---

    Every element the theme styles, rendered, with copy-paste source.

-   :material-pencil-outline: **[Writing style](writing.md)**

    ---

    How to write procedures that hold up when somebody is reading them
    mid-task.

-   :material-translate: **[Translations](translations.md)**

    ---

    How the English, Russian and Uzbek versions of a page fit together.

</div>

## Running the site locally

<div class="steps" markdown>

1.  **Create a virtual environment and install the dependencies.**

    ```bash
    python3 -m venv .venv
    source .venv/bin/activate
    pip install -r requirements.txt
    ```

2.  **Serve with live reload.**

    ```bash
    mkdocs serve
    ```

    The site is then at `http://127.0.0.1:8000`. Saved edits reload the page.

3.  **Check the build is clean before pushing.**

    ```bash
    mkdocs build --strict
    ```

    `--strict` turns broken links and missing files into errors. CI runs it, so
    a clean local build means a green pipeline.

</div>

!!! note "Docker, if you prefer"

    ```bash
    docker run --rm -it -p 8000:8000 -v ${PWD}:/docs squidfunk/mkdocs-material
    ```

    Note that the i18n plugin is not in that image — install it in the container
    or use the virtual environment for translated sites.

## Repository layout

```text
├── docs/
│   ├── index.md              landing page
│   ├── assets/               logos, favicon, images
│   ├── stylesheets/
│   │   └── newuu.css         the theme — do not edit casually
│   ├── includes/             shared snippets pulled in with --8<--
│   ├── guide/                this section — delete it
│   └── example/              example pages — delete them
├── .github/
│   ├── ISSUE_TEMPLATE/
│   └── workflows/docs.yml    builds and publishes on push to main
├── mkdocs.yml                config; change the five values at the top
├── requirements.txt
└── DESIGN-DECISIONS.md       why the theme looks the way it does
```

## Changing the theme

Don't, casually. The value of a template is that the same decisions are not
remade in every repository — and `newuu.css` encodes decisions that were made
against measured contrast ratios, not taste.

If a genuine gap appears, open an issue against the template repository so that
the fix reaches every site, rather than patching one repository's stylesheet.
