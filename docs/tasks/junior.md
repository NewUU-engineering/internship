# Task 1 — Junior Track

## Part A — Human Motion to Robot

Use UltimateBots Studio to generate a motion for the Unitree G1 robot. You can either upload a short human motion video or describe the motion using a text prompt. Keep the motion under 30 seconds and export it as a LAFAN CSV file.

Then, using the Unitree G1 model from the Unitree RL Gym repository, write a Python script that loads the robot in MuJoCo, plays the generated motion, and renders the result as an MP4 video.

**Push to your repository:**

- The rendered robot motion (motion.mp4)
- The source video or text prompt used
- The LAFAN motion file (motion.csv)
- Your Python script and a short README explaining how to reproduce the result

**In the README, briefly answer:**

1. How did you determine what the columns in the CSV represent?

## Part B — Walking Policy

Clone the Unitree RL Gym repository and run the pretrained G1 walking policy using its MuJoCo deployment.

The default policy makes the robot walk forward. Modify the setup so that the robot instead walks in a circle.

**Push to your repository:**

- A video of the G1 walking in a circle
- A short note explaining what you changed and why it produces circular motion

**In the note, briefly answer:**

1. What inputs does the policy receive, and where do they come from?
2. What does the policy output, and how is that converted into joint torques?

## Submission

Create a public GitHub repository, push everything listed above to it, and submit the link to the repository through [this Google Form](https://docs.google.com/forms/d/e/1FAIpQLSd0eTLY8zXTCS4gyTA9HDae2g5ZOY3dNbb-wedcaOr1DcXXFg/viewform?usp=publish-editor).

## Links

- UltimateBots Studio: [https://studio.ultimatebots.com/home](https://studio.ultimatebots.com/home)
- Unitree RL Gym repository: [https://github.com/unitreerobotics/unitree_rl_gym](https://github.com/unitreerobotics/unitree_rl_gym)
