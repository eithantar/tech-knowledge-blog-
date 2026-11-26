# What Are Docker and Docker Compose?

> Read in: **English** | [မြန်မာ](docker-and-docker-compose-mm.md)

Have you ever heard a developer say, *"But it works on my machine!"*?

An application might run perfectly on one computer but fail on another because of a different operating system, a missing library, or a different version of Python or a database.

Installing and configuring everything by hand on every computer and server takes time and often leads to mistakes.

This is the problem that **Docker** solves.

## 1. What Is Docker?

In simple terms, Docker is a tool that packages an application together with everything it needs to run — code, libraries, settings, and runtime — into a single unit called a **container**.

The easiest way to understand Docker is to think about a **game machine**.

When you buy a game disc, you don't need to install a graphics engine, sound drivers, or special settings. You put the disc into the game machine and it just plays. The same disc plays the same way on any compatible machine — at your home, at a friend's home, or at a game center.

Docker works the same way:

- The **game disc** contains everything the game needs → a Docker **image** contains everything the application needs.
- The **game machine** runs the disc → **Docker** runs the image.
- The **game being played** → a running **container**.

If Docker is installed, the application runs the same way on your laptop, a teammate's computer, or a cloud server.

## 2. Key Docker Concepts (The Game Machine Way)

| Docker | Game Machine Example | Meaning |
|---|---|---|
| **Docker Engine** | The game machine | The software that runs containers |
| **Image** | The game disc | A read-only package of the application and its environment |
| **Container** | The game currently being played | A running instance of an image |
| **Dockerfile** | The instructions used to make the game disc | Step-by-step instructions for building an image |
| **Registry (Docker Hub)** | The online game store | A place to download and share images |
| **Volume** | The memory card / save data | Stores data outside the container so it isn't lost |
| **Network** | Multiplayer connection | Lets containers talk to each other |
| **Docker Compose** | A game center control panel | Starts and manages many machines together |

**Image – The Game Disc**

An image never changes once it is created, just like a game disc. You can play the same disc again and again.

**Container – The Game Being Played**

One disc can be played on many machines at the same time. In the same way, you can start many containers from one image.

**Volume – The Memory Card**

When you turn off the game machine, your progress would be lost without a memory card. Containers are the same: when a container is deleted, its data is lost. A volume works like a memory card and keeps important data, such as a database, safe.

**Network – Multiplayer**

In a multiplayer game, machines connect to each other. Docker networks let containers communicate, for example, a game server talking to a database.

## 3. Containers vs Virtual Machines

Both containers and virtual machines (VMs) create isolated environments, but they work differently.

Using the game example: a **virtual machine** is like buying a whole new game machine for every game. A **container** is like putting a different disc into the same machine.

| | Container | Virtual Machine |
|---|---|---|
| Operating System | Shares the host OS kernel | Runs a full guest OS |
| Size | Small (MBs) | Large (GBs) |
| Startup Time | Seconds | Minutes |
| Resource Usage | Light | Heavy |

Because containers are lightweight, you can run many of them on a single machine.

## 4. Writing a Dockerfile

In this article, our example application is a **game score server** — a small Python web API that saves players' scores and shows a leaderboard.

Project structure:

```
game-server/
├── app.py
├── requirements.txt
└── Dockerfile
```

**Dockerfile** (the instructions for making our "game disc")

```dockerfile
# 1. Start from an official Python image
FROM python:3.12-slim

# 2. Set the working directory inside the container
WORKDIR /app

# 3. Install dependencies
COPY requirements.txt .
RUN pip install --no-cache-dir -r requirements.txt

# 4. Copy the application code
COPY . .

# 5. Command to run when the container starts
CMD ["python", "app.py"]
```

## 5. Basic Docker Commands

```bash
# Make the "game disc" (build an image)
docker build -t game-server:1.0 .

# Put the disc in and start playing (run a container)
docker run -d -p 5000:5000 --name game-server game-server:1.0

# See which games are running
docker ps

# View the container's logs
docker logs game-server

# Stop the game and remove it
docker stop game-server
docker rm game-server

# List your game discs (images)
docker images

# Download a disc from the store (Docker Hub)
docker pull postgres:16
```

