# Schedule and deliverables

The work is split into packages. Each package has a level (Junior or Senior), the week it belongs to and the deliverable that has to be handed in.

## Core plan

| Week | Package | Level | Deliverable |
|---|---|---|---|
| 1 | Joint-order mapping across URDF / MJCF / Isaac Lab / SDK, with a tested conversion script | Junior | Table + script everyone imports |
| 1 | Shared MuJoCo evaluation harness | Junior | Script + metric definitions |
| 1–2 | Jetson Orin NX bring-up: network, DDS, `LowState` read, ONNX inference benchmark, base container | Senior | Working onboard inference + latency numbers |
| 1 | Safety protocol and hardware checklist | Senior | Written procedure, signed off by you |
| 1 | RL baseline survey | Senior | Three candidates, a pick, and a working run of the pick |
| 2 | Video → motion: GVHMR vs WHAM (TRAM if the camera moves) | Junior | Jitter and foot-slide comparison |
| 2 | Retargeting: baseline vs PHC / ProtoMotions, including limit and clamping analysis | Senior | Comparison through the harness |
| 2–3 | Deploy the Go2 velocity policy to the real Go2 | Senior | First hardware milestone |
| 3 | Tracking: BeyondMimic, SONIC fine-tune, fast off-policy trainer | Senior ×3 | Training time, tracking error, robustness |
| 3 | Sim-to-sim validation of every policy through the harness | Junior | Comparison table |
| 4 | Gantry tests → supervised floor tests on the G1 | Group | Videos and logged runs |
| 4 | Final comparison report | Everyone | The full matrix |

## Additional assignments

| Week | Package | Level | Deliverable |
|---|---|---|---|
| 1 | Set up the MSI computer: install the right Ubuntu version and set up Isaac Lab | Junior | Ubuntu on the computer, everything running |
| 1 | Research flow matching methods and policies | Senior | Reproducible code, state-of-the-art models |
| 1 | Research motion retargeting methods | Junior | Description of the methods, with an example of how each one worked |
| 2 | Train an RL policy for the G1 (MLP) | Senior | Result in simulation that passes the requirements |
| 3 | Run the learned policy on the real G1; research the sim2real and sim2sim gap | Senior | Sim2real and sim2sim results; working on the real G1 for the best candidates |
