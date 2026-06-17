<h2 align="center">🐳 Docker Installation</h2>


## 1️⃣ Install Docker

Install:

- Docker
- Docker Compose

Verify installation:

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

This allows MuJoCo and pygame windows to open correctly from the container.

---

## 4️⃣ Build the Docker image

```bash
docker compose -f docker/docker-compose.yml build --no-cache
```

The first build can take several minutes.

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

## 6️⃣ Launch MuJoCo simulation

Inside the container:

```bash
python 1.Unitree_mujoco/simulate_python/unitree_mujoco.py
```

---

## 7️⃣ Open a second terminal inside the same container

On the host machine:

```bash
docker ps
```

Copy the container name, then:

```bash
docker exec -it CONTAINER_NAME bash
```

Example:

```bash
docker exec -it summer_school_workshop_rl-summer-school-rl-run-xxxx bash
```

---

## 8️⃣ Launch deploy.py

Inside the second Docker terminal:

```bash
python 2.Deploy_python/deploy.py
```

Or without the dashboard:

```bash
python 2.Deploy_python/deploy.py --debug
```