## 6. What Is Docker Compose?

Real applications usually need more than one service.

Our game score server needs:
- The **game server** (Python API)
- A **database** (PostgreSQL) to save scores
- Later, a **load balancer** (Nginx) to share players across servers

Imagine running a **game center**. Turning on every machine one by one, inserting the right disc, and connecting the cables every morning would be tiring.

Instead, the game center has a **control panel**. Press one button and every machine turns on with the right game.

**Docker Compose** is that control panel. You describe all your services in one YAML file, and start everything with a single command.

## 7. Writing a Docker Compose File

**compose.yaml** (or `docker-compose.yml`)

```yaml
services:
  game-server:
    build: .
    ports:
      - "5000:5000"
    environment:
      DATABASE_URL: postgresql://user:password@db:5432/games
    depends_on:
      - db

  db:
    image: postgres:16
    environment:
      POSTGRES_USER: user
      POSTGRES_PASSWORD: password
      POSTGRES_DB: games
    volumes:
      - score-data:/var/lib/postgresql/data

volumes:
  score-data:
```

What this file means:

- **services** – The machines in our game center.
- **game-server** – Built from the Dockerfile in this folder and available on port 5000.
- **db** – Uses the official PostgreSQL image to store scores.
- **depends_on** – Starts the database before the game server.
- **volumes** – The memory card. Player scores are kept even if the container is removed.

The game server connects to the database using the hostname `db`. Docker Compose automatically creates a network, so services can find each other by their service names — like players joining the same multiplayer room.

## 8. Basic Docker Compose Commands

```bash
# Press the "power on" button for the whole game center
docker compose up -d

# Rebuild the discs and start
docker compose up -d --build

# See which services are running
docker compose ps

# View logs from all services
docker compose logs -f

# Turn everything off
docker compose down

# Turn everything off AND erase the memory cards (deletes data!)
docker compose down -v
```

## 9. Scalability – Adding More Game Machines

**The problem**

Your game center has one machine for a popular game. On weekdays it's fine, but on Saturday 100 people are waiting in line.

The solution is simple: **add more machines with the same game disc**, and have a staff member at the entrance send each new player to a free machine.

**Scalability** in software means the same thing: when more users arrive, you run more copies of your application and share the traffic between them.

With Docker, every copy is started from the same image, so every "machine" plays exactly the same game.

**Step 1 – Add a load balancer (the staff member at the entrance)**

**nginx.conf**

```nginx
events {}

http {
  upstream game_servers {
    server game-server:5000;
  }

  server {
    listen 80;
    location / {
      proxy_pass http://game_servers;
    }
  }
}
```

**Step 2 – Update compose.yaml**

```yaml
services:
  nginx:
    image: nginx:1.27
    ports:
      - "80:80"
    volumes:
      - ./nginx.conf:/etc/nginx/nginx.conf:ro
    depends_on:
      - game-server

  game-server:
    build: .
    # No fixed host port here: only Nginx talks to the game servers,
    # so we can run many copies without port conflicts.
    environment:
      DATABASE_URL: postgresql://user:password@db:5432/games
    depends_on:
      - db

  db:
    image: postgres:16
    environment:
      POSTGRES_USER: user
      POSTGRES_PASSWORD: password
      POSTGRES_DB: games
    volumes:
      - score-data:/var/lib/postgresql/data

volumes:
  score-data:
```

**Step 3 – Scale up for the weekend**

```bash
# Run 5 game servers instead of 1
docker compose up -d --scale game-server=5

# Let Nginx discover the new servers
docker compose restart nginx

# Check: you should see game-server-1 ... game-server-5
docker compose ps
```

**Step 4 – Scale down on Monday**

```bash
docker compose up -d --scale game-server=2
docker compose restart nginx
```

Players still connect to one address (port 80). Nginx sends each request to one of the game servers, so no single machine gets overloaded.

**What about very large scale?**

Docker Compose is great for one server. When a game becomes really popular and you need many servers — or want machines to be added **automatically** when traffic increases — tools like **Kubernetes** or **AWS ECS** take the same Docker images and scale them across many computers.

