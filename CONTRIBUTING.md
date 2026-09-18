# Contributing

This file covers contributing to **the template**. A repository created from it
should replace this file with its own rules for its own content.

## Reporting a problem

Open an issue using one of the templates:

- **Documentation error** — something is wrong, unclear or out of date.
- **Proposal** — new documentation, or a change to the shared theme.

Before opening one:

1. Check you are in the right repository. A wrong procedure in a course's
   documentation belongs in that course's repository, not here.
2. Check no equivalent issue exists.
3. If it affects safety, say so — the error template asks explicitly.

For small fixes — a typo, broken formatting — a pull request is better than an
issue.

## Pull requests

```bash
python3 -m venv .venv
source .venv/bin/activate
pip install -r requirements.txt
mkdocs serve
```

Before you open the PR:

- `mkdocs build --strict` passes.
- You checked the change in **both** themes, using the header toggle.
- If you touched tables or navigation, you checked it below 768px.
- English is updated first; translations mirror it.
- Exact input — key combinations, paths, commands — is left untranslated.

The PR template repeats this as a checklist.

## Changing the theme

`docs/stylesheets/newuu.css` is shared by every documentation site in the
organisation. A change here changes all of them.

- **Say what is wrong before proposing CSS.** Which component, which reader,
  what did they get wrong?
- **Colours that carry text need a contrast ratio in the PR description**,
  measured against the background it sits on, in both schemes. AA is 4.5:1 for
  body text and 3:1 for large text and UI.
- **Severity may never depend on colour alone.** A new state needs a shape, an
  icon or a weight as well.
- **New admonition types will usually be declined.** Three sanctioned severities
  is a ladder people can read; twelve is not.

Anything touching `danger` styling needs a second reviewer. Those callouts exist
to stop somebody being hurt.

## Writing style

See [Writing style](docs/guide/writing.md) — imperative, exact about input,
numbers with units, safety before procedure.

## Commit messages

Present tense, one line, saying what changed and why if it is not obvious:

```
Pin the emergency row style to the first cell

attr_list cannot set attributes on a table row, so the class goes on the
first cell and :has() lifts it to the row.
```
