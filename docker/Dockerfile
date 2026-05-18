FROM python:3.11-slim

ENV PYTHONDONTWRITEBYTECODE=1
ENV PYTHONUNBUFFERED=1

WORKDIR /workspace/SUMMER-SCHOOL-RL

RUN apt-get update && apt-get install -y --no-install-recommends \
    git \
    build-essential \
    cmake \
    libgl1 \
    libglib2.0-0 \
    libx11-6 \
    libxext6 \
    libxrender1 \
    libxrandr2 \
    libxcursor1 \
    libxi6 \
    libxinerama1 \
    libegl1 \
    libglfw3 \
    && rm -rf /var/lib/apt/lists/*

COPY docker/requirements.txt .

RUN pip install --upgrade pip \
    && pip install --no-cache-dir -r requirements.txt

COPY . .

ENV CYCLONEDDS_HOME=/workspace/SUMMER-SCHOOL-RL/cyclonedds/install
ENV PYTHONPATH="/workspace/SUMMER-SCHOOL-RL:/workspace/SUMMER-SCHOOL-RL/unitree_sdk2_python:${PYTHONPATH}"

RUN cd /workspace/SUMMER-SCHOOL-RL/unitree_sdk2_python \
    && pip install -e .

CMD ["bash"]