## 10. Manageability – Running the Game Center Easily

Imagine managing a game center with 50 machines. You need to:

- Update the game to a new version on every machine
- Go back to the old version if the new one has bugs
- Restart machines that freeze
- Make sure one machine doesn't use all the electricity

Doing this by hand for every machine would be a nightmare. Docker makes all of this simple.

**Example 1 – Updating every machine at once**

Without Docker: visit each server, install the new code, update libraries, hope nothing breaks.

With Docker: build a new disc and swap it everywhere.

```yaml
  game-server:
    build: .
    image: game-server:1.1   # was 1.0
```

```bash
docker compose up -d --build
```

Every game server is replaced with version 1.1.

**Example 2 – Rolling back when something goes wrong**

Version 1.1 has a bug and scores are not saving? Put the old disc back in.

```yaml
    image: game-server:1.0
```

```bash
docker compose up -d
```

Because the old image still exists, rollback takes seconds.

**Example 3 – Automatic restart when a machine freezes**

A game center staff member restarts a frozen machine. Docker can do it automatically.

```yaml
  game-server:
    restart: unless-stopped
```

If the game server crashes, Docker starts it again by itself.

**Example 4 – Health checks**

Don't let players onto a machine that is still loading. A health check tells Docker when a service is really ready.

```yaml
  db:
    image: postgres:16
    healthcheck:
      test: ["CMD-SHELL", "pg_isready -U user -d games"]
      interval: 5s
      retries: 5

  game-server:
    depends_on:
      db:
        condition: service_healthy
```

Now the game server only starts after the database is ready to accept connections.

**Example 5 – Resource limits**

One broken machine shouldn't use all the power in the game center. You can limit how much CPU and memory each container may use.

```yaml
  game-server:
    deploy:
      resources:
        limits:
          cpus: "0.5"
          memory: 256M
```

**Example 6 – Settings in one place**

Instead of changing settings on every machine, keep them in a `.env` file.

**.env**

```
POSTGRES_USER=user
POSTGRES_PASSWORD=change-me
POSTGRES_DB=games
```

**compose.yaml**

```yaml
  db:
    image: postgres:16
    env_file: .env
```

Change the value once, and every service uses the new setting. (Don't commit `.env` files that contain real passwords to Git.)

**Example 7 – One place to watch everything**

```bash
# Logs from every machine in one screen
docker compose logs -f

# Logs from only the game servers
docker compose logs -f game-server

# CPU and memory usage of every container
docker stats
```

## 11. Where Can We Use Docker?

**1. Development**

Every team member gets the same environment with one command, so setup takes minutes instead of hours.

**2. Testing and CI/CD**

Automated tests run in clean, consistent containers every time code is pushed.

**3. Deployment**

The same image that was tested can be deployed to servers or cloud platforms such as AWS (ECS, EKS), Google Cloud Run, or Azure.

**4. Microservices**

Large applications can be split into small services, each running in its own container — just like a game center where each machine runs its own game.

**5. Learning and Experimenting**

You can try databases or tools like MySQL, Redis, or Elasticsearch without installing them on your computer.

## 12. Best Practices

- Use official and small base images (for example, `python:3.12-slim`).
- Add a `.dockerignore` file to exclude unnecessary files such as `.git`, `__pycache__`, and `.env`.
- Don't store passwords or secrets directly in a Dockerfile or image.
- Use volumes for data that must be kept, such as databases.
- Run one main process per container.
- Pin image versions (for example, `postgres:16`) instead of always using `latest`.
- Tag your own images with versions (`game-server:1.0`, `game-server:1.1`) so you can roll back easily.

## Conclusion

Docker is like a game machine: put in the disc (image), and the game (container) runs the same way everywhere. Docker Compose is the game center's control panel that starts and manages all the machines together.

With Docker, you can **scale** by adding more identical machines when players arrive, and **manage** everything — updates, rollbacks, restarts, and limits — from one place.

Whether you are building a web scraper, an AI application, or a game server, Docker is an essential tool for modern software development.

**Build once, run anywhere.**
