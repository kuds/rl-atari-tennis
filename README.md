# Reinforcment Learning with Atari Tennis
The purpose of this repository is to explore how to play Atari Tennis using single and multi-agent reinforcement learning systems

![](/Images/ppo_atari_tennis.gif)

## Training Notes
- Set `ent_coef` for PPO as it encourages exploration of other actions. Stable Baselines3 defaults the value to 0.0. [More Information](https://www.youtube.com/watch?v=1ppslywmIPs)
- Do not set your `eval_freq` too low, as it can sometimes cause instability during learning due to being interrupted by evaluation. (e.g. >=10,000)
- Be careful when using Stable Baselines3's `VecTransposeImage` and `VecFrameStack` operators with grayed-scaled images. Atari Preprocessed Images are grayed scaled to (84, 84, 1) &rarr; Then stacked with 4 images (84, 84, 4) &rarr; Transpose to (4, 84, 84). In this context, `VecTransposeImage` is not needed when using Stable Baselines3's `make_atari_env`.
