# 15 — Dockerfile Best Practices

## 1. Use Trusted Base Images

Select maintained base images from trusted publishers.

## 2. Pin Versions When Appropriate

Use explicit version tags and consider immutable digests when reproducibility is critical.

## 3. Run as a Non-Root User

Use the USER instruction where the application supports it, and verify filesystem permissions.

## 4. Optimize Image Size

- Use multi-stage builds where appropriate.
- Remove unnecessary packages and temporary files.
- Avoid copying development dependencies into the final runtime image.

## 5. Use .dockerignore

Exclude unnecessary files, Git metadata, logs, and local secrets from the build context.

## 6. Never Embed Secrets

Do not place passwords, tokens, private keys, or database credentials in Dockerfiles, image layers, or ordinary build arguments.

## 7. Use Build Cache Effectively

Order instructions to reuse stable build steps when practical.

## 8. Scan and Test Images

Check for known vulnerabilities, verify application behavior, and rebuild when dependencies require security updates.

## 9. Configure Health Checks

Use an appropriate health check when Docker or your deployment platform can use the result.

## 10. Document the Build

Explain how to build, run, configure, and troubleshoot the application.

## Example Checklist

- [ ] Base image is trusted and maintained.
- [ ] Unnecessary packages are excluded.
- [ ] Application runs as a non-root user where practical.
- [ ] No secrets are embedded in the image.
- [ ] .dockerignore is configured.
- [ ] Image is tested and scanned.
- [ ] Application configuration is documented.
- [ ] Image versions are tracked.

## Practice Assignment

Review an existing Dockerfile and identify at least five improvements related to security, image size, maintainability, or reliability.****
