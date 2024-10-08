# Reinforcment Learning with Atari Tennis
The purpose of this repository is to explore how to play Atari Tennis using single and multi-agent reinforcement learning systems

![](/Images/dqn_atari_tennis.gif)

## Training Notes
- Set `ent_coef` for PPO as it encourages exploration of other actions. Stable Baselines3 defaults the value to 0.0. [More Information](https://www.youtube.com/watch?v=1ppslywmIPs)
- Do not set your `eval_freq` too low, as it can sometimes cause instability during learning due to being interrupted by evaluation. (e.g. >=10,000)
- Be careful when using Stable Baselines3's `VecTransposeImage` and `VecFrameStack` operators with grayed-scaled images. Atari Preprocessed Images are grayed scaled to (84, 84, 1) &rarr; Then stacked with 4 images (84, 84, 4) &rarr; Transpose to (4, 84, 84). Stable Baselines3 will automatically apply `VecTransposeImage` if it detects that the input type is images. But will not do so for the elevation environment automatically
- Due to extremely long run times, it is best to save checkpoints and model files to external sources like Google Drive
- One of the challenges with Atari Tennis is Sparse Rewards because it usually takes multiple hits before a point is rewarded. Need to encourage lots of exploration
- Sometimes, the policy will learn a policy not to serve the ball as it leads to a better policy than continually losing points. Something to monitor
