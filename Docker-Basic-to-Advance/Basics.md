# 🐳 Docker: Basics to Advanced (GitHub Notes)

This guide covers **Docker from basic to advanced**, with commonly used commands, best practices, and examples. Ideal for beginners and quick revision.

---

## 📦 IMAGES

### List all local images

```bash
docker images
```

### Delete an image

```bash
docker rmi <image_name_or_id>
```

### Remove unused images (dangling)

```bash
docker image prune
```

### Remove all unused images

```bash
docker image prune -a
```

### Build an image from Dockerfile

```bash
docker build -t <image_name>:<version> .
```

### Build image without cache

```bash
docker build --no-cache -t <image_name>:<version> .
```

---

## 🚢 CONTAINERS

### List all containers (running + stopped)

```bash
docker ps -a
```

### List running containers

```bash
docker ps
```

### Create & run a new container

```bash
docker run <image_name>
```

> If image is not available locally, Docker will pull it from Docker Hub.

### Run container in background (detached mode)

```bash
docker run -d <image_name>
```

### Run container with custom name

```bash
docker run --name <container_name> <image_name>
```

### Port binding (host → container)

```bash
docker run -p <host_port>:<container_port> <image_name>
```

### Set environment variables

```bash
docker run -e VAR_NAME=VAR_VALUE <image_name>
```

### Start or stop an existing container

```bash
docker start <container_name_or_id>
docker stop <container_name_or_id>
```

### Restart a container

```bash
docker restart <container_name_or_id>
```

### Inspect a container

```bash
docker inspect <container_name_or_id>
```

### Delete a container

```bash
docker rm <container_name_or_id>
```

### Force delete a running container

```bash
docker rm -f <container_name_or_id>
```

---

## 🛠️ TROUBLESHOOTING

### Fetch container logs

```bash
docker logs <container_name_or_id>
```

### Follow logs in real-time

```bash
docker logs -f <container_name_or_id>
```

### Open shell inside a running container

```bash
docker exec -it <container_name> /bin/bash
```

> Use `/bin/sh` for lightweight images like Alpine

```bash
docker exec -it <container_name> sh
```

---

## ☁️ DOCKER HUB

### Login to Docker Hub

```bash
docker login
```

### Logout from Docker Hub

```bash
docker logout
```

### Pull an image

```bash
docker pull <image_name>
```

### Push an image to Docker Hub

```bash
docker push <username>/<image_name>:<tag>
```

### Search for images

```bash
docker search <image_name>
```

---

## 💾 VOLUMES

### List all volumes

```bash
docker volume ls
```

### Create a named volume

```bash
docker volume create <volume_name>
```

### Delete a volume

```bash
docker volume rm <volume_name>
```

### Mount named volume to container

```bash
docker run --volume <volume_name>:<mount_path> <image_name>
```

### Mount using --mount (recommended)

```bash
docker run --mount type=volume,src=<volume_name>,dest=<mount_path> <image_name>
```

### Anonymous volume

```bash
docker run -v <mount_path> <image_name>
```

### Bind mount (host ↔ container)

```bash
docker run -v <host_path>:<container_path> <image_name>
```

### Remove unused volumes

```bash
docker volume prune
```

---

## 🌐 NETWORKING

### List networks

```bash
docker network ls
```

### Create a network

```bash
docker network create <network_name>
```

### Remove a network

```bash
docker network rm <network_name>
```

### Remove all unused networks

```bash
docker network prune
```

### Run container in a custom network

```bash
docker run --network <network_name> <image_name>
```

---

## ⚙️ DOCKERFILE (BASICS)

### Sample Dockerfile

```Dockerfile
FROM python:3.11-slim
WORKDIR /app
COPY requirements.txt .
RUN pip install -r requirements.txt
COPY . .
CMD ["python", "app.py"]
```

---

## 🚀 DOCKER COMPOSE (ADVANCED)

### docker-compose.yml example

```yaml
version: '3.9'
services:
  web:
    build: .
    ports:
      - "5000:5000"
    volumes:
      - .:/app
    environment:
      - ENV=development
```

### Start services

```bash
docker compose up -d
```

### Stop services

```bash
docker compose down
```

---

## 🧹 CLEANUP COMMANDS (IMPORTANT)

```bash
docker system df            # Disk usage
docker system prune         # Remove unused containers, images, networks
docker system prune -a      # Remove everything unused
```

---

## ✅ BEST PRACTICES

* Use **small base images** (alpine, slim)
* Avoid running containers as root
* Use `.dockerignore`
* Tag images properly
* Prefer `--mount` over `-v`
* Use Docker Compose for multi-container apps
