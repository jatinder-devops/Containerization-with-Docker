# 04 — RUN Instruction

## What Is RUN?

`RUN` executes a command while Docker builds an image. The filesystem changes made by that command become part of the resulting image.

## Syntax

```dockerfile
RUN command
```

## Example

```dockerfile
FROM ubuntu:24.04

RUN apt-get update && \
    apt-get install -y --no-install-recommends curl && \
    rm -rf /var/lib/apt/lists/*

CMD ["curl", "--version"]
```

## Build and Run

```bash
docker build -t run-demo:v1 .
docker run --rm run-demo:v1
```

The output should display the installed curl version.

## Why Use RUN?

- Install software packages.
- Create directories.
- Set up application dependencies.
- Prepare files and permissions.

## Best Practices

- Combine related package-management operations appropriately.
- Clean up unnecessary package files.
- Avoid installing unnecessary packages.
- Do not store secrets in image layers.
- Remember that RUN executes during the build, not each time the container starts.

## Practice Tasks

1. Install `curl` in an Ubuntu image.
2. Create a directory named `/app`.
3. Check whether the directory exists inside a container.
4. Compare an image with and without unnecessary packages.
