## Intermediate Docker Scenario-Based Interview Questions

Here are some scenario-based Docker questions suitable for candidates with basic experience, moving beyond fresher-level knowledge:

---

**1. You need to update a running container with a new version of your application. How would you do this with minimal downtime?**

- Build a new Docker image with the updated application version.
- Stop the existing container.
- Start a new container from the updated image, mapping the necessary ports and volumes.
- Optionally, use Docker Compose or orchestration tools to perform a rolling update for zero downtime.

---

**2. A containerized application needs to persist user-uploaded files, but you notice files are lost after a container restart. What is the problem and how do you fix it?**

- By default, files written inside a container are lost when the container is removed or recreated.
- Solution: Use Docker volumes to persist data by mounting a host directory or a named volume to the container’s file path where uploads are stored.

---

**3. You have multiple containers that need to communicate with each other. How can you enable this communication securely?**

- Use Docker’s user-defined bridge network to allow containers to communicate by name.
- For sensitive data, use overlay networks with encryption, and consider network policies or firewalls to restrict traffic between containers.

---

**4. After deploying a multi-container application, one container fails to start and exits immediately. How would you troubleshoot this?**

- Check logs with `docker logs <container_name_or_id>`.
- Inspect the container’s configuration for errors in the Dockerfile or entrypoint.
- Verify dependencies and environment variables are correctly set.
- Use `docker inspect` to check for resource constraints or misconfigurations.

---

**5. You want to reduce the size of your Docker images for faster deployment. What steps would you take?**

- Use a minimal base image (e.g., `alpine`).
- Combine commands in the Dockerfile to reduce the number of layers.
- Remove unnecessary build tools and cache files after installation.
- Use multi-stage builds to separate build-time and runtime dependencies.

---

**6. How would you handle environment-specific configurations (like database URLs) in Docker containers?**

- Use environment variables, passed via the `-e` flag or `env_file` in Docker Compose.
- Avoid hardcoding sensitive data in the Dockerfile; use secrets management tools for production.

---

**7. You need to debug a running container. What are some methods you can use?**

- Use `docker exec -it <container_name_or_id> /bin/sh` or `/bin/bash` to get a shell inside the container.
- Inspect logs with `docker logs`.
- Check resource usage with `docker stats`.

---

**8. How can you ensure that your containers restart automatically if they crash or the Docker daemon restarts?**

- Use the `--restart` policy (e.g., `--restart always` or `--restart on-failure`) when running the container.

---

**9. How do you share data between a host and a container, and between multiple containers?**

- Use bind mounts or named volumes to share data between the host and containers.
- Use the same named volume in multiple containers to share data between them.

---

**10. If you need to scale a service to run multiple containers, how would you do this with Docker Compose?**

- Use the `docker-compose up --scale <service>=<number>` command to run multiple instances of a service.

---

These scenario-based questions test your understanding of Docker’s practical usage, troubleshooting, and best practices in real-world situations.
