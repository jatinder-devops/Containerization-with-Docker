# 11 — .dockerignore

## What Is .dockerignore?

`.dockerignore` is a file used to exclude matching files and directories from the Docker build context.

## Example

```text
.git
.gitignore
.env
*.log
node_modules/
tmp/
```

## Why Use It?

- Reduce unnecessary build-context data.
- Avoid sending irrelevant files to the builder.
- Help prevent accidental inclusion of local files.
- Improve build performance in some workflows.

## Example Directory

```text
my-project/
├── Dockerfile
├── .dockerignore
├── index.html
├── .git/
├── .env
└── debug.log
```

With suitable `.dockerignore` patterns, the Git directory, local environment file, and logs are excluded from the build context.

## Important Security Note

Do not rely on `.dockerignore` as your only secrets protection. Avoid putting secrets into image layers, and use secret-management mechanisms when credentials are needed.

## Practice Tasks

1. Create a `.dockerignore` file.
2. Exclude `.git` and log files.
3. Build the image.
4. Test what happens when you try to COPY an excluded file.
5. Explain why local environment files should generally be excluded.
