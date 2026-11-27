# Client-Server Architecture and Three-Tier Architecture

> Read in: **English** | [မြန်မာ](client-server-and-three-tier-architecture-mm.md)

When you open Facebook, send an email, withdraw money from an ATM, or play an online game, you are using software that is split between **your device** and **a computer somewhere else**.

How that software is divided, and how the parts talk to each other, is called its **architecture**.

In this article, we'll look at two of the most important architectures in software engineering:

- **Client-Server Architecture** – The foundation of almost everything on the Internet.
- **Three-Tier Architecture** – The most common way to organize web and business applications.

## 1. What Is Client-Server Architecture?

**Client-Server Architecture** is a model where work is divided between two roles:

- **Client** – Asks for something (sends a **request**).
- **Server** – Provides it (sends a **response**).

```
┌──────────┐      Request       ┌──────────┐
│          │ ─────────────────► │          │
│  Client  │                    │  Server  │
│          │ ◄───────────────── │          │
└──────────┘      Response      └──────────┘
```

Key characteristics:

- **The client starts the conversation.** The server waits and listens for requests.
- **One server serves many clients** at the same time.
- **The server holds the shared resources**: data, files, business logic, and computing power.
- **They communicate over a network** using agreed rules called **protocols** (such as HTTP).

## 2. The Restaurant Example

Like in our earlier articles, think of a **restaurant**:

| Restaurant | Client-Server |
|---|---|
| Customers | **Clients** |
| The restaurant | **Server** |
| Placing an order | **Request** |
| Getting your food | **Response** |
| Speaking the same language as the waiter | **Protocol** |
| One restaurant serving many customers at once | **One server, many clients** |

Customers don't cook for themselves, and they don't need a kitchen at home. They just ask the restaurant, which has all the ingredients, equipment, and chefs. In the same way, your phone doesn't need to store all of Facebook. It just asks Facebook's servers.

## 3. Client-Server Examples in Everyday Life

| Client | Server | Protocol |
|---|---|---|
| Web browser (Chrome, Firefox) | Web server | HTTP / HTTPS |
| Email app (Gmail app, Outlook) | Mail server | SMTP, IMAP |
| Mobile banking app | Bank's API server | HTTPS |
| ATM | Bank's central server | Bank network protocols |
| Online game | Game server | TCP / UDP / WebSocket |
| Your computer looking up `google.com` | DNS server | DNS |

## 4. How Does a Client Find and Talk to a Server?

To reach a server, a client needs two things:

- **IP Address** – The server's address on the network, like the restaurant's street address. Example: `142.250.190.78`
- **Port** – A specific "door" on that server for a specific service, like the restaurant's front door vs. the delivery door. Examples: `80` for HTTP, `443` for HTTPS, `5432` for PostgreSQL.

Since IP addresses are hard to remember, we use **domain names** (like `google.com`), and **DNS** translates them into IP addresses.

## 5. Example: A Tiny Client-Server Program in Python

Let's build the simplest possible client and server, using only Python's built-in `socket` module. The server is a tea shop that answers menu questions.

**server.py**

```python
import socket

HOST = "127.0.0.1"  # This computer
PORT = 9000         # The "door" our server listens on

MENU = {
    "mohinga": "Mohinga - 2,500 MMK",
    "tea": "Laphet Yay - 800 MMK",
    "samosa": "Samosa - 500 MMK",
}

with socket.socket(socket.AF_INET, socket.SOCK_STREAM) as server:
    server.setsockopt(socket.SOL_SOCKET, socket.SO_REUSEADDR, 1)
    server.bind((HOST, PORT))
    server.listen()
    print(f"Tea shop server is open on {HOST}:{PORT}")

    while True:
        conn, address = server.accept()  # Wait for a customer
        with conn:
            order = conn.recv(1024).decode().strip().lower()
            print(f"Customer {address} asked for: {order}")

            answer = MENU.get(order, "Sorry, that's not on the menu.")
            conn.sendall(answer.encode())
```

**client.py**

```python
import socket

with socket.socket(socket.AF_INET, socket.SOCK_STREAM) as client:
    client.connect(("127.0.0.1", 9000))  # Go to the tea shop
    client.sendall(b"mohinga")            # Place an order (request)
    answer = client.recv(1024).decode()   # Get the answer (response)
    print("Server replied:", answer)
```

