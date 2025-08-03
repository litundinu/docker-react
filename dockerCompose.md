# 🐳 Docker Compose Cheat Sheet (`docker-compose.yml`)

## 📘 Version
```yaml
version: "3.8"  # Compose file format version
```

---

## 🧱 Services

```yaml
services:
  web:
    image: nginx:latest
    build:
      context: ./dir
      dockerfile: Dockerfile.dev
      args:
        APP_ENV: production
    ports:
      - "80:80"
    volumes:
      - ./code:/app
      - data-volume:/data
    environment:
      - DEBUG=true
      - PORT=8000
    env_file:
      - .env
    command: node server.js
    entrypoint: /entry.sh
    depends_on:
      - db
    networks:
      - backend
    restart: always
    container_name: my_web
    hostname: myhost
    working_dir: /app
    user: "1000:1000"
    extra_hosts:
      - "local.dev:127.0.0.1"
    healthcheck:
      test: ["CMD", "curl", "-f", "http://localhost"]
      interval: 30s
      timeout: 10s
      retries: 5
    logging:
      driver: "json-file"
      options:
        max-size: "10m"
        max-file: "3"
    deploy:  # Swarm only
      replicas: 2
      update_config:
        parallelism: 1
        delay: 10s
      restart_policy:
        condition: on-failure
    tty: true
    stdin_open: true
    privileged: true

  db:
    image: postgres:15
    environment:
      POSTGRES_USER: user
      POSTGRES_PASSWORD: pass
    volumes:
      - pg_data:/var/lib/postgresql/data
```

---

## 📦 Volumes

```yaml
volumes:
  data-volume:
    driver: local
    driver_opts:
      type: none
      device: /path/on/host
      o: bind

  pg_data: {}
```

---

## 🌐 Networks

```yaml
networks:
  backend:
    driver: bridge
    ipam:
      driver: default
      config:
        - subnet: "172.16.238.0/24"
```

---

## 🔐 Secrets (Swarm only)

```yaml
secrets:
  db_password:
    file: ./secrets/db_password.txt
```

Use in a service:

```yaml
    secrets:
      - db_password
```

---

## 🗂️ Configs (Swarm only)

```yaml
configs:
  my_config:
    file: ./default.conf
```

Use in a service:

```yaml
    configs:
      - source: my_config
        target: /etc/config/default.conf
```

---

## 💡 Tips

- Use `.env` files to manage environment variables cleanly.
- Validate your file with `docker-compose config`.
- Run containers with `docker-compose up -d`.
