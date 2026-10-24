# 16 — Docker Compose

## What Is Docker Compose?

Docker Compose is a tool for defining and running multi-container applications using a YAML configuration file.

## Dockerfile vs Compose

- Dockerfile defines how to build an image.
- Compose defines how services run, including ports, networks, volumes, and configuration.

## Example Project

This project builds an Apache image and runs it as a service.

### Start the Application

```bash
docker compose up -d --build
```

### Check the Service

```bash
docker compose ps
```

### View Logs

```bash
docker compose logs web
```

### Stop the Application

```bash
docker compose down
```
## docker-compose/Dockerfile
```
FROM httpd:2.4

COPY index.html /usr/local/apache2/htdocs/index.html

EXPOSE 80

```
## docker-compose/compose.yaml
```

services:
  web:
    build: .
    ports:
      - "8080:80"
    restart: unless-stopped

```
## Benefits

- Simple application startup.
- Centralized service configuration.
- Repeatable development environments.
- Easier management of service dependencies and networks.

## Practice Tasks

1. Create a Compose file for an Apache service.
2. Publish host port 8080 to container port 80.
3. Add a restart policy.
4. Run the service and inspect its logs.
5. Explain the difference between `docker run` and `docker compose up`.
