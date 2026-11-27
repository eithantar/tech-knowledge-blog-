# What Is a Web Application and How Does It Work?

> Read in: **English** | [မြန်မာ](what-is-web-application-mm.md)

Think about the apps you use in your browser every day: Gmail, Facebook, YouTube, online banking, Google Docs, or an online shopping site.

You don't install any of them. You just open a browser, type an address, and start using them. They remember your account, show your own data, and update when you click a button.

These are all **Web Applications**.

## 1. What Is a Web Application?

A **Web Application (Web App)** is a software program that runs on a **server** and that you use through a **web browser**, over the Internet.

- **No installation** – Open a browser and go to the URL.
- **Works everywhere** – Windows, Mac, Linux, phones, and tablets all have a browser.
- **Always up to date** – The developer updates the server, and every user gets the new version immediately.
- **Your data is saved on the server** – Log in from any device and your data is there.

## 2. Website vs Web Application

People often use these words as if they mean the same thing, but there is a difference.

| | Website | Web Application |
|---|---|---|
| Main purpose | Show information | Let users **do** things |
| Interaction | Mostly reading | Logging in, creating, editing, buying |
| Content | Same for everyone | Different for each user |
| Example | A company's "About Us" page, a blog | Gmail, online banking, Facebook |

A simple way to remember: **a website is like a restaurant's menu board, and a web application is the whole restaurant where you can actually order food.**

In reality, it's a spectrum. Many sites are a bit of both. For example, a blog becomes a web app once you add login and comments.

## 3. The Restaurant Example

In the [API article](../API/what-is-api-en.md), we compared an API to a restaurant waiter. Now let's look at the **whole restaurant**, because a web application has the same parts.

| Restaurant | Web Application | What It Does |
|---|---|---|
| Dining room, tables, menu, decoration | **Frontend** | What the user sees and clicks |
| Waiter | **API** | Carries requests and responses between frontend and backend |
| Kitchen and chefs | **Backend** | Processes requests and applies business rules |
| Storeroom / pantry | **Database** | Stores data permanently |
| The building | **Server / Hosting** | The computer where the app runs |
| The street address | **Domain name** (e.g., `myshop.com`) | How people find the app |
| The address book | **DNS** | Turns the domain name into the server's IP address |

The customer only sees the dining room (frontend). But without the kitchen (backend) and the storeroom (database), no food could be served.

## 4. Web Application Architecture

Most web applications follow the same basic structure:

```
┌──────────────┐        ┌──────────────┐        ┌──────────────┐
│   Browser    │  HTTP  │   Backend    │  SQL   │   Database   │
│  (Frontend)  │ ─────► │   (Server)   │ ─────► │              │
│ HTML/CSS/JS  │ ◄───── │ Python, Node │ ◄───── │  PostgreSQL  │
└──────────────┘  JSON  └──────────────┘  Data  └──────────────┘
     Client                                         
```

This is often called a **three-tier architecture**:

1. **Presentation tier** – The frontend in the browser.
2. **Application tier** – The backend with the business logic.
3. **Data tier** – The database.

## 5. What Happens When You Open a Web App?

Let's follow what happens when you type `https://myshop.com` and press Enter.

**Step 1 – Find the server (DNS)**

The browser asks DNS, "What is the IP address of `myshop.com`?" DNS replies with something like `203.0.113.10`. It's like looking up a restaurant's address before going there.

**Step 2 – Connect securely (HTTPS)**

The browser connects to the server and sets up encryption, so no one can read the data on the way.

**Step 3 – Send a request (HTTP)**

The browser sends `GET /` to ask for the home page.

**Step 4 – The backend does its work**

The backend checks who you are, gets your data from the database (for example, your shopping cart), and prepares the response.

**Step 5 – Send a response**

The server sends back HTML, CSS, JavaScript, and data (often JSON).

**Step 6 – The browser shows the page**

The browser draws the page on screen. When you click a button, JavaScript sends new requests to the backend's API, and the cycle continues.

All of this usually happens in **less than a second**.

## 6. The Frontend – What Users See

The frontend runs **inside the browser**. It's built with three core technologies:

| Technology | Role | Restaurant Example |
|---|---|---|
| **HTML** | Structure and content | Tables, chairs, and the menu |
| **CSS** | Design and layout | Paint colors, lighting, decoration |
| **JavaScript** | Behavior and interaction | The waiter responding when you call |

```html
<!-- HTML: structure -->
<button id="like">❤️ Like</button>
<span id="count">0</span>

<!-- CSS: design -->
<style>
  #like { background: hotpink; color: white; border: none; padding: 8px 16px; }
</style>

<!-- JavaScript: behavior -->
<script>
  let likes = 0;
  document.getElementById("like").addEventListener("click", () => {
    likes++;
    document.getElementById("count").textContent = likes;
  });
</script>
```

For bigger apps, developers use **frontend frameworks** that make building complex user interfaces easier:

