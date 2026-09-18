# Components

Every element the theme styles, rendered, with the source underneath. Copy from
here rather than inventing — that is the whole point of the template.

Toggle the theme with the icon in the header: **every component below is designed
in both schemes**, not filtered.

---

## Admonitions

Three severities, and each carries a distinct **shape** as well as a colour, so
the ladder survives greyscale and every form of colour blindness.

!!! danger "Emergency stop"

    The one component that must be impossible to skim past. Filled title bar,
    4px edge, circle-and-bang icon.

    The emergency combination is ++l2+b++{: .kbd-danger } — and it belongs in the
    body, not the title. See the note below.

    Use `danger` **only** where ignoring it can injure somebody or destroy
    equipment. If everything is a danger, nothing is.

!!! warning "This is a warning"

    For things that will cost time, money or data — but not safety. Triangle
    icon, amber, no filled bar.

!!! note "This is a note"

    Context, background, a useful aside. Plain green rule, no ground.
    `note` is the only content component allowed to use the brand green.

??? danger "Collapsed danger — click to open"

    Admonitions collapse with `???` instead of `!!!`. Add a trailing `+` —
    `???+` — to render it open but collapsible.

    Tables and code blocks nest inside without breaking the frame.

```markdown title="Source"
!!! danger "Emergency stop"

    Indent the body by four spaces.

!!! warning "This is a warning"

    Body text.

!!! note "This is a note"

    Body text.

??? danger "Collapsed danger — click to open"

    `???` collapses, `???+` renders open but collapsible.
```

!!! warning "Keyboard keys do not work in an admonition title"

    A title is taken as plain text, so `++l2+b++` written there is published
    literally as `++l2+b++` — which on a safety callout is exactly the wrong
    place to be wrong.

    Put the combination in the **body** of the callout. The same applies to
    `summary` on a collapsed block.

!!! warning "Do not add admonition types"

    The theme sanctions exactly three: `danger`, `warning`, `note`. Material
    ships twelve, and the other nine are deliberately unstyled. A ladder with
    three rungs is one people can actually read.

---

## Tables

The component that carries these sites. Ruled rather than zebra-striped:
at 50+ rows of prose, alternating fills add noise without adding structure.

| Situation | Action | Result |
| --- | --- | --- |
| Routine stop, situation under control | 1× ++enter++ | The unit returns to idle |
| A running sequence must be cut short | 2× ++enter++ | The sequence is interrupted |
| **Emergency: risk to people** {: .row-danger } | ++l2+b++{: .kbd-danger } | Damping mode — the unit **sinks to the ground** |
| Controller unresponsive | Battery button | **Only after the unit is suspended** with 2 m of clear space |

```markdown title="Source"
| Situation | Action | Result |
| --- | --- | --- |
| Routine stop, situation under control | 1× ++enter++ | The unit returns to idle |
| **Emergency: risk to people** {: .row-danger } | ++l2+b++{: .kbd-danger } | Damping mode |
```

!!! note "Why the class goes on the first cell"

    python-markdown's `attr_list` does **not** support attributes on a table
    *row* — `{: .row-danger }` written after a row is emitted as a literal extra
    cell. It does work on a *cell*, so the class goes on the row's first cell and
    CSS lifts it to the whole row with `:has()`.

**On mobile** the table scrolls horizontally with the first column pinned.
Narrow this window below 768px to see it. Collapsing rows into cards was
considered and rejected — a 50-row table becomes unnavigable as 50 stacked
blocks.

---

## Keyboard keys

Controller and keyboard input renders as real keys, not as inline code, so it
reads as a button rather than as a filename.

Press ++ctrl+alt+del++ to interrupt. A single ++enter++ returns to idle.
The emergency combination is ++l2+b++{: .kbd-danger }.

```markdown title="Source"
Press ++ctrl+alt+del++ to interrupt. A single ++enter++ returns to idle.
The emergency combination is ++l2+b++{: .kbd-danger }.
```

`.kbd-danger` inherits the danger colours — use it **only** for the emergency
combination, so that the combination looks the same everywhere it appears.

---

## Step sequences

For procedures. Numbered markers, a connecting rule, and room for a warning or a
key combination inside any step.

<div class="steps" markdown>

1.  **Clear the workspace.** At least 2 m of clear floor. Dry, hard, level
    surface only.

2.  **Confirm the stop combination with everyone present.** Each person says the
    combination aloud: ++l2+b++{: .kbd-danger }

3.  **Check the battery.** Below 20 % the unit may shut down without warning.

    !!! warning "Do not start a session below 20 %"

        Callouts nest inside a step and keep the connecting rule.

4.  **Log the session.** Date, operator, and the serial number of the unit.

</div>

````markdown title="Source"
<div class="steps" markdown>

1.  **Clear the workspace.** At least 2 m of clear floor.

