# Torch Lure


<a href="https://www.youtube.com/watch?v=wCzCOYCfY9g" target="_blank">
  <img src="http://img.youtube.com/vi/wCzCOYCfY9g/maxresdefault.jpg" alt="Chandelure" style="width: 100%;">
</a>


# Depndencies

```
pip install git+https://github.com/Farama-Foundation/Minari.git@19565bd8cd33f2e4a3a9a8e4db372044b01ea8d3
```


```sh
pip install torchlure
```

# Usage
```py
import torchlure as lure

# Optimizers
lure.SophiaG(lr=1e-3, weight_decay=0.2)

# Functions
lure.tanh_exp(x)
lure.TanhExp()

lure.quantile_loss(y_pred, y_target, quantile=0.5)
lure.QuantileLoss(quantile=0.5)

lure.RMSNrom(dim=256, eps=1e-6)

# Noise Scheduler
lure.LinearNoiseScheduler(beta=1e-4, beta_end=0.02, num_timesteps=1000)
lure.CosineNoiseScheduler(max_beta=0.999, s=0.008, num_timesteps=1000):
```

### Dataset



```py
from torchlure.datasets import MinariEpisodeDataset, MinariTrajectoryDataset

env = gym.make("Hopper-V4")
minari_dataset = MinariEpisodeDataset("2048.2407.2")
minari_dataset.create(env, n_episodes=100)
minari_dataset.info()

traj_dataset = MinariTrajectoryDataset(minari_dataset, traj_len=20)

ep = traj_dataset[2]
ep["observations"].shape, ep["actions"].shape, ep["rewards"].shape, ep[
    "terminations"
].shape, ep["truncate"].shape

ep = traj_dataset[[3, 8, 15]]
ep = traj_dataset[np.arange(16)]
ep = traj_dataset[torch.arange(16)]
ep = traj_dataset[-16:]

```

<!-- # %%
dataset = D4RLDataset(
    dataset_id= "hopper-medium-expert-v2.2405",
    d4rl_name= "hopper-medium-expert-v2",
    env_id= "Hopper-v4",
)

# if you are download it once
dataset = D4RLDataset(
    dataset_id= "hopper-medium-expert-v2.2405",
) -->
<!-- See all datasets [here](https://github.com/pytorch/rl/blob/3a7cf6af2a08089f11e0ed8cad3dd1cea0e253fb/torchrl/data/datasets/d4rl_infos.py) -->