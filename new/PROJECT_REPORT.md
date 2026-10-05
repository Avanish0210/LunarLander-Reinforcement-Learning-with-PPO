# LunarLander: Reinforcement Learning with PPO

## Group Project Report

| Submission detail | Information |
|---|---|
| Institution | VIT Bhopal |
| Course | [Add course name] |
| Faculty | [Add faculty name] |
| Submission date | [Add date] |

### Submitted by

| Student name | Roll number |
|---|---|
| Avanish Pratap Singh | 23MIM10017 |
| Arpita Pateriya | 23MIM10168 |
| Aastha Pateriya | 23MIM10167 |
| Chaitanya Gupta | 23MIM10122 |
| Jai Palan | 23MIM10052 |

## Abstract

This project applies reinforcement learning to the LunarLander control task. A Proximal Policy Optimization (PPO) agent, implemented with Stable-Baselines3, learns to control a lunar module in Gymnasium's `LunarLander-v3` environment. The model is evaluated against a random-action baseline, and the project records training progress and a rendered landing demonstration. The reported trained-agent mean score is approximately 251, above the environment's 200-point solved threshold. The notebook, trained checkpoint, monitor logs, reward curve, and demonstration are included with the submission.

## 1. Introduction

LunarLander is a control problem in which an agent must guide a lunar module to a landing pad. The agent observes the state of the lander and chooses among discrete engine actions. Safe, controlled landings receive positive rewards, while crashes are penalized. Fuel use also incurs a small cost. Because actions affect later observations and rewards, the task is naturally modeled as a Markov decision process.

## 2. Problem statement

Train a policy that maps the environment's observations to engine actions so that the lander reaches the pad and lands safely. The project uses an average evaluation score of 200 as the target for considering the environment solved.

## 3. Objectives

1. Set up and inspect the Gymnasium `LunarLander-v3` environment.
2. Measure a random-action policy as a baseline.
3. Train a PPO policy using Stable-Baselines3.
4. Evaluate the trained policy and compare it with the baseline and solved threshold.
5. Record training progress and produce a visual episode demonstration.

## 4. Tools and environment

| Component | Choice |
|---|---|
| Programming language | Python |
| Environment | Gymnasium `LunarLander-v3` |
| Reinforcement-learning algorithm | Proximal Policy Optimization (PPO) |
| RL implementation | Stable-Baselines3 |
| Training setup | Eight parallel environments |
| Monitoring and evaluation | Stable-Baselines3 Monitor and evaluation utilities |
| Visualization and recording | Matplotlib and ImageIO |

## 5. Methodology

### 5.1 Baseline

The notebook first runs a random policy for five episodes. It records the return from each episode and uses their mean as a reference point for the learned policy.

### 5.2 PPO training

PPO is an on-policy actor-critic method. It updates a policy using collected trajectories while clipping policy changes to limit overly large updates. The notebook creates eight parallel instances of the environment and trains toward the 200-point target. It stores training monitor data under `logs/` and saves the model checkpoint as `ppo_lunarlander.zip`. When a checkpoint already exists, the workflow loads and evaluates it before deciding whether more training is needed.

### 5.3 Evaluation

The trained policy is evaluated deterministically over five episodes. The notebook reports the episode scores and their mean, then compares the mean with the 200-point target.

### 5.4 Training curve and demonstration

The notebook reads episode monitor logs and plots episode reward against cumulative timesteps, including a rolling mean and the target threshold. It also runs a rendered episode and saves the captured frames to `demo.gif`.

## 6. Results

The project README records the following approximate results:

| Measure | Reported value |
|---|---:|
| Random-agent mean score | -178 |
| Trained-agent mean score | 251 |
| Solved threshold | 200 |
| Training timesteps | Approximately 1.11 million |
| Parallel training environments | 8 |

The reported trained-agent mean is 51 points above the solved threshold. These values are approximate; episode returns can vary with training and evaluation conditions. The notebook's printed evaluation output and monitor logs should be treated as the run-specific source of truth.

## 7. Discussion

The recorded result indicates that the PPO policy learned a substantially more effective landing strategy than random actions and exceeded the benchmark threshold. The reward curve provides a view of learning progress, while the saved GIF offers a qualitative check of the learned behavior. Evaluation over five episodes provides a useful demonstration but is a relatively small sample; repeated evaluation over more episodes would give a more stable estimate of expected performance.

## 8. Conclusion

The project demonstrates an end-to-end reinforcement-learning workflow: environment setup, random-policy baseline, parallel PPO training, deterministic evaluation, reward visualization, and a rendered demonstration. The reported trained-agent mean score of approximately 251 exceeds the LunarLander solved threshold of 200. The notebook and saved artifacts make the experiment reproducible and inspectable.

## 9. Team contributions

The source materials identify the project team but do not specify each member's individual contribution. Complete this table with the group's actual division of work before submission; do not treat the names below as assigned roles.

| Student name | Roll number | Individual contribution |
|---|---|---|
| Avanish Pratap Singh | 23MIM10017 | [Add actual contribution] |
| Arpita Pateriya | 23MIM10168 | [Add actual contribution] |
| Aastha Pateriya | 23MIM10167 | [Add actual contribution] |
| Chaitanya Gupta | 23MIM10122 | [Add actual contribution] |
| Jai Palan | 23MIM10052 | [Add actual contribution] |

## 10. References

1. Schulman, J., Wolski, F., Dhariwal, P., Radford, A., and Klimov, O. “Proximal Policy Optimization Algorithms.” arXiv:1707.06347, 2017. https://arxiv.org/abs/1707.06347
2. Farama Foundation. “Lunar Lander.” Gymnasium documentation. https://gymnasium.farama.org/environments/box2d/lunar_lander/
3. Stable-Baselines3. “PPO.” Documentation. https://stable-baselines3.readthedocs.io/en/master/modules/ppo.html
4. Stable-Baselines3. “Evaluate Policy.” Documentation. https://stable-baselines3.readthedocs.io/en/master/common/evaluation.html

## Appendix: Reproduction

Install dependencies and run the notebook from the project folder:

```bash
pip install gymnasium Box2D pygame "stable-baselines3>=2.3" imageio matplotlib pandas notebook
jupyter notebook LunarLander_PPO_RL.ipynb
```

Run the notebook cells in order. Training, evaluation, plotted logs, checkpoint loading, and GIF generation are implemented in `LunarLander_PPO_RL.ipynb`.
