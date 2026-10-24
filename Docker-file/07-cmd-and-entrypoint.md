# 07 — CMD and ENTRYPOINT

## CMD

`CMD` specifies the default command or arguments used when a container starts.

Example:

```dockerfile
FROM ubuntu:24.04

CMD ["echo", "Hello from CMD"]
```

Build and run:

```bash
docker build -t cmd-demo .
docker run --rm cmd-demo
```

## ENTRYPOINT

`ENTRYPOINT` defines the main executable that the container runs.

Example:

```dockerfile
FROM ubuntu:24.04

ENTRYPOINT ["echo"]
CMD ["Hello from ENTRYPOINT"]
```

Run with default arguments:

```bash
docker run --rm entrypoint-demo
```

Override the default arguments:

```bash
docker run --rm entrypoint-demo "Hello DevOps"
```

## CMD vs ENTRYPOINT

- CMD provides a default command or arguments.
- ENTRYPOINT defines the main executable.
- Positional arguments supplied to `docker run` normally replace CMD.
- With an exec-form ENTRYPOINT, those arguments are passed to the executable.

## Shell Form and Exec Form

Exec form:

```dockerfile
CMD ["sleep", "30"]
```

Shell form:

```dockerfile
CMD sleep 30
```

Exec form is generally preferred for applications because it avoids an unnecessary shell process and supports signal handling more predictably.

## Practice Tasks

1. Create an image using CMD.
2. Create another using ENTRYPOINT.
3. Override CMD at runtime.
4. Explain how the two instructions work together.
5. Test how container stop signals affect a long-running process.