**Run it** (in two separate terminals)

```bash
# Terminal 1
python server.py

# Terminal 2
python client.py
```

**Output**

```
Server replied: Mohinga - 2,500 MMK
```

Run `client.py` several times, or change the order to `tea` or `pizza`. One server keeps answering many clients. That's client-server architecture in under 30 lines.

Real web servers work the same way underneath. Frameworks like FastAPI and Django just handle the low-level details (HTTP, many clients at once, security) for you.

## 6. Thin Client vs Thick Client

Clients can do a little work or a lot of work.

| | Thin Client | Thick (Fat) Client |
|---|---|---|
| Where most work happens | On the server | On the client |
| Client needs | Just a browser or a simple app | More processing power and storage |
| Example | A simple web page, Google Docs | A PC video game, Photoshop |
| Updates | Update the server once | Users must install updates |

Many modern apps are in between. For example, a single-page web app does a lot of work in the browser, but still gets its data from the server.

## 7. Client-Server vs Peer-to-Peer (P2P)

Not everything uses client-server. In **Peer-to-Peer**, every computer can act as both client and server.

| | Client-Server | Peer-to-Peer |
|---|---|---|
| Structure | Central server, many clients | All computers are equal "peers" |
| Data stored | On the server | Spread across all peers |
| If the server goes down | Service stops | Other peers keep working |
| Control and security | Easy to manage centrally | Harder to control |
| Examples | Websites, banking, email | BitTorrent, blockchain networks |

## 8. Advantages and Disadvantages of Client-Server

**Advantages**

- **Centralized data** – Everyone sees the same, up-to-date data.
- **Easier security** – Access rules are enforced in one place.
- **Easier updates** – Update the server, and all clients benefit.
- **Scalability** – Add more servers as the number of clients grows.

**Disadvantages**

- **Single point of failure** – If the server goes down, clients can't work (solved with backups and multiple servers).
- **Network dependency** – No network, no service.
- **Server overload** – Too many clients at once can slow the server down (solved with load balancing and scaling).

## 9. From Client-Server to Tiers

As applications grew bigger, developers started to split the **server side** into separate parts too. Each separate part is called a **tier**.

> **Tier vs Layer:** A **layer** is a *logical* separation in the code (for example, separate folders for UI, logic, and data). A **tier** is a *physical* separation, where each part can run on a different machine or container. You'll often hear the words used interchangeably, but this is the technical difference.

| Architecture | Tiers | Example |
|---|---|---|
| **1-Tier** | Everything on one machine | Excel, a desktop app with a local database file |
| **2-Tier** | Client + Database | An old shop's desktop app connecting directly to a MySQL server |
| **3-Tier** | Client + Application Server + Database | Most modern web applications |
| **N-Tier** | More than 3 (e.g., + cache, + load balancer, + separate services) | Large systems like Netflix or Amazon |

## 10. 2-Tier Architecture and Its Problems

In **2-Tier Architecture**, the client application talks **directly to the database**.

```
┌──────────────────────┐         ┌──────────────┐
│  Client Application  │ ──SQL─► │   Database   │
│  (UI + Logic)        │ ◄────── │              │
└──────────────────────┘         └──────────────┘
```

Back to the restaurant: this is like letting **customers walk into the storeroom** and take ingredients themselves.

It's simple, and it works for small offices, but it causes serious problems as the app grows:

- **Security risk** – Every client needs the database password. If one computer is hacked, the whole database is exposed.
- **Hard to update** – Business rules live in the client app, so every computer must be updated whenever a rule changes.
- **Cheating is easy** – Users can modify the client and send any data they want straight into the database.
- **Poor scalability** – Databases can only handle a limited number of direct connections.

Three-tier architecture solves these problems.

## 11. What Is Three-Tier Architecture?

**Three-Tier Architecture** divides an application into three independent tiers, each with its own job.

