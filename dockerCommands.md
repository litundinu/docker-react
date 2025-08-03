# 🐳 Docker CLI Commands Cheat Sheet

---

## 🔧 `docker build`

```bash
docker build [OPTIONS] PATH | URL | -
```

**Common Flags:**
- `-t`, `--tag`: Name and optionally a tag (`name:tag`)
- `-f`, `--file`: Dockerfile location
- `--build-arg`: Set build-time variables
- `--no-cache`: Do not use cache
- `--pull`: Always attempt to pull newer image
- `--target`: Build a specific stage in a multi-stage Dockerfile

---

## 🚀 `docker run`

```bash
docker run [OPTIONS] IMAGE [COMMAND] [ARG...] 
```

**Common Flags:**
- `-d`, `--detach`: Run in background
- `-p`, `--publish`: Port mapping (`host:container`)
- `--name`: Container name
- `-e`, `--env`: Set environment variables
- `--env-file`: Load environment vars from file
- `-v`, `--volume`: Mount volumes
- `--rm`: Auto remove container on exit
- `--network`: Connect to a specific network
- `--restart`: Restart policy (`no`, `always`, `on-failure`)
- `--entrypoint`: Override entrypoint
- `-it`: Interactive + TTY
- `--privileged`: Give extended privileges

---

## 📂 `docker ps`

```bash
docker ps [OPTIONS]
```

**Common Flags:**
- `-a`, `--all`: Show all containers (default shows running)
- `-q`, `--quiet`: Only display container IDs
- `--format`: Format output using Go template

---

## 🛑 `docker stop` / `docker kill`

```bash
docker stop [OPTIONS] CONTAINER [CONTAINER...]
docker kill [OPTIONS] CONTAINER [CONTAINER...]
```

- `-t`, `--time`: Seconds to wait for stop before killing

---

## ❌ `docker rm`

```bash
docker rm [OPTIONS] CONTAINER [CONTAINER...]
```

- `-f`, `--force`: Force removal
- `-v`, `--volumes`: Remove anonymous volumes

---

## 📥 `docker pull`

```bash
docker pull [OPTIONS] NAME[:TAG|@DIGEST]
```

- `--all-tags`, `-a`: Download all tags
- `--quiet`, `-q`: Suppress verbose output

---

## 📤 `docker push`

```bash
docker push [OPTIONS] NAME[:TAG]
```

- No major flags besides credentials and registry config (use `docker login` before)

---

## 🏷️ `docker tag`

```bash
docker tag SOURCE_IMAGE[:TAG] TARGET_IMAGE[:TAG]
```

Used to rename or version an image.

---

## 🧼 `docker rmi`

```bash
docker rmi [OPTIONS] IMAGE [IMAGE...]
```

- `-f`, `--force`: Force removal

---

## 🔍 `docker images`

```bash
docker images [OPTIONS]
```

- `-a`, `--all`: Show all images
- `-q`, `--quiet`: Show only IDs
- `--digests`: Show image digests
- `--filter`: Filter output

---

## 🧾 `docker logs`

```bash
docker logs [OPTIONS] CONTAINER
```

- `-f`, `--follow`: Follow logs
- `--tail`: Lines from the end (`--tail 100`)
- `-t`: Show timestamps

---

## 🔄 `docker exec`

```bash
docker exec [OPTIONS] CONTAINER COMMAND [ARG...]
```

- `-it`: Interactive with TTY
- `-u`, `--user`: Run as specific user
- `--env`: Set environment variable
- `-w`, `--workdir`: Working directory inside container

---

## 🔧 `docker inspect`

```bash
docker inspect [OPTIONS] NAME|ID
```

- `-f`, `--format`: Format output using Go template
- Useful to get container IP, volumes, etc.

---

## 📊 `docker stats`

```bash
docker stats [OPTIONS] [CONTAINER...]
```

- Real-time metrics
- `--no-stream`: Only show one-time snapshot

---

## 🗺️ `docker network`

```bash
docker network [COMMAND]`
```

Commands:
- `ls`: List networks
- `create`: Create a network
- `inspect`: Inspect a network
- `rm`: Remove a network

---

## 🗃️ `docker volume`

```bash
docker volume [COMMAND]`
```

Commands:
- `create`, `inspect`, `ls`, `rm`, `prune`

---

## 🧽 `docker system`

```bash
docker system prune -a
```

Cleans up unused containers, networks, volumes, and images.

---

## 📋 `docker-compose`

```bash
docker-compose [COMMAND] [OPTIONS]
```

Most common:
- `up -d`: Start services in background
- `down`: Stop and remove containers/networks
- `logs -f`: Stream logs
- `build`: Build images
- `ps`: List containers
- `exec`, `run`, `restart`, `stop`, `start`

---

Let me know if you'd like this exported to a `.md` or `.pdf` file!