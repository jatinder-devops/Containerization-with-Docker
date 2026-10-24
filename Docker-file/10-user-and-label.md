# 10 — USER and LABEL Instructions

## USER

`USER` selects the user and optionally the group used for subsequent build instructions and the container's runtime process.

Example:

```dockerfile
FROM ubuntu:24.04

RUN useradd --create-home appuser

USER appuser

CMD ["id"]
```

Build and run:

```bash
docker build -t user-demo .
docker run --rm user-demo
```

The output should identify `appuser`.

### Why Use USER?

Running an application as a non-root user reduces the impact of some security failures.

Ensure the user has permission to read application files, write to necessary directories, and access required resources.

## LABEL

`LABEL` adds metadata to an image.

Example:

```dockerfile
FROM httpd:2.4

LABEL org.opencontainers.image.title="Apache Website"
LABEL org.opencontainers.image.version="1.0"
LABEL org.opencontainers.image.description="Dockerfile learning project"
```

Inspect image metadata:

```bash
docker image inspect apache-site:v1
```

### Why Use LABEL?

- Identify images.
- Store version and ownership metadata.
- Support automation and image-management workflows.

## Practice Tasks

1. Create a non-root user.
2. Run a container as that user.
3. Add image title and version labels.
4. Inspect the image configuration.
5. Explain why non-root execution matters.
