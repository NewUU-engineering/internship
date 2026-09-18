# NewUU documentation template

The documentation template of the **School of Engineering, New Uzbekistan
University**. Clone it and the design is already done — colours, typography,
components and accessibility are decided, implemented and written down.

Built on [Material for MkDocs](https://squidfunk.github.io/mkdocs-material/),
published to GitHub Pages, in English, Russian and Uzbek.

## Start a new documentation repository

1. Press **Use this template** → *Create a new repository*, inside the
   `NewUU-engineering` organisation.
2. Change the five values under `CHANGE THESE` at the top of `mkdocs.yml`:
   `site_name`, `site_description`, `site_url`, `repo_url`, `repo_name`.
3. Replace the contents of `docs/`, and rewrite `nav`.
4. Delete `docs/guide/` and `docs/example/` — they are the component reference,
   not your content.
5. Push to `main`. The workflow publishes the site; enable GitHub Pages once,
   serving from the `gh-pages` branch.

## Run it locally

```bash
python3 -m venv .venv
source .venv/bin/activate
pip install -r requirements.txt
mkdocs serve          # http://127.0.0.1:8000
```

Before pushing:

```bash
mkdocs build --strict   # broken links and missing files become errors
```

## What is in here

| Path | What it is |
|---|---|
| `docs/stylesheets/newuu.css` | The theme. Two colour schemes, the component styles, and the reasoning in comments |
| `docs/assets/` | Logos, the mark, the favicon |
| `docs/guide/` | How to use the template — **components reference lives here**. Delete after use |
| `docs/example/` | Example pages showing the components at work, with Russian and Uzbek versions. Delete after use |
| `docs/includes/` | Shared snippets pulled into pages with `--8<--` |
| `DESIGN-DECISIONS.md` | Why the theme looks the way it does |
| `.github/workflows/docs.yml` | Builds with `--strict`, publishes on push to `main` |

## The design, in brief

- **Navy `#162347` is the chrome, green `#147E5C` is the accent.** Green never
  carries meaning inside content — that is what keeps the danger red free.
- **Two schemes, designed separately.** The brand green changes value between
  them (`#147E5C` light, `#41B078` dark); `#147E5C` fails contrast on the dark
  ground, so it is not simply reused.
- **A danger red was introduced** (`#B3261E` light, `#FF6B5E` dark) because the
  NewUU palette ships no error colour, and these sites carry safety content.
- **Severity never depends on colour alone** — danger, warning and note each
  carry a distinct shape, so the ladder survives greyscale and colour blindness.
- **IBM Plex Sans + JetBrains Mono**, because Museo Sans is commercially
  licensed and cannot be self-hosted. Body weight is 500, carried over from the
  university's own typography.

Full reasoning in [DESIGN-DECISIONS.md](DESIGN-DECISIONS.md).

## Changing the theme

Please don't, casually. The point of a template is that the same decisions are
not remade in every repository, and `newuu.css` encodes choices made against
measured contrast ratios rather than taste.

If you hit a genuine gap, open an issue **against this repository** so the fix
reaches every site, instead of patching one repository's stylesheet.

## Contributing

See [CONTRIBUTING.md](CONTRIBUTING.md).

## Licence

Content is [CC BY 4.0](LICENSE). **The university logo and mark in
`docs/assets/` are not covered by that licence** and remain the property of New
Uzbekistan University.
