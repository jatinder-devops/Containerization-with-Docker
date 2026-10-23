# 02 — My First Dockerfile

## Objective

Build a custom Apache HTTP Server image and serve a simple HTML page.

## Dockerfile Instructions

- `FROM` selects the Apache base image.
- `COPY` copies the website into Apache's document root.
- `EXPOSE` documents the application's container port.
```

FROM httpd:2.4

COPY index.html /usr/local/apache2/htdocs/index.html

EXPOSE 80

```
## Build the Image

```bash
docker build -t my-first-web:v1 .
```

## Run the Container

```bash
docker run -d --name my-first-web -p 8080:80 my-first-web:v1
```

## Verify the Application

```bash
docker ps
curl http://localhost:8080
docker logs my-first-web
```

Open `http://localhost:8080` in your browser.

## Clean Up

```bash
docker stop my-first-web
docker rm my-first-web
```

## Practice Tasks

1. Change the HTML heading.
2. Rebuild the image using tag `v2`.
3. Run the new version on a different host port.
4. Explain the meaning of `-d`, `--name`, and `-p`.

## Expected Result

The Apache container serves your custom HTML page successfully.
