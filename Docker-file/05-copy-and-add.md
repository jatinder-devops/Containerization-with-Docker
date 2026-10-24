# 05 — COPY and ADD Instructions

## What Is COPY?

`COPY` copies files or directories from the build context into the image.

## Example

```dockerfile
FROM httpd:2.4

COPY index.html /usr/local/apache2/htdocs/index.html
```

The local `index.html` becomes the website's main HTML file inside the image.

## What Is ADD?

`ADD` can copy local files and automatically extract supported local tar archives. It also supports additional source types in Docker builds, so use it only when those capabilities are needed.

## Example

```dockerfile
FROM ubuntu:24.04

ADD website.tar.gz /opt/website/
```
```

FROM httpd:2.4

COPY index.html /usr/local/apache2/htdocs/index.html
COPY assets/ /usr/local/apache2/htdocs/assets/

EXPOSE 80

```
A supported local tar archive is extracted into `/opt/website/`.

## COPY vs ADD

| Feature | COPY | ADD |
|---|---|---|
| Copy local files | Yes | Yes |
| Copy directories | Yes | Yes |
| Automatically extract supported local tar archives | No | Yes |
| Preferred for ordinary file copying | Yes | Usually not needed |

## Important: Build Context

Run `docker build` from a directory containing the files referenced by the Dockerfile, or explicitly supply the appropriate build context.

Files excluded by `.dockerignore` are not available for ordinary COPY/ADD operations from the build context.

## Practice Tasks

1. Copy an HTML file into an Apache image.
2. Copy a directory containing CSS files.
3. Experiment with a local tar archive using ADD.
4. Explain why COPY is normally preferred for simple file copying.
