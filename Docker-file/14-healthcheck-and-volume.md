# 14 — HEALTHCHECK and VOLUME

## HEALTHCHECK

`HEALTHCHECK` configures a command Docker uses to evaluate whether an application is healthy.

Example for a container with curl and a web server:

```dockerfile
HEALTHCHECK --interval=30s --timeout=5s --retries=3 \
  CMD curl -fsS http://127.0.0.1/ || exit 1
```

The application must actually listen on the specified URL, and curl must be installed.

Inspect container health:

```bash
docker ps
docker inspect --format='{{json .State.Health}}' container-name
```

A health check reports status; it does not automatically fix every failure.

## VOLUME

`VOLUME` declares a mount point intended for persistent or externally managed data.

Example:

```dockerfile
FROM ubuntu:24.04

VOLUME ["/data"]
```

A named volume can be used at runtime:

```bash
docker volume create app-data

docker run -d \
  --name volume-demo \
  -v app-data:/data \
  ubuntu:24.04 sleep infinity
```

Inspect the volume:

```bash
docker volume inspect app-data
```

## Why Persistent Storage Matters

A container can be removed and recreated. Data that exists only in its writable layer can be lost when the container is removed.

A named volume stores data independently of the container lifecycle.

## Practice Tasks

1. Create a named volume.
2. Write a test file into `/data`.
3. Remove the container and create another using the same volume.
4. Verify whether the file persists.
5. Explain why volumes still need a backup and recovery strategy.
