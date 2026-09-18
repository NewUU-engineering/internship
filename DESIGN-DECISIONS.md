# NewUU documentation theme — decisions

Everything here is implemented in `docs/stylesheets/newuu.css` and `mkdocs.yml`.
Kept short on purpose: when somebody asks in a year why danger is *that* red,
the answer should be in one file.

## 1. Which colour is primary

**Navy `#162347` is the chrome. Green `#147E5C` is the accent.**

Green is the signature colour of the identity, but on a documentation site the
chrome is the largest coloured surface on every page. Green at that size
competes with the content and, worse, reads as "safe" on pages whose whole job
is to say *not safe*. Navy carries the institution; green does the work where it
is informative — active navigation, hover, links, section rules, the mark.

Green never carries meaning inside content. That is what keeps the red free.

## 2. The two greens

`#147E5C` measures 5.0:1 on white and passes; it measures far too low on the
dark ground. The dark scheme therefore uses `#41B078` (6.7:1 on `#0A1122`). Any
component using green declares both — the two schemes are two designs, not one
design and a filter.

## 3. Danger red: `#B3261E` light, `#FF6B5E` dark

The palette ships no error colour, so one was introduced.

- Roughly 6:1 on white, and white text on it passes — usable as ink and as fill.
- Warm crimson rather than orange-red, which keeps it far enough from the brand
  green in hue that the two do not go muddy when both are on screen.
- Warning amber is `#8A5A00` — dark enough to carry text, unlike a mid amber.

**Severity never depends on colour alone.** Danger is a circle with a bang,
warning a triangle, note a plain rule; danger additionally gets a filled title
bar and a 4px edge. The ladder survives greyscale and every form of colour
blindness.

## 4. Neutrals

Every grey comes from the university's navy-tinted ramp (`#F8FAFD` … `#010B1B`),
not from Material's greys. The cheapest change in the package and the largest
part of why the docs read as NewUU rather than as a brand colour dropped onto a
default page.

## 5. Typeface: IBM Plex Sans + JetBrains Mono

Museo Sans cannot be self-hosted, so it is replaced rather than approximated.
IBM Plex Sans was chosen because this content is dense, procedural and often
read at arm's length: it is engineered for small sizes, has excellent Cyrillic,
and covers the Latin Extended characters Uzbek needs (`o'`, `g'`, `ʻ`).
JetBrains Mono is one of the few monospaces with real Cyrillic.

**Body weight is 500, not 400** — carried over from the brand, and a large part
of why newuu.uz reads deliberate rather than default.

Currently loaded from the Google Fonts CDN via `theme.font`. To self-host (one
fewer third party, and it works on networks where that CDN is slow) set
`font: false` and add `@font-face` rules — budget four faces: sans 500 and 700,
mono 400 and 500.

## 6. Tables

Ruled, not zebra: at 550+ rows and three columns of prose, alternating fills add
noise without adding structure. Uppercase 10.5px headers on a 2px rule,
vertical-align top, 11px cell padding.

Mark the emergency row with `{: .row-danger }` — tinted ground, 3px red inset
edge, bold first cell.

**Mobile:** horizontal scroll with the first column pinned (`position: sticky`).
Chosen over collapsing rows into cards because a 53-row table becomes
unnavigable as 53 stacked blocks. Trade-off accepted: the reader swipes.

## 7. Keyboard keys

`pymdownx.keys` plus the three `--md-typeset-kbd-*` variables. `++l2+b++`
renders as real keys with a 2px bottom border, so it reads as a button and not
as a filename. The emergency combination takes `.kbd-danger` and inherits the
danger colours.

## 8. Three languages

`mkdocs-static-i18n` with `en` (default), `ru`, `uz` and
`fallback_to_default: true`. Two design consequences:

- At three items the switcher is a **menu**, not a toggle — which is also what
  finally makes it findable.
- A language with incomplete coverage needs a visible state. Untranslated pages
  fall back to English; mark the language *Partial / Qismli* in the menu and say
  so on the page, rather than leaving the reader on a page they believe is
  theirs. Uzbek labels run longest of the three — the mobile drawer wraps
  rather than truncates.

Keep `navigation.instant` **off**: it breaks the switcher.

## 9. Theme switch

One icon, three states (auto → light → dark), using Material's `palette`
toggle. Not a labelled light/dark pair: the label costs header room in three
languages and says nothing the icon does not.

## 10. Still open

- No official brand book. Every value above was read out of what `newuu.uz`
  serves in production. Confirm with communications.
- **A single-line horizontal lockup does not exist.** The header uses the mark
  alone — which in this logo is the tri-tone vertical rule. Clear space and
  minimum size are undefined; the three-line wordmark is illegible at header
  size, which is why it is not used there.