- **React** (by Meta) – The most popular.
- **Vue** – Easy to learn.
- **Angular** (by Google) – Popular in large companies.
- **Svelte** – Lightweight and fast.

## 7. The Backend – The Kitchen

The backend runs **on the server**. Users never see it directly. Its jobs include:

- **Business logic** – "Is this item in stock?", "Apply a 10% discount for members."
- **Authentication** – Checking usernames and passwords, and managing logins.
- **Talking to the database** – Saving and reading data.
- **Providing an API** – Sending data to the frontend.
- **Talking to other services** – Payments, email, AI models, and more.

Popular backend languages and frameworks:

| Language | Frameworks |
|---|---|
| **Python** | Django, FastAPI, Flask |
| **JavaScript / TypeScript** | Node.js with Express, NestJS, Next.js |
| **Java** | Spring Boot |
| **PHP** | Laravel |
| **Go** | Gin, Echo |
| **C#** | ASP.NET Core |

## 8. The Database – The Storeroom

The database stores data permanently: user accounts, products, orders, messages, and scores.

**SQL (Relational) Databases** store data in **tables** with rows and columns, like a spreadsheet.

- Examples: **PostgreSQL, MySQL, SQLite**
- Good for: data with clear relationships, such as users, orders, and payments.

| id | player | score |
|---|---|---|
| 1 | Aung | 1500 |
| 2 | Su | 1200 |

**NoSQL Databases** store data in more flexible formats, such as JSON-like documents or key-value pairs.

- Examples: **MongoDB** (documents), **Redis** (key-value, very fast, often used for caching)
- Good for: flexible or rapidly changing data, real-time features, and very large scale.

## 9. Types of Web Applications

**1. Multi-Page Application (MPA)**

Every click loads a **new page** from the server. This is the traditional approach.

- Examples: Many news sites, government websites, traditional e-commerce sites.
- Good for: content-heavy sites and SEO (being found on Google).

**2. Single-Page Application (SPA)**

The browser loads **one page** once. After that, JavaScript updates only the parts that change, using data from the API.

- Examples: Gmail, Google Maps, Trello.
- Good for: smooth, app-like experiences.

**3. Progressive Web App (PWA)**

A web app that can be **installed** on your phone's home screen, work **offline**, and send **notifications**, like a mobile app.

- Examples: Twitter/X Lite, Starbucks PWA.
- Good for: mobile users with slow or unstable Internet.

Modern frameworks like **Next.js** and **Nuxt** mix these approaches. For example, they can render the first page on the server for speed and SEO, and then behave like an SPA.

## 10. Example: Build a Small Web Application

Let's build a complete mini web app: a **game leaderboard**. It has all three parts:

- **Frontend** – An HTML page where players add scores and see the top 10.
- **Backend** – A FastAPI server with an API.
- **Database** – SQLite (a small database stored in one file, built into Python).

**Project structure**

```
leaderboard/
├── main.py       # Backend + database
└── index.html    # Frontend
```

**main.py** (the kitchen and the storeroom)

```python
import sqlite3

from fastapi import FastAPI
from fastapi.responses import FileResponse
from pydantic import BaseModel

app = FastAPI()
DB_FILE = "leaderboard.db"


def get_db():
    conn = sqlite3.connect(DB_FILE)
    conn.row_factory = sqlite3.Row
    return conn


# Create the table when the app starts
with get_db() as conn:
    conn.execute("CREATE TABLE IF NOT EXISTS scores (player TEXT, score INTEGER)")


class Score(BaseModel):
    player: str
    score: int


# Frontend: send the HTML page to the browser
@app.get("/")
def home():
    return FileResponse("index.html")


# API: get the top 10 scores
@app.get("/api/scores")
def list_scores():
    with get_db() as conn:
        rows = conn.execute(
            "SELECT player, score FROM scores ORDER BY score DESC LIMIT 10"
        ).fetchall()
    return [dict(row) for row in rows]


# API: add a new score
@app.post("/api/scores", status_code=201)
def add_score(score: Score):
    with get_db() as conn:
        conn.execute(
            "INSERT INTO scores (player, score) VALUES (?, ?)",
            (score.player, score.score),
        )
    return score
```

**index.html** (the dining room)

