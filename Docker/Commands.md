## 🐳✨ Docker Ad-hoc Commands — Full & Advanced Cheat Sheet

---

### 📦 1️⃣ Images
| Command                                            | What it does                                     |
| -------------------------------------------------- | ------------------------------------------------ |
| `docker pull <image>`                              | Download an image from a registry.               |
| `docker build -t <name> <context>`                 | Build an image from a Dockerfile in `<context>`. |
| `docker build -f <Dockerfile> -t <name> <context>` | Specify a custom Dockerfile.                     |
| `docker images`                                    | List local images.                               |
| `docker rmi <image>`                               | Remove an image.                                 |
| `docker tag <source> <target>`                     | Tag an image.                                    |
| `docker push <image>`                              | Push an image to a registry.                     |
| `docker save -o <file>.tar <image>`                | Save image as a tar archive.                     |
| `docker load -i <file>.tar`                        | Load an image from a tar archive.                |
| `docker image prune`                               | Remove dangling images.                          |
| `docker image history <image>`                     | Show history of image layers.                    |

---

### 🐳 2️⃣ Containers
| Command                                                       | What it does                                    |
| ------------------------------------------------------------- | ----------------------------------------------- |
| `docker run <image>`                                          | Run a container.                                |
| `docker run --name <name> <image>`                            | Assign a custom name.                           |
| `docker run -it <image>`                                      | Interactive terminal.                           |
| `docker run -d <image>`                                       | Run in background (detached).                   |
| `docker run -p <host:container>`                              | Publish container port to host.                 |
| `docker run -v /host:/container`                              | **Bind mount:** use host dir inside container.  |
| `docker run -v myvolume:/data`                                | **Named volume:** use Docker-managed volume.    |
| `docker run --mount type=bind,source=/host,target=/container` | **Advanced bind mount using `--mount`.**        |
| `docker run --mount type=volume,source=myvolume,target=/data` | **Advanced named volume using `--mount`.**      |
| `docker run --mount type=tmpfs,target=/app/cache`             | **Tmpfs mount (in-memory)** for ephemeral data. |
| `docker run --network <network>`                              | Connect to a custom network.                    |
| `docker run --env VAR=value`                                  | Pass environment variables.                     |
| `docker run --rm <image>`                                     | Remove container when it exits.                 |
| `docker ps`                                                   | List running containers.                        |
| `docker ps -a`                                                | List all containers.                            |
| `docker start <container>`                                    | Start a stopped container.                      |
| `docker stop <container>`                                     | Stop a running container.                       |
| `docker restart <container>`                                  | Restart a container.                            |
| `docker kill <container>`                                     | Force stop a container immediately.             |
| `docker exec -it <container> <cmd>`                           | Run a command inside a running container.       |
| `docker attach <container>`                                   | Attach to a running container’s output.         |
| `docker logs <container>`                                     | Show logs.                                      |
| `docker logs -f <container>`                                  | Follow logs (like `tail -f`).                   |
| `docker inspect <container>`                                  | JSON details.                                   |
| `docker cp <container>:<path> <host>`                         | Copy files between host and container.          |
| `docker rename <old> <new>`                                   | Rename a container.                             |
| `docker commit <container> <newimage>`                        | Create a new image from container changes.      |
| `docker export <container>`                                   | Export container filesystem as tar.             |
| `docker import <file>.tar`                                    | Import tar as image.                            |

---

### 📂 3️⃣ Volumes
| Command                                                               | What it does               |
| --------------------------------------------------------------------- | -------------------------- |
| `docker volume create <name>`                                         | Create a volume.           |
| `docker volume ls`                                                    | List volumes.              |
| `docker volume inspect <name>`                                        | Inspect volume details.    |
| `docker volume rm <name>`                                             | Remove a volume.           |
| `docker volume prune`                                                 | Remove all unused volumes. |
| **Example bind mount:**                                               |                            |
| `docker run -v /host/data:/container/data alpine`                     |                            |
| **Example named volume:**                                             |                            |
| `docker run -v myvolume:/data alpine`                                 |                            |
| **Example advanced `--mount`:**                                       |                            |
| `docker run --mount type=bind,source="$(pwd)"/app,target=/app alpine` |                            |

---

### 🌐 4️⃣ Networks
| Command                                           | What it does                         |
| ------------------------------------------------- | ------------------------------------ |
| `docker network ls`                               | List networks.                       |
| `docker network create <name>`                    | Create a custom network.             |
| `docker network inspect <name>`                   | Inspect a network.                   |
| `docker network rm <name>`                        | Remove a network.                    |
| `docker network connect <network> <container>`    | Connect container to a network.      |
| `docker network disconnect <network> <container>` | Disconnect container from a network. |
| **Example with custom bridge:**                   |                                      |
| `docker network create mynet`                     |                                      |
| `docker run -d --network mynet nginx`             |                                      |

---

### 🧹 5️⃣ System Cleanup
| Command                  | What it does                                             |
| ------------------------ | -------------------------------------------------------- |
| `docker system df`       | Show disk usage.                                         |
| `docker system prune`    | Remove unused containers, networks, images, build cache. |
| `docker system prune -a` | Same + remove unused images.                             |
| `docker container prune` | Remove stopped containers.                               |
| `docker image prune`     | Remove dangling images.                                  |
| `docker volume prune`    | Remove unused volumes.                                   |
| `docker builder prune`   | Clean up build cache.                                    |

---

### 🏗️ 6️⃣ Build Cache & Context
| Command                              | What it does                       |
| ------------------------------------ | ---------------------------------- |
| `docker build --no-cache`            | Build without cache.               |
| `docker build --build-arg VAR=value` | Pass build arguments.              |
| `docker build --target <stage>`      | Build specific multi-stage target. |

---

### 🔑 7️⃣ Misc & Debug
| Command                   | What it does                        |
| ------------------------- | ----------------------------------- |
| `docker info`             | Show Docker system info.            |
| `docker version`          | Docker version details.             |
| `docker events`           | Stream real-time Docker events.     |
| `docker top <container>`  | Show processes in container.        |
| `docker stats`            | Live resource usage for containers. |
| `docker diff <container>` | Changes to container filesystem.    |

---

### ✅ Example Advanced `--mount` vs `-v`
| Use case         | `-v` syntax           | `--mount` syntax                                     |
| ---------------- | --------------------- | ---------------------------------------------------- |
| **Bind mount**   | `-v /host:/container` | `--mount type=bind,source=/host,target=/container`   |
| **Named volume** | `-v myvol:/container` | `--mount type=volume,source=myvol,target=/container` |
| **Tmpfs**        | N/A                   | `--mount type=tmpfs,target=/cache`                   |

---

### ⚡ Pro Tip
- `-v` is simpler and shorter — best for quick use.
- `--mount` is clearer for advanced options (e.g. read-only).

---

### 🎉 Full Power in One Cheat Sheet
✅ **This covers:**
- All everyday tasks
- Bind mounts
- Volumes
- Custom networks
- Cleanup
- Advanced build and inspect