- `#314988` (campus logo) and `#CEFF01` (four occurrences on the homepage) are
  unexplained. Not adopted.

## 11. Resolved while building the template

The design above was implemented as a working repository and checked in a
browser. Six things were found and fixed; §12 of `newuu.css` holds the CSS ones,
each with its own note.

1.  **`assets/newuu-mark.svg` and `assets/favicon.svg` now exist.** Rebuilt from
    the official logo's geometry rather than traced: the bar sits at x
    2.233–4.241 with segment breaks at y 30.700 and y 51.580, which is the
    38 % / 64 % split §4 already assumed. The mark carries a padded 24:80 canvas,
    because a 4:80 rule at header height renders about one pixel wide.

2.  **`--md-admonition-fg-color` was undefined, and dark mode failed because of
    it.** A custom scheme name inherits only Material's `:root` fallbacks, which
    are the *light* values — so every admonition body rendered near-black in dark
    mode. Danger body text measured **1.15:1**. Invisible, on the one component
    whose job is to stop somebody being hurt, and invisible *only* in dark mode,
    which is why nothing looked wrong in light. Now 11.8:1.

3.  **`++l2+b++` published literally.** `pymdownx.keys` renders only names it
    knows, and `l1`, `l2`, `r1`, `r2` and `start` are not in its default map —
    they came out as the raw text `++l2+b++`, again on safety callouts.
    `mkdocs.yml` now carries a controller `key_map`.

4.  **Keyboard keys do not work in an admonition *title*** at all — a title is
    taken as plain text. Combinations belong in the body. Documented on the
    Components page.

5.  **`.row-danger` could not be authored.** `attr_list` does not support
    attributes on a table row; it does support them on a table *cell*. The class
    goes on the first cell and `:has()` lifts it to the row.

6.  **`.md-typeset p { max-width: 68ch }` leaked onto structural paragraphs.**
    An admonition title is emitted as `<p class="admonition-title">`, so the
    filled danger bar stopped two-thirds of the way across the callout.

Two smaller ones: the header showed the mark twice (Material puts the drawer
toggle between the logo and the title, so the `+` combinator never matched), and
status pills need a real `<span>` — `attr_list` cannot attach to a bare
`[bracket]` because there is no element to attach to.

## 12. From the first review

1.  **The header mark read as a stray hairline, and the university's actual logo
    appeared nowhere.** The mark had been scaled down from the official lockup,
    where the bar is 2 units against 80 tall — at a 28px header that measured
    **1.4px wide**. `assets/newuu-mark.svg` is now *redrawn* rather than scaled,
    keeping the 38 % / 64 % segment breaks.

    The width ratio took two passes. The first redraw went to 6:26 (1:4.3),
    which was legible but read as a rounded *block* — the corner radius, carried
    over from the original as a true pill, became a visible capsule once the bar
    was three times wider. The original is a pill too, but at ~1px wide nobody
    ever sees it as one; it reads as a plain rule. The mark is therefore
    **1:10 with a radius well under a pill** (`viewBox 0 0 4 40`, `rx 1.2`),
    which is ~3px at header height: visible, still a rule, crisp at the ends.

    The lesson generalises — **copying a ratio from a logo drawn at one size does
    not preserve how it reads at another.** Match the apparent character.

    The full three-line lockup moved to the **footer**, via
    `overrides/partials/copyright.html`. That is the only place on the page tall
    enough for it to be legible, and it means the real NewUU logo now appears on
    every page. Both footer grounds are dark, so `logo-light.svg` — the file with
    the white wordmark — is correct in both schemes.

    This still leaves §10's open item standing: **no single-line horizontal
    lockup exists**, and one would be the better answer for the header.

2.  **The copy button sat on code blocks as a pale filled tile.** The glyph was
    not the problem — its container was. Material gives `.md-code__nav` a
    hardcoded `background: rgba(245,245,245,.3)`, which is invisible on a light
    code block and composites to grey on ours. No theme variable reaches it. The
    tile is now transparent at rest and takes a token-derived ground only while
    the block is hovered.

    Worth knowing: Material 9.7 renamed this control from `.md-clipboard` to
    `.md-code__button`. The CSS matches both.

3.  **Buttons all but vanished in the dark scheme.** Material builds both button
    variants out of `--md-primary-fg-color` — the *chrome* colour. That works in
    light (navy fill, white ink, 15.4:1) and collapses in dark, where the chrome
    is `#060C19`, darker than the `#0A1122` page:

        primary    fill #060C19 on #0A1122   1.1:1   a hole, not a button
        secondary  text #060C19 on #0A1122   1.1:1   invisible label

    Dark mode cannot reuse the chrome as a fill, because the chrome *is* the
    page. The accent green takes the primary action instead — consistent with
    green already meaning "interactive" in this theme (active nav, hover) and
    leaving the danger red untouched. Now 7.2:1 text on fill, 6.9:1 fill against
    the page; the outlined variant is 17.4:1 text with a 6.2:1 border.

    Same root cause as §11.2: a token that is correct in one scheme is not
    automatically correct in the other, and only the dark scheme shows it.

