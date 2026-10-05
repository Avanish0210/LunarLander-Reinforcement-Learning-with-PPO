# LunarLander: Reinforcement Learning with PPO

## Group project submission

**Institution:** VIT Bhopal  
**Course:** Reinforcement learning 
**Faculty:** Vandana Shakya
**Submission date:** 05-10-2026

### Submitted by

| Student name | Roll number |
|---|---|
| Avanish Pratap Singh | 23MIM10017 |
| Arpita Pateriya | 23MIM10168 |
| Aastha Pateriya | 23MIM10167 |
| Chaitanya Gupta | 23MIM10122 |
| Jai Palan | 23MIM10052 |

## Submission documents

- [Project report](PROJECT_REPORT.md) — abstract, objectives, methodology, results, conclusion, references, and team contributions.
- [Training and evaluation notebook](LunarLander_PPO_RL.ipynb) — executable experiment and result visualizations.

## Project files

| File or folder | Description |
|---|---|
| `PROJECT_REPORT.md` | Structured group project report |
| `LunarLander_PPO_RL.ipynb` | Training, evaluation, reward-curve generation, and demonstration workflow |
| `ppo_lunarlander.zip` | Trained PPO model checkpoint; load with `PPO.load` |
| `demo.gif` | Recorded trained-agent landing demonstration |
| `training_curve.png` | Episode reward over training timesteps |
| `logs/` | Training monitor logs |

## Reported results

The project records an approximate random-agent mean score of **-178** and a trained-agent mean score of **251**, above the environment's **200-point solved threshold**. The notebook evaluates policies over five episodes; scores may vary with the training run and evaluation episodes.

## Run the notebook

Install the notebook dependencies:

```bash
pip install gymnasium Box2D pygame "stable-baselines3>=2.3" imageio matplotlib pandas notebook
```

Start Jupyter and run the notebook cells:

```bash
jupyter notebook LunarLander_PPO_RL.ipynb
```

The notebook uses eight parallel environments for training and saves a checkpoint as `ppo_lunarlander.zip`. The training workflow checks an existing checkpoint before continuing training.

## Before final submission

Fill in the course, faculty, and submission-date fields. Complete the individual contribution entries in `PROJECT_REPORT.md` to match the group's actual work.
