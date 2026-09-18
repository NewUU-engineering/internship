# Example reference

<span class="nu-pill nu-pill--draft">Draft</span>

A specification page: dense tables, definitions, and notes that belong at the
foot rather than in the flow.

## Operating limits

| Parameter | Value | Notes |
| --- | --- | --- |
| Operating temperature | 0 – 40 °C | Below 0 °C the battery will not charge |
| Continuous runtime | 90 min | At 20 °C with a full charge[^battery] |
| Maximum payload | 3 kg | Distributed; a point load derates this sharply |
| **Minimum clear space** {: .row-danger } | **2 m radius** | Non-negotiable during any session |
| Charge time | 2 h | 0 → 100 % with the supplied charger |
| Network | 1 Gb Ethernet | SDK requires a wired link |

## Terminology

Damping mode
:   Motors are energised but compliant. The unit sinks under its own weight
    rather than falling. This is the safe stop state.

Suspended
:   Held on the gantry with the feet clear of the ground. Required before any
    power cycle.

Idle
:   Powered, balanced, holding position, accepting commands.

## Controller reference

| Input | Function |
| --- | --- |
| ++start++ | Return to idle |
| 2× ++start++ | Interrupt running sequence |
| ++l2+b++{: .kbd-danger } | **Emergency: damping mode** |
| ++l1+a++ | Cycle operating mode |
| ++select++ | Toggle fall protection |

!!! note "Keep this table in sync with the controller"

    If the firmware remaps an input, this table is the page that will be wrong.
    Reference it from procedures rather than repeating the combinations.

The SDK exposes the same commands over Ethernet.

*[SDK]: Software Development Kit

[^battery]: Measured at 20 °C on a battery under 50 charge cycles. Expect
    roughly 15 % less in the first session after storage.
