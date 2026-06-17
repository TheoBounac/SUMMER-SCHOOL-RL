# 🏋️ Training (MJLab)

Go to the MJLab workspace:

```bash
cd /opt/mjlab
```
You should see:
<p align="center">
  <img src="docker1.png" width="700">
</p>

Launch the Go2 environment with a random policy:

```bash
uv run play Mjlab-Velocity-Flat-Unitree-Go2 --agent random
```

Start training:

```bash
uv run train Mjlab-Velocity-Flat-Unitree-Go2 --env.scene.num-envs 1024
```

