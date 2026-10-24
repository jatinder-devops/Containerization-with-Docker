# 06 — WORKDIR Instruction

## What Is WORKDIR?

`WORKDIR` sets the working directory for subsequent Dockerfile instructions.

If the directory does not exist, Docker creates it.

## Example

```dockerfile
FROM ubuntu:24.04

WORKDIR /app

COPY app.txt .

CMD ["pwd"]
```

If `app.txt` exists in the build context, it will be copied to `/app/app.txt`.

## Build and Run

```bash
docker build -t workdir-demo:v1 .
docker run --rm workdir-demo:v1
```

Expected output:

```text
/app
```

## Why Use WORKDIR?

- Keep application files organized.
- Make relative file paths easier to understand.
- Avoid repeatedly writing absolute paths.
- Improve Dockerfile readability.

## Important Note

WORKDIR affects subsequent instructions. It does not automatically move every file in the base image or change the working directory of unrelated processes.

## Practice Tasks

1. Set the working directory to `/app`.
2. Copy a file using a relative destination.
3. Create a second directory using an absolute path.
4. Check the location of your copied files.

## Key Takeaway

Use WORKDIR to establish a predictable working location for your application's build and runtime instructions.
