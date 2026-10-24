# 03 — FROM Instruction

## What Is FROM?

`FROM` specifies the base image used to build an image. Most Dockerfiles begin with this instruction.

## Syntax

```dockerfile
FROM image-name:tag
```

## Examples

```dockerfile
FROM ubuntu:24.04
```

Starts from Ubuntu.

```dockerfile
FROM httpd:2.4
```

Starts from an Apache HTTP Server image.

```dockerfile
FROM python:3.12-slim
```

Starts from a Python image with a relatively minimal base.

## Why Is FROM Important?

A base image provides an existing filesystem and software environment. Choosing an appropriate base can reduce setup effort and improve consistency.

## Practical Lab

Create a Dockerfile:

```dockerfile
FROM ubuntu:24.04

CMD ["cat", "/etc/os-release"]
```

Build and run:

```bash
docker build -t ubuntu-base:v1 .
docker run --rm ubuntu-base:v1
```

## Important Notes

- Choose maintained and trusted base images.
- Use an appropriate version tag.
- Consider pinning the image digest when reproducibility is critical.
- A smaller image is not automatically more secure.

## Practice Tasks

1. Build an image using Ubuntu.
2. Build another using Apache.
3. Explain the difference between the two base images.
4. Find out why `FROM scratch` is different from a full operating-system image.
