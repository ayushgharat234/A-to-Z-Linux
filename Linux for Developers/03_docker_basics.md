# Docker Basics

Docker allows you to package applications into "containers" that run anywhere.

---

## 1. Concepts

*   **Image**: The blueprint (read-only template). Like a CD.
*   **Container**: The running instance of an image. Like the music playing.
*   **Dockerfile**: The recipe to build an image.

---

## 2. Basic Commands

### Running Containers
```bash
# Run Hello World
docker run hello-world

# Run Nginx in background (-d) mapped to port 8080 (-p)
docker run -d -p 8080:80 nginx
```

### Managing Containers
```bash
# List running containers
docker ps

# List all containers (including stopped)
docker ps -a

# Stop a container
docker stop <container_id>

# Remove a container
docker rm <container_id>
```

### Managing Images
```bash
# List images
docker images

# Remove image
docker rmi <image_id>
```

---

## 3. The Dockerfile

To create your own image, write a `Dockerfile`.

**Example:**
```dockerfile
# Base image
FROM python:3.9

# Work directory
WORKDIR /app

# Copy code
COPY . .

# Install dependencies
RUN pip install flask

# Run command
CMD ["python", "app.py"]
```

### Build it
```bash
docker build -t my-flask-app .
```

---

## Summary
*   `docker run` starts containers.
*   `docker ps` shows what's running.
*   `docker build` creates images from a Dockerfile.