```
┌───────────────────────────────┐
│     1. PRESENTATION TIER      │   What users see and interact with
│   Browser / Mobile App (UI)   │   HTML, CSS, JavaScript, React, Flutter
└───────────────┬───────────────┘
                │ HTTP / API (JSON)
┌───────────────▼───────────────┐
│     2. APPLICATION TIER       │   Business logic and rules
│   Backend Server / API        │   Python, Node.js, Java, Go
└───────────────┬───────────────┘
                │ SQL / Queries
┌───────────────▼───────────────┐
│        3. DATA TIER           │   Stores and manages data
│          Database             │   PostgreSQL, MySQL, MongoDB
└───────────────────────────────┘
```

**The golden rule: each tier only talks to the tier next to it.** The presentation tier **never** talks to the database directly.

## 12. The Three Tiers in Detail

**1. Presentation Tier (Dining Room)**

- **Job:** Show information to users and collect their input.
- **Runs on:** The user's browser or phone.
- **Technologies:** HTML, CSS, JavaScript, React, Vue, mobile apps (Swift, Kotlin, Flutter).
- **Should NOT contain:** Important business rules or database passwords. Anything in the client can be seen and changed by users.

**2. Application Tier (Kitchen)**

- **Job:** Apply the business logic. For example: "Is this user logged in?", "Is there enough money in the account?", "Is this score valid?"
- **Runs on:** Servers you control.
- **Technologies:** Python (FastAPI, Django), Node.js (Express), Java (Spring Boot), Go.
- **Also called:** Logic tier, business tier, middle tier.

**3. Data Tier (Storeroom)**

- **Job:** Store, read, and protect data.
- **Runs on:** Database servers, usually in a private network.
- **Technologies:** PostgreSQL, MySQL, SQL Server, MongoDB.

In the restaurant, **customers stay in the dining room**, **only waiters and chefs go into the kitchen**, and **only kitchen staff go into the storeroom**. Each area has its own job and its own access rules.

## 13. Example: Following a Request Through the Three Tiers

Let's use an online banking transfer.

1. **Presentation tier** – You enter "Send 50,000 MMK to Su" in the banking app and press **Send**. The app sends a request to the API.
2. **Application tier** – The server checks:
   - Are you logged in?
   - Is the amount positive?
   - Do you have enough money?
   - Is this within your daily limit?
3. **Data tier** – If all checks pass, the server updates both accounts in the database.
4. **Back up the tiers** – The database confirms, the server sends "Transfer successful", and the app shows a ✅ message.

Your phone never touched the database. It only talked to the application tier.

## 14. Why Business Rules Must Live in the Application Tier

Let's go back to the game leaderboard from the [Web Application article](../Web-Application/what-is-web-application-en.md).

Imagine we check that scores are valid **only in the browser's JavaScript**. A cheater can open Browser DevTools, skip the check, and send:

```json
{ "player": "Cheater", "score": 99999999 }
```

That's why the rule must be in the **application tier**, where users can't change it:

```python
from fastapi import HTTPException

MAX_SCORE = 1_000_000


@app.post("/api/scores", status_code=201)
def add_score(score: Score):
    # Business rule: enforced in the application tier, not in the browser
    if not 0 <= score.score <= MAX_SCORE:
        raise HTTPException(status_code=400, detail="Invalid score")

    save_score(score)  # Only the application tier talks to the data tier
    return score
```

> Checking input in the browser is still useful for a better user experience (showing errors immediately). But the **real** check must always happen on the server.

## 15. Three-Tier Architecture With Docker Compose

Docker Compose makes the three tiers very clear. Each tier is a separate service, and **networks** control who can talk to whom.

**Project structure**

```
leaderboard/
├── frontend/
│   └── index.html         # Presentation tier files
├── backend/
│   ├── main.py            # Application tier
│   └── Dockerfile
├── nginx.conf
└── compose.yaml
```

**compose.yaml**

```yaml
services:
  # 1. Presentation tier: serves the HTML/JS to browsers
  web:
    image: nginx:1.27
    ports:
      - "80:80"
    volumes:
      - ./frontend:/usr/share/nginx/html:ro
      - ./nginx.conf:/etc/nginx/conf.d/default.conf:ro
    networks:
      - frontend

  # 2. Application tier: the API and business rules
  api:
    build: ./backend
    environment:
      DATABASE_URL: postgresql://user:password@db:5432/games
    networks:
      - frontend
      - backend

  # 3. Data tier: the database
  db:
    image: postgres:16
    environment:
      POSTGRES_USER: user
      POSTGRES_PASSWORD: password
      POSTGRES_DB: games
    volumes:
      - db-data:/var/lib/postgresql/data
    networks:
      - backend

networks:
  frontend:
  backend:

volumes:
  db-data:
```

