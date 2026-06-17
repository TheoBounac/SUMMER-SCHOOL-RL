<h2 align="center">🐳 Docker Installation</h2>

This project can be launched entirely inside Docker.

The Docker image automatically installs all dependencies required for both:

* **Training** (MJLab + MuJoCo Warp)
* **Deployment** (Unitree SDK2 + CycloneDDS + MuJoCo simulator)

No manual installation of MJLab, MuJoCo, CycloneDDS, or the Unitree SDK is required.

---

## 1️⃣ Install Docker

Install:

* Docker
* Docker Compose

Verify the installation:

```bash
docker --version
docker compose version
```

---

## 2️⃣ Clone the repository

```bash
git clone https://github.com/TheoBounac/SUMMER-SCHOOL-RL.git
cd SUMMER-SCHOOL-RL
```

---

## 3️⃣ Allow Docker to access the graphical display

```bash
xhost +local:docker
```

This allows MuJoCo, MJLab, and pygame windows to open correctly from the container.

---

## 4️⃣ Build the Docker image

```bash
docker compose -f docker/docker-compose.yml build
```

> **Note:** The first build can take several minutes because it installs MJLab, MuJoCo Warp, Unitree SDK2, CycloneDDS, and all Python dependencies.

---

## 5️⃣ Launch the container

```bash
docker compose -f docker/docker-compose.yml run --rm summer-school-rl
```

You should now be inside the Docker container:

```bash
root@xxxxx:/workspace/SUMMER-SCHOOL-RL#
```

---

# 🏋️ Training (MJLab)

Go to the MJLab workspace:

```bash
cd /opt/mjlab
```

Launch the Go2 environment with a random policy:

```bash
uv run play Mjlab-Velocity-Flat-Unitree-Go2 --agent random
```

Start training:

```bash
uv run train Mjlab-Velocity-Flat-Unitree-Go2 --env.scene.num-envs 1024
```

---

# 🤖 Deployment

## 6️⃣ Launch the MuJoCo simulator

Inside the container:

```bash
cd /workspace/SUMMER-SCHOOL-RL/2.Deploy

python Unitree_mujoco/simulate_python/unitree_mujoco.py
```

---

## 7️⃣ Open a second terminal inside the same container

On the host machine:

```bash
docker ps
```

Copy the container name, then run:

```bash
docker exec -it CONTAINER_NAME bash
```

Example:

```bash
docker exec -it summer-school-rl bash
```

---

## 8️⃣ Launch the deployment script

Inside the second Docker terminal:

```bash
cd /workspace/SUMMER-SCHOOL-RL/2.Deploy

python Deploy_python/deploy.py
```

Or without the dashboard:

```bash
python Deploy_python/deploy.py --debug
```
