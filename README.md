

# Docker Concepts Cheat Sheet

A concise reference for core Docker concepts, commands, and workflows.  
This cheat sheet summarizes the essential ideas and commands that help you understand how Docker works and how to use it effectively.

---

## 📦 Core Docker Concepts

### 1. **Image**
- A snapshot/blueprint of an application and its environment.
- Built from a Dockerfile.
- Immutable (doesn’t change after it’s built).
- **Example:** `node:18`, `postgres:16`, or your custom `mycompany/base-server`.
- Occupies **disk space only** — serves as a **template** to create containers.

### 2. **Container**
- A running instance of an image.
- Isolated from the host and other containers.
- Has its own filesystem (stored on disk alongside the image), processes, and network.
- Multiple containers can be created from the same image.

### 3. **Dockerfile**
- A script with instructions to build a Docker image.
- Defines base image, files to copy, commands to run, etc.

### 4. **Docker Compose**
- Tool for defining and running multi-container Docker applications.
- Uses a `docker-compose.yml` file to specify services, networks, and volumes.

### 5. **Registry**
- Storage and distribution system for Docker images.
- **Examples:** Docker Hub, GitHub Container Registry, AWS ECR.

---

## 🗄️ Storage Concepts

### 6. **Volume**
- A persistent storage mechanism managed by Docker.
- Data persists even if the container is deleted.
- Commonly used for databases, user uploads, etc.
- A container can use one or more volumes, defined in `docker-compose.yml` or at runtime (e.g., `docker run -v`).

**Example (in `docker-compose.yml`):**
  ```
  volumes:
    - db-data:/var/lib/postgresql/data
  ```

- Managed with commands like:
  ```
  docker volume ls
  docker volume inspect <volume_name>
  ```

### 7. **Bind Mount**
- Maps a directory or file from your host machine directly into the container.
- Changes on the host are reflected in the container (and vice versa).
- Great for development (e.g., mount your source code for live editing).

**Example (in `docker-compose.yml`):**
  ```
  volumes:
    - .:/usr/src/app
  ```

---

## 🌐 Networking Concepts

### 8. **Network**
- Allows Docker containers to communicate with each other.
- By default, Compose creates a network for your app’s services.
- You can define custom networks for more control.

---

## 🔄 Lifecycle & Management

### 9. **Build**
- Creates a Docker image from a Dockerfile.
- **Command:**
  ```bash
  docker build -t myimage .
  ```

### 10. **Run**
- Starts a container from an image.
- **Command:**
  ```bash
  docker run myimage
  ```

### 11. **Pull / Push**
- Download or upload images from/to a registry.
- **Commands:**
  ```bash
  docker pull <image>
  docker push <image>
  ```

### 12. **Exec**
- Run a command inside a running container.
- **Example:**
  ```bash
  docker exec -it <container> bash
  ```

---

## 🛠️ Useful Docker Commands

| Command                                | Description                                 |
|-----------------------------------------|---------------------------------------------|
| `docker ps`                            | List running containers                    |
| `docker images`                        | List images on your system                  |
| `docker stop <container>`              | Stop a running container                   |
| `docker rm <container>`                | Remove a container                         |
| `docker rmi <image>`                   | Remove an image                            |
| `docker volume ls`                     | List volumes                               |
| `docker-compose up`                    | Start all services in the Compose file     |
| `docker-compose down`                  | Stop and remove services/volumes/networks  |

---

## 📝 Summary Table of Key Concepts

| Concept       | What It Is                             | Example / Use Case              |
|---------------|-----------------------------------------|---------------------------------|
| Image         | Blueprint for containers               | `node:18`, `postgres:16`        |
| Container     | Running instance of an image           | Your app or DB running isolated |
| Dockerfile    | Script to build an image                | Defines app setup              |
| Compose       | Multi-container orchestration          | App + DB together              |
| Registry      | Image storage and distribution         | Docker Hub, AWS ECR            |
| Volume        | Persistent storage (managed by Docker) | Database data, user uploads    |
| Bind Mount    | Host directory/file mapped into container | Live code editing in dev    |
| Network       | Communication between containers       | App talks to DB by name        |

---

## 🎯 Why This Cheat Sheet?
I created this Docker concepts cheat sheet to solidify my understanding of Docker and help others quickly grasp the key ideas and commands!

---

## 📜 License
MIT License.
