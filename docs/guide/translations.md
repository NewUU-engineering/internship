# Translations

The site builds in **English**, **Russian** and **Uzbek** through
`mkdocs-static-i18n`, using the suffix structure.

## How a page maps to its translations

```text
docs/example/procedure.md        English   (the source of truth)
docs/example/procedure.ru.md     Russian
docs/example/procedure.uz.md     Uzbek
```

A missing translation **falls back to English** rather than breaking the build
(`fallback_to_default: true`). That is deliberate: a partial translation should
never block publishing.

## The rules

<div class="steps" markdown>

1.  **English first.** Make substantive changes to the English page, then mirror
    them. A Russian page that has drifted ahead of its English source is a page
    nobody can review.

2.  **Translate the whole page or none of it.** A half-translated page is worse
    than an English one, because the reader cannot tell what they are missing.

3.  **Never translate exact input.** ++l2+b++ is ++l2+b++ in every language.
    Neither are file paths, command names or `code`.

4.  **Keep the file structure identical.** Same headings, same order, same
    tables. Translations are reviewed by comparing them side by side.

</div>

!!! warning "Uzbek needs Latin Extended, not plain ASCII"

    `oʻ` and `gʻ` use the modifier letter turned comma (U+02BB), not an
    apostrophe. IBM Plex Sans covers it; a font without Latin Extended will
    substitute and the page will look broken.

!!! note "Why `navigation.instant` is off"

    Material's instant loading breaks the language switcher: it sends the reader
    to the home page of the other language instead of the same page. Do not turn
    it on. The comment in `mkdocs.yml` says so too.

## Marking incomplete coverage

If a language is only partly translated, say so where the reader will see it —
at the top of the page, not only in the switcher:

```markdown
!!! note "Частичный перевод"

    Эта страница ещё не переведена полностью. Разделы без перевода
    отображаются на английском языке.
```