**nginx.conf**

```nginx
server {
  listen 80;

  # Send the frontend files
  location / {
    root /usr/share/nginx/html;
  }

  # Forward API requests to the application tier
  location /api/ {
    proxy_pass http://api:8000;
  }
}
```

The backend's Dockerfile should start the server with `uvicorn main:app --host 0.0.0.0 --port 8000` so other containers can reach it.

**Notice the security design:**

- `web` is only on the `frontend` network, so it **cannot reach** the database.
- `db` is only on the `backend` network, and it has **no public port**, so nobody on the Internet can reach it.
- Only `api` is on both networks, so it is the **only bridge** to the data.

Customers stay in the dining room, and only the kitchen can enter the storeroom. (See the [Docker article](../Docker/docker-and-docker-compose-en.md) for more about Compose.)

## 16. Benefits of Three-Tier Architecture

**1. Security**

The database is hidden behind the application tier. Users never get database passwords, and every request goes through the business rules.

**2. Scalability – Scale each tier separately**

Lots of visitors? Add more application servers behind a load balancer. Heavy database load? Upgrade only the database or add read replicas. You don't have to scale everything together.

**3. Maintainability**

Each tier can be changed without rewriting the others. You can redesign the frontend without touching the database, or move from MySQL to PostgreSQL by changing only the data access code.

**4. One backend, many frontends**

The same application tier can serve a website, an Android app, an iOS app, and even other companies' systems through the same API.

```
  Website ──┐
  Android ──┼──► Application Tier (API) ──► Database
  iOS ──────┘
```

**5. Team specialization**

Frontend, backend, and database specialists can work in parallel on their own tier.

## 17. Disadvantages

- **More complexity** – Three things to build, deploy, and monitor instead of one.
- **More network hops** – Each request passes through more tiers, adding a little latency.
- **Overkill for tiny apps** – A personal script or a small offline tool doesn't need three tiers.

## 18. Three-Tier Architecture on AWS

A common way to build three tiers on AWS:

| Tier | AWS Services |
|---|---|
| **Presentation** | Amazon S3 + CloudFront (static frontend), or AWS Amplify |
| **Application** | Amazon EC2, ECS (containers), or AWS Lambda (serverless), behind an Application Load Balancer |
| **Data** | Amazon RDS (PostgreSQL/MySQL) or DynamoDB, in a **private subnet** |

The database in a private subnet follows the same rule as our Docker example: only the application tier can reach it.

## 19. Beyond Three Tiers

As systems grow even larger, more tiers and patterns are added:

- **Load balancer** – Spreads traffic across many application servers.
- **Cache tier** (Redis) – Keeps frequently used data in memory for speed.
- **Message queue** (RabbitMQ, Amazon SQS) – Handles slow tasks in the background, like sending emails.
- **Microservices** – Splits the application tier into many small, independent services (users, payments, orders), each with its own database.

But almost all of them are still built on the same idea: **clients ask, servers answer, and each part has one clear job.**

## Comparison Summary

| | 1-Tier | 2-Tier | 3-Tier |
|---|---|---|---|
| Structure | All in one | Client → Database | Client → App Server → Database |
| Security | Local only | Weak (clients access the DB) | Strong (DB hidden) |
| Scalability | None | Limited | High |
| Updating logic | Update each install | Update every client | Update the server once |
| Best for | Personal tools | Small office apps | Web, mobile, and business apps |

## Conclusion

**Client-server architecture** is the foundation of the Internet: clients send requests, and servers send responses, just like customers and a restaurant.

**Three-tier architecture** organizes the server side into clear parts: the **presentation tier** (dining room), the **application tier** (kitchen), and the **data tier** (storeroom). Each tier has one job and only talks to its neighbor, which makes applications more secure, scalable, and easier to maintain.

Once you understand these two architectures, you'll recognize them everywhere, from banking apps to online games.

**Good architecture puts everything in its right place: the customer in the dining room, the chef in the kitchen, and the ingredients in the storeroom.**