```html
<!doctype html>
<html>
<head>
  <meta charset="utf-8">
  <title>Game Leaderboard</title>
  <style>
    body { font-family: sans-serif; max-width: 480px; margin: 40px auto; }
    li { padding: 4px 0; }
  </style>
</head>
<body>
  <h1>🏆 Game Leaderboard</h1>

  <form id="score-form">
    <input id="player" placeholder="Player name" required>
    <input id="score" type="number" placeholder="Score" required>
    <button>Add Score</button>
  </form>

  <ol id="board"></ol>

  <script>
    const board = document.getElementById("board");
    const form = document.getElementById("score-form");
    const playerInput = document.getElementById("player");
    const scoreInput = document.getElementById("score");

    // Ask the backend for the top scores and show them
    async function loadScores() {
      const response = await fetch("/api/scores");
      const scores = await response.json();

      board.innerHTML = "";
      for (const s of scores) {
        const li = document.createElement("li");
        li.textContent = `${s.player} — ${s.score}`;
        board.appendChild(li);
      }
    }

    // Send a new score to the backend
    form.addEventListener("submit", async (event) => {
      event.preventDefault();
      await fetch("/api/scores", {
        method: "POST",
        headers: { "Content-Type": "application/json" },
        body: JSON.stringify({
          player: playerInput.value,
          score: Number(scoreInput.value),
        }),
      });
      form.reset();
      loadScores();
    });

    loadScores();
  </script>
</body>
</html>
```

**Run it**

```bash
cd leaderboard
pip install fastapi uvicorn
uvicorn main:app --reload
```

Open `http://127.0.0.1:8000` in your browser, add a few scores, and watch the leaderboard update. Stop the server and start it again: the scores are still there, because they are saved in the database.

**What just happened?**

1. The browser asked for `/`, and the backend sent `index.html` (the **frontend**).
2. JavaScript called `GET /api/scores` (the **API**).
3. The backend read the top scores from SQLite (the **database**) and returned JSON.
4. When you submitted the form, JavaScript sent `POST /api/scores`, and the backend saved the new score.

That is the complete life cycle of a web application.

## 11. Deploying a Web Application

To let other people use your app, you need to put it on a server that is always on and connected to the Internet. This is called **deployment**.

Common options:

- **Platform as a Service (PaaS)** – Upload your code and the platform runs it for you. Examples: Render, Railway, Heroku, AWS Elastic Beanstalk.
- **Virtual servers** – Rent a server and set everything up yourself. Examples: AWS EC2, DigitalOcean.
- **Frontend hosting** – For static frontends and frameworks like Next.js. Examples: Vercel, Netlify, AWS Amplify.
- **Containers** – Package the app with Docker and run it anywhere (see the [Docker article](../Docker/docker-and-docker-compose-en.md)).

You'll also need:

- A **domain name** (e.g., `myleaderboard.com`)
- An **HTTPS certificate** (free with Let's Encrypt, and included automatically by most platforms)
- A **production database** (e.g., PostgreSQL instead of SQLite)

## 12. Web Application Security

Web apps are open to the whole Internet, so security is essential. Here are the most common dangers and how to prevent them:

| Danger | What Happens | Prevention |
|---|---|---|
| **SQL Injection** | An attacker types SQL code into a form to read or delete your database | Always use parameterized queries (`?` placeholders), like in our example |
| **XSS (Cross-Site Scripting)** | An attacker puts JavaScript into content, which then runs in other users' browsers | Use `textContent` instead of `innerHTML` for user data, like in our example; escape output |
| **Weak passwords / stolen passwords** | Accounts get taken over | Hash passwords (bcrypt, Argon2); never store plain text; support 2FA |
| **CSRF** | A malicious site tricks your browser into sending requests to another site | Use CSRF tokens and `SameSite` cookies |
| **Data sent without encryption** | Someone on the network reads passwords and data | Always use HTTPS |

The **OWASP Top 10** is a well-known list of the most important web security risks. It's worth reading once you start building real apps.

## 13. Making a Web App Fast and Scalable

As more people use your app, you can:

- **Cache** frequently used data (e.g., with Redis) so you don't hit the database every time.
- Use a **CDN** (Content Delivery Network) to serve images, CSS, and JavaScript from servers close to users.
- Add **more backend servers** behind a **load balancer** (see the scaling section in the [Docker article](../Docker/docker-and-docker-compose-en.md)).
- Use **WebSocket** for real-time features (see the [WebSocket article](../WebSocket/what-is-websocket-en.md)).
- **Optimize the database** with indexes and efficient queries.

## 14. How to Start Learning Web Development

A common learning path:

1. **HTML and CSS** – Build simple static pages.
2. **JavaScript** – Make pages interactive.
3. **Git and GitHub** – Save and share your code.
4. **A backend language and framework** – For example, Python with FastAPI or Django, or JavaScript with Node.js.
5. **Databases and SQL** – Start with SQLite or PostgreSQL.
6. **APIs** – Connect frontend and backend (see the [API article](../API/what-is-api-en.md)).
7. **A frontend framework** – For example, React or Vue.
8. **Deployment** – Put your app online, then learn Docker and the cloud.

The best way to learn is to **build small projects**: a to-do list, a blog, a leaderboard, or a chat app.

## Conclusion

A web application is like a complete restaurant. The **frontend** is the dining room that users see, the **backend** is the kitchen that does the work, the **database** is the storeroom that keeps everything, and the **API** is the waiter that connects them.

Once you understand how these parts work together, you can understand almost any web app you use, from Gmail to online banking, and start building your own.

**Every great web app starts with a simple idea, a browser, and a server.**
