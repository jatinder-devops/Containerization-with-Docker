# 08 — ENV and ARG

## ENV Instruction

`ENV` sets an environment variable in the image configuration.

```dockerfile
FROM ubuntu:24.04

ENV APP_ENV=development

CMD ["sh", "-c", "echo $APP_ENV"]
```

Run:

```bash
docker build -t env-demo .
docker run --rm env-demo
```

Override the value:

```bash
docker run --rm -e APP_ENV=production env-demo
```

## ARG Instruction

`ARG` defines a build-time variable.

```dockerfile
FROM ubuntu:24.04

ARG APP_VERSION=1.0

RUN echo "Building version ${APP_VERSION}"

CMD ["echo", "Build complete"]
```

Pass a different value:

```bash
docker build --build-arg APP_VERSION=2.0 -t arg-demo .
```

## ENV vs ARG

| Feature | ENV | ARG |
|---|---|---|
| Primary purpose | Image/runtime configuration | Build-time configuration |
| Set using | `ENV` | `--build-arg` |
| Available to the running application by default | Yes | Not automatically |
| Suitable for secrets | No | No |

## Security Warning

Never place passwords, API keys, private keys, or database credentials in Dockerfile instructions or ordinary build arguments.

Use appropriate secret-management systems and, for build-time credentials, BuildKit secret mounts.

## Practice Tasks

1. Set `APP_ENV=development`.
2. Override it to `production` at runtime.
3. Pass a version through ARG.
4. Explain when you would use ENV instead of ARG.