## 13. From the second review

1.  **The brand rule is decoration, not a button — and the gap was three times
    too wide.** Material always wraps `theme.logo` in an anchor to the home page
    and lays it out as a button: `padding: 0 8px` plus `margin: 4px`, with the
    title carrying another `margin-left: 20px`. Measured gap between the 3px rule
    and the first glyph: **32px**.

    Rasterising the official lockup gives the real relationship — the rule is
    4.0 viewBox units wide and the wordmark starts 15.4 units later, so the gap
    is **3.76x the rule's width**. At 3px that is ~11px.

    `theme.logo` is therefore dropped and the rule is drawn as a `::before` on
    the header title: never a link, and present wherever the title is, which
    includes every mobile breakpoint. Measured gap now 11px against the 11.3px
    the lockup implies. `assets/newuu-mark.svg` is kept for social cards and
    external use.

2.  **The mobile drawer no longer navigates itself.** Stock Material builds the
    primary nav below 76.1875em as absolutely-positioned panels that translate in
    and out, each with its own back-button header — tap a section, a sub-panel
    slides over, tap back to return.

    `navigation.sections` alone does **not** fix this: it flattens the *desktop*
    sidebar only. Verified in the DOM — five `.md-nav__title[for]` back buttons
    survived on a three-item nav. The panels are now un-positioned so every level
    renders in flow, the per-section back headers are removed, and section labels
    become headings rather than controls. One scrollable list, no hidden state.

    Two follow-ons the flattening exposed: Material's drawer title is normally
    5.6rem tall, which is what kept it clear of the fixed header — shrinking it
    put it underneath. The drawer now starts *below* the header instead
    (`top: 2.4rem`), so the header stays whole and the drawer reads as opening
    under it. And the active page kept a chevron that used to open its table of
    contents as a sub-panel; the contents are inline now, so the control is gone.

3.  **Mobile search wears the same field as desktop.** Desktop renders a tinted
    rounded field on the navy header; below the breakpoint the same markup became
    a full-bleed white strip with dark text.

    Specificity was the trap. Material sets the open state with
    `[data-md-toggle="search"]:checked ~ .md-header .md-search__form`, which
    outranks a plain `.md-search__form`. A first pass overrode at the lower
    specificity: the bar stayed white while the *input* override did land,
    giving white text on white — worse than stock. Every rule is now written at
    Material's own specificity.

    Search **behaviour** — the full-screen overlay, focus handling and result
    rendering — comes from Material's bundled JavaScript. It can be restyled but
    not restructured, and this is styling only.

    Note for anyone testing: toggling `#__search` programmatically renders
    results but leaves the list with Material's `hidden` attribute. Click the
    control and type, or you will diagnose a bug that is not there.

## 14. From the third review

1.  **The rule disappeared from the header in dark mode.** `--nu-mark-1/2/3`
    were declared only inside `[data-md-color-scheme="newuu"]`. Under the dark
    scheme they resolved to nothing, every colour stop in the gradient became
    invalid, and an invalid stop drops the whole `background` declaration — so
    the rule rendered as nothing at all. It had survived until now only because
    the mark used to be an `<img>` with the colours baked into the SVG; moving it
    to a CSS gradient in §13.1 exposed the gap.

    **Third occurrence of the same shape of bug** — see §11.2 (admonition text)
    and §12.3 (buttons): a value defined in one scheme and silently missing from
    the other, harmless in light and broken in dark.

    These three are not semantic tokens that should vary by scheme; they are the
    logo's own colours, and the official lockup keeps them identical on light and
    dark grounds. They now live in `:root`, where no scheme can lose them. **Any
    value that is a brand constant rather than a semantic role belongs there.**

2.  **The mobile search field was not centred** — flush against the left edge
    with the whole gap piled up on the right (measured 0px / 16px).

    The cause is counter-intuitive and worth writing down: **horizontal padding
    on `.md-search__form` does not inset the field.** Whatever padding the form
    is given, its own border box shifts left by exactly that amount, so the field
    stays flush and the gap accumulates on the opposite side. Confirmed by
    probing — at `.4rem` the form sat at −8, at `.5rem` at −10.

    The fix is to stop padding the form (at zero padding it sits true) and inset
    the field itself with `width: calc(100% - 1rem)` and `margin: 0 .5rem`, with
    the two icons moved out to match. Measured result: 10px / 10px, icons 15px
    inside each edge, all three vertically centred on the field.
