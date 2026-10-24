# 09 — EXPOSE Instruction

## What Is EXPOSE?

`EXPOSE` documents the port on which an application is expected to listen inside a container.

Example:

```dockerfile
FROM httpd:2.4

EXPOSE 80
```

## Does EXPOSE Publish the Port?

No. EXPOSE does not automatically make the container accessible from the host or internet.

To publish the port, use:

```bash
docker run -d --name apache-demo -p 8080:80 httpd:2.4
```

The mapping means:

- Host port: 8080
- Container port: 80

Test the website:

```bash
curl http://localhost:8080
```

## Port Mapping

```text
Browser
   |
   v
Host port 8080
   |
   v
Container port 80
   |
   v
Apache HTTP Server
```

## Important Notes

- EXPOSE is documentation in the image configuration.
- `-p` publishes a port.
- Host firewalls and network security rules still control external access.
- Publishing a port does not guarantee the application is running.

## Practice Tasks

1. Use EXPOSE in an Apache Dockerfile.
2. Run the container using host port 8081.
3. Test the website with curl.
4. Explain the difference between EXPOSE and `-p`.
