# 17 — Production-Oriented Apache Website

## Project Overview

This project demonstrates how to package a static website into a Docker image using Apache HTTP Server.

The objective is to apply the Dockerfile instructions and practices learned throughout this repository.

## Objectives

- Create a custom Dockerfile.
- Use an Apache base image.
- Copy website files into the image.
- Build a versioned Docker image.
- Run a container with port mapping.
- Configure .dockerignore.
- Inspect logs and troubleshoot common errors.

## Technologies

- Docker
- Dockerfile
- Apache HTTP Server
- HTML
- Ubuntu Linux
## production-project/docker file
```

FROM httpd:2.4

LABEL org.opencontainers.image.title="DevOps Apache Website"
LABEL org.opencontainers.image.description="Dockerfile learning project"

COPY index.html /usr/local/apache2/htdocs/index.html

EXPOSE 80

```

## Build the Image

```bash
docker build -t devops-apache:v1 .
```

## Run the Container

```bash
docker run -d \
  --name devops-apache \
  -p 8080:80 \
  devops-apache:v1
```

## Verify the Deployment

```bash
docker ps
curl -I http://localhost:8080
docker logs devops-apache
```

A successful HTTP response should normally return status `200 OK`.

## Troubleshooting

If the container is not running:

```bash
docker ps -a
docker logs devops-apache
docker inspect devops-apache
```

If the website cannot be accessed, check the port mapping, application status, host firewall, and network security rules.

## Cleanup

```bash
docker stop devops-apache
docker rm devops-apache
```

## Future Improvements

- Add an automated build and test pipeline.
- Scan images for vulnerabilities.
- Use an appropriate non-root runtime where supported.
- Publish versioned images to a container registry.
- Add monitoring and deployment automation.

## Learning Outcome

This project demonstrates practical knowledge of Dockerfile authoring, image building, container execution, testing, and troubleshooting.
