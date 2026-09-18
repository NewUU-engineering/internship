# Writing style

These sites are read by somebody standing next to equipment, looking for one
specific step. Write for that reader.

## Procedures

<div class="steps" markdown>

1.  **Number every step, and put the action first.** "Press ++enter++ to return
    to idle", not "To return to idle, press ++enter++". The reader is scanning
    for the verb.

2.  **Be exact about input.** ++l2+b++, not "the stop combination". Exact
    combinations belong in keyboard keys, never in prose.

3.  **Say what should happen.** A step without an observable result cannot be
    verified, and the reader cannot tell whether it worked.

4.  **One action per step.** If a step contains "and", it is usually two steps.

</div>

## Severity

| Use | When | Example |
|---|---|---|
| `danger` | Ignoring it can injure somebody or destroy equipment | **Emergency stop combination** {: .row-danger } |
| `warning` | Ignoring it costs time, money or data | "Double-press is not an emergency stop" |
| `note` | Context that helps but is not required | "Fall protection reduces damage; it does not replace procedure" |

!!! warning "Severity inflation is the failure mode"

    Every callout marked `danger` makes the next one less visible. On a page with
    forty callouts, the reader stops seeing all of them.

## Tone

- **Imperative and unambiguous.** "Clear 2 m around the unit." Not "the
  workspace should ideally be clear."
- **No hedging in safety text.** "Below 20 % the unit may shut down without
  warning" is a fact. "It is recommended to check the battery" is not.
- **Numbers with units, always.** 2 m, 20 %, 24 V.
- **Name things the way the equipment names them.** If the controller says
  `START`, write ++start++ — not "the start button".

## Structure

- One `h1`, at the top. `nav` supplies the page title elsewhere.
- If you reach `h5`, the page is doing two jobs — split it.
- Put the safety content **before** the procedure, not after it.
- A page that is mostly a table should be a table. Do not narrate a table.

## Language

English is the source of truth. Make substantive changes in English first, then
mirror them — see [Translations](translations.md).
