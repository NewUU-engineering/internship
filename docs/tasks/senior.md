# Task 2 — Senior Track

Training a locomotion policy in Isaac Lab, then investigating what a change to the task makes.

If you cannot get Isaac Lab running after a reasonable attempt, email us and explain why it didnt work.

## Part A — Train a walking policy

Install Isaac Lab by following the official installation guide at [https://isaac-sim.github.io/IsaacLab/](https://isaac-sim.github.io/IsaacLab/)

Train the Unitree Go2 quadruped on the flat-terrain velocity tracking task that ships with Isaac Lab. Use the default settings. Training runs headless, without a visualizer, and should take a few minutes.

When training finishes, load your trained policy and watch it run in the Newton visualizer. Record the screen.

**Push to your repository:**

- A video of your policy running
- Your trained checkpoint file

## Part B — Widen the command range and investigate

During training, the policy is given velocity commands sampled from a range. By default the linear velocity range is roughly minus one to plus one metre per second. Find where this range is set in the configuration and widen it to minus two to plus two.

Before you run the training, write down what you expect to happen and why. Put this in your report. If the result contradicts your prediction, say so and explain what you had wrong. A wrong prediction that is honestly analysed scores higher than a correct one with no reasoning behind it.

Retrain with the wider range, then watch the new policy in the visualizer and record it.

Open TensorBoard and compare your two runs. Look at error_vel_xy, success_rate, and the base contact termination rate.

Then retrain the wide-range configuration again, this time with roughly three times as many training iterations, and compare a third time.

**Push to your repository:**

- A video and checkpoint for the wide-range policy
- A video and checkpoint for the wide-range policy trained longer
- A short report

**In the report, answer:**

1. Your prediction, written before you ran the experiment.
2. What actually happened, with the metrics to support it.
3. Did more training iterations fix it? If yes, what does that tell you about the cause? If no, what does that rule out?

## Submission

Create a public GitHub repository, push everything listed above to it, and send us the link to the repository.

## Notes

Training with the default number of parallel environments takes a few minutes. If you run out of memory, reduce it — but be aware that the number of environments and the number of iterations are coupled, because one iteration collects a batch of data across all environments at once. A run with eight times fewer environments sees eight times less data over the same number of iterations.
