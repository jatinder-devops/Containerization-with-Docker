# 01 — Introduction to Dockerfiles

## What Is a Dockerfile?

A Dockerfile is a text file containing instructions used by Docker to build a container image.

It describes the base image, application files, dependencies, environment configuration, and default startup behavior.

## Dockerfile vs Image vs Container

- **Dockerfile:** Instructions for building an image.
- **Image:** A packaged template used to create containers.
- **Container:** An isolated running or stopped instance of an image.
- **Registry:** A service used to store and distribute images.

## Why Use Dockerfiles?

- Automate image creation.
- Maintain consistent application environments.
- Version-control infrastructure and application packaging.
- Rebuild images consistently.
- Simplify application deployment.

## Basic Workflow

1. Write a Dockerfile.
2. Build an image.
3. Run a container.
4. Test the application.
5. Publish the image to a registry when required.

## Important Commands

```bash
docker --version
docker build -t my-image:v1 .
docker images
docker run --name my-container my-image:v1
docker ps -a
```

## Practice Exercise

Explain the difference between a Dockerfile, image, container, and registry. Draw a diagram showing how source code becomes a running application.

## Key Takeaway

A Dockerfile automates the process of packaging an application into a Docker image.