2.  **Confirm the stop combination.** ++l2+b++{: .kbd-danger }

    !!! warning "Callouts nest inside a step"

        Indent by four spaces, as usual.

</div>
````

The blank line after `<div ... markdown>` and before `</div>` is required —
without it, `md_in_html` does not process the contents.

---

## Card grids

For landing pages and section indexes. Not for use inside a procedure.

<div class="grid cards" markdown>

-   :material-book-open-variant: **A card with an icon**

    ---

    The `---` produces the rule under the title. Icons come from the Material
    icon set via `pymdownx.emoji`.

-   :material-shield-check: **A card that links**

    ---

    Ending a card with a link makes the whole card feel clickable.

    [Components reference](components.md)

</div>

```markdown title="Source"
<div class="grid cards" markdown>

-   :material-book-open-variant: **A card with an icon**

    ---

    Body text.

-   :material-shield-check: **A card that links**

    ---

    [Components reference](components.md)

</div>
```

---

## Code

=== "Python"

    ```python title="example.py" linenums="1"
    from pathlib import Path

    def load_config(path: Path) -> dict:
        """Read the unit configuration."""
        if not path.exists():                      # (1)!
            raise FileNotFoundError(path)
        return parse(path.read_text())
    ```

    1.  Numbered annotations need `content.code.annotate`. The marker is `(1)!`
        in a comment, and the note is a numbered list item under the block.

=== "C++"

    ```cpp title="example.cpp"
    #include <filesystem>

    Config load_config(const std::filesystem::path& path) {
        if (!std::filesystem::exists(path)) {
            throw std::runtime_error("missing config");
        }
        return parse(read_file(path));
    }
    ```

=== "Shell"

    ```bash title="Install and serve locally"
    python3 -m venv .venv
    source .venv/bin/activate
    pip install -r requirements.txt
    mkdocs serve
    ```

Tabs sharing the same labels stay in sync across the whole site
(`content.tabs.link`), so choosing *Python* once selects it everywhere.

````markdown title="Source"
=== "Python"

    ```python title="example.py" linenums="1"
    def load_config(path):
        if not path.exists():                      # (1)!
            raise FileNotFoundError(path)
    ```

    1.  The annotation text.

=== "C++"

    ```cpp title="example.cpp"
    auto config = load_config(path);
    ```
````

Inline code looks like `mkdocs serve`, and a file path like
`docs/stylesheets/newuu.css`.

---

## Text elements

### Headings

`h1` opens the page and there is exactly one. `h2` takes a rule, `h3` and `h4`
do not. Below `h4` the hierarchy has failed — split the page instead.

### Emphasis, links, quotes

Body text is **IBM Plex Sans at weight 500**, carried over from the university's
own typography. **Bold** for the operative word in a procedure, *italic* for
quoted source material, and [links](writing.md) in blue rather than green.

> A blockquote takes the green rule — the same vertical device as the mark.
> Use it for quoted source material, such as a manufacturer's manual.

### Lists

- An unordered list
- With a second item
    - And a nested item
    - And another

1. An ordered list
2. With a second item

- [x] A completed task
- [ ] An outstanding task

Term
:   A definition list. Useful for glossaries and parameter references.

Another term
:   With its own definition.

### Status pills

Mark a page's state: <span class="nu-pill nu-pill--draft">Draft</span>
<span class="nu-pill nu-pill--review">Needs review</span>
<span class="nu-pill nu-pill--stable">Stable</span>

```markdown title="Source"
<span class="nu-pill nu-pill--draft">Draft</span>
<span class="nu-pill nu-pill--review">Needs review</span>
<span class="nu-pill nu-pill--stable">Stable</span>
```

### Abbreviations and footnotes

Hover over SDK to see the tooltip. Footnotes[^1] collect at the foot of the page.

*[SDK]: Software Development Kit

[^1]: Defined anywhere in the file with `[^1]: text`.

```markdown title="Source"
Hover over SDK to see the tooltip. Footnotes[^1] collect at the foot.

*[SDK]: Software Development Kit
[^1]: The footnote text.
```

---

## Shared snippets

Text repeated across pages should live in `docs/includes/` and be pulled in, so
that correcting it once corrects it everywhere. The block below is included, not
typed:

--8<-- "safety-warning.md"

```markdown title="Source"
--8<-- "safety-warning.md"
```

Safety warnings duplicated by hand drift apart. This is the fix.

---

## What is deliberately absent

| Not included | Why |
|---|---|
| The other nine admonition types | Three rungs is a ladder people can read |
| Zebra-striped tables | Noise at 50+ rows of prose |
| Gradients in content | Reserved for the landing hero |
| Green as a meaning-carrying colour in content | It is what keeps the danger red free |
| Custom fonts beyond the two | Every extra weight is a download on a slow connection |
