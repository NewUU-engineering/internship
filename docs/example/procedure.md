# Example procedure

<span class="nu-pill nu-pill--stable">Stable</span>

Run through this page before every session.

--8<-- "safety-warning.md"

## How to stop the unit

There is no physical emergency stop on this configuration. Stopping is a remote
action, and the correct action depends on the situation.

| Situation | Action | Result |
| --- | --- | --- |
| Moving somewhere unintended, situation under control | 1× ++start++ | Returns to standing and holds |
| A sequence is running and must be cut short | 2× ++start++ | The running sequence is interrupted |
| **Emergency: unpredictable behaviour, risk to people** {: .row-danger } | ++l2+b++{: .kbd-danger } | Damping mode — the unit **slowly sinks to the ground** |
| Controller dead or unresponsive | Battery button | **Only after the unit is suspended**, feet clear of the ground, 2 m of clear space |

!!! warning "A double press is not an emergency stop"

    Double-press interrupts whatever is currently running. If nothing is running,
    the unit steps in place — and the operator believes they pressed stop.

!!! note "Fall protection is not a stop"

    Fall protection switches the motors to braking. It reduces damage; it does
    not replace correct stopping procedure.

## Pre-session procedure

<div class="steps" markdown>

1.  **Clear the workspace.** At least 2 m of clear floor around the unit. Dry,
    hard, level surface only.

2.  **Confirm the stop combination with every participant.** Each person present
    says the combination aloud: ++l2+b++{: .kbd-danger }

3.  **Check the battery.** Below 20 % the unit may sit down without warning.

    !!! warning "Do not begin a session below 20 %"

        Charge first. A shutdown mid-session drops the unit from standing height.

4.  **Record the session.** Date, operator, unit serial number.

</div>

## Confirming state from the SDK

=== "Python"

    ```python title="check_state.py"
    from example_sdk import UnitClient

    client = UnitClient("eth0")
    assert client.mode == "damping"   # (1)!
    ```

    1.  Raises if the unit is still standing. Never cut power to a standing unit.

=== "C++"

    ```cpp title="check_state.cpp"
    #include <example_sdk/unit_client.hpp>

    auto client = UnitClient("eth0");
    assert(client.mode() == Mode::Damping);
    ```

## Session checklist

- [ ] Workspace cleared to 2 m
- [ ] Stop combination confirmed aloud by every participant
- [ ] Battery above 20 %
- [ ] Session recorded in the log
