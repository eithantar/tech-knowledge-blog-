# What Is Web Development? A Beginner's Guide

> Read in: **English** | [မြန်မာ](what-is-web-development-mm.md)

In the [Web Application article](../Web-Application/what-is-web-application-en.md), we learned **how a web app works**: the frontend, backend, database, and API working together, like a restaurant.

But who builds that restaurant? How do they plan it, design it, test it, open it to the public, and keep it running every day?

That is what **Web Development** is about.

## 1. What Is Web Development?

**Web Development** is the work of **building, testing, launching, and maintaining** websites and web applications.

It includes much more than writing code:

- Planning what to build
- Designing how it looks and feels
- Writing the frontend and backend code
- Setting up databases and servers
- Testing that everything works
- Putting it online (deployment)
- Fixing bugs and adding features after launch

The people who do this work are called **Web Developers**.

## 2. The Restaurant Example – Building a Restaurant

If a web application is a restaurant, then web development is the whole job of **building and running that restaurant**.

| Building a Restaurant | Web Development |
|---|---|
| Deciding the concept, menu, and budget | **Planning** – Requirements and goals |
| Architect and interior designer draw the plans | **UI/UX Design** – Layouts, colors, user flow |
| Builders set up the dining room and decoration | **Frontend Development** |
| Builders set up the kitchen, plumbing, and equipment | **Backend Development** |
| Organizing the storeroom | **Database Design** |
| Health inspector and taste testing before opening | **Testing / QA** |
| Grand opening day | **Deployment / Launch** |
| Electricity, water, and building maintenance | **DevOps / Operations** |
| Updating the menu and fixing broken chairs | **Maintenance and new features** |

Just like a restaurant, a web app is never really "finished." After opening day, you keep improving it based on what customers say.

## 3. The Main Roles in Web Development

| Role | What They Do | Restaurant Example |
|---|---|---|
| **Frontend Developer** | Builds what users see and interact with (HTML, CSS, JavaScript, React) | Builds the dining room |
| **Backend Developer** | Builds the server, API, business logic, and database (Python, Node.js, Java) | Builds the kitchen |
| **Full-Stack Developer** | Works on both frontend and backend | Can build both the dining room and the kitchen |
| **UI/UX Designer** | Designs how the app looks (UI) and how easy it is to use (UX) | Architect and interior designer |
| **QA / Test Engineer** | Finds bugs before users do | Health inspector and taste tester |
| **DevOps / Cloud Engineer** | Manages servers, deployment, monitoring, and scaling | Building manager who keeps the lights and water running |

In small teams and startups, one person often does several of these roles. In large companies, each role may be a whole team.

## 4. The Web Development Process

Most projects follow a cycle called the **Software Development Life Cycle (SDLC)**.

```
  ┌──────────┐    ┌──────────┐    ┌─────────────┐
  │ 1. Plan  │ ─► │ 2. Design│ ─► │ 3. Develop  │
  └──────────┘    └──────────┘    └─────────────┘
       ▲                                 │
       │                                 ▼
  ┌──────────────┐  ┌──────────┐  ┌──────────┐
  │ 6. Maintain  │◄─│ 5. Deploy│◄─│ 4. Test  │
  └──────────────┘  └──────────┘  └──────────┘
```

**1. Plan**

What problem are we solving? Who are the users? What features are needed first? What is the budget and deadline?

*Example:* "Players want to see a leaderboard and submit their scores."

**2. Design**

Create **wireframes** (simple sketches of each page) and **mockups** (detailed designs with colors and fonts), often in a tool like **Figma**. Also plan the database tables and API endpoints.

**3. Develop**

Write the frontend and backend code, set up the database, and connect everything through the API.

**4. Test**

Check that features work, that nothing old has broken, and that the app works on different browsers and screen sizes.

**5. Deploy**

Put the app on a server so real users can access it.

**6. Maintain**

Fix bugs, update libraries for security, monitor performance, and add new features based on user feedback. Then the cycle starts again.

Most teams today work in short cycles of 1–2 weeks called **sprints**. This approach is called **Agile**. Instead of building everything at once, they build a small piece, release it, get feedback, and improve.

## 5. Essential Tools for Web Developers

| Tool | What It's For | Examples |
|---|---|---|
| **Code Editor** | Writing code | VS Code, WebStorm |
| **Browser DevTools** | Inspecting HTML/CSS, debugging JavaScript, checking network requests | Chrome DevTools (press F12) |
| **Terminal** | Running commands, servers, and scripts | Bash, PowerShell, Zsh |
| **Version Control** | Tracking changes and working as a team | Git, GitHub, GitLab |
| **Package Manager** | Installing libraries | npm (JavaScript), pip (Python) |
| **API Testing** | Sending test requests to APIs | Postman, curl, Bruno |
| **Design** | Creating and sharing designs | Figma |
| **Containers** | Running the same environment everywhere | Docker (see the [Docker article](../Docker/docker-and-docker-compose-en.md)) |
| **AI Coding Assistants** | Explaining code, writing code, finding bugs | GitHub Copilot, Claude, ChatGPT |

**Tip:** Learn **Browser DevTools** early. Press `F12` in your browser, and you can see every HTML element, change CSS live, read JavaScript errors, and watch every request your page sends to the API.

## 6. Development Environments

Professional teams usually run their app in at least three places:

| Environment | Who Uses It | Purpose |
|---|---|---|
| **Local (Development)** | The developer, on their own computer | Writing and trying out code |
| **Staging** | The team and testers | A copy of production for final testing |
| **Production** | Real users | The live app |

Think of staging as a **practice run** before the restaurant's grand opening. You invite friends and family to eat first, so you can fix problems before real customers arrive.

**Golden rule:** Never test new code directly in production.

## 7. Working as a Team With Git

**Git** records every change to your code, so you can see who changed what, go back to an older version, and work with others without overwriting each other's work.

A typical team workflow:

```bash
# 1. Get the latest code
git checkout main
git pull

# 2. Create a new branch for your feature
git checkout -b feature/add-search-box

# 3. Write code, then save your changes
git add .
git commit -m "Add search box to leaderboard"

# 4. Upload your branch
git push -u origin feature/add-search-box
```

**5. Open a Pull Request (PR)** on GitHub. A teammate reviews your code, leaves comments, and approves it.

**6. Merge** the PR into `main`. Your feature is now part of the project.

This is like a chef trying a new recipe in a test kitchen, letting the head chef taste it, and only then adding it to the real menu.

## 8. Building a Good Website: Beyond "It Works"

A professional web app doesn't just work. It also has to be:

**1. Responsive – Works on every screen size**

More than half of web traffic comes from phones. A responsive design adjusts its layout automatically.

```css
/* 3 columns on large screens */
.cards {
  display: grid;
  grid-template-columns: repeat(3, 1fr);
  gap: 16px;
}

/* 1 column on phones */
@media (max-width: 768px) {
  .cards {
    grid-template-columns: 1fr;
  }
}
```

**2. Accessible – Usable by everyone**

People with visual, hearing, or movement disabilities also use the web. Accessibility (often written as **a11y**) means:

- Adding `alt` text to images for screen readers
- Using enough color contrast
- Making everything usable with a keyboard
- Using proper HTML elements (`<button>`, `<nav>`, `<h1>`) instead of `<div>` for everything

```html
<!-- ❌ Bad -->
<img src="trophy.png">
<div onclick="save()">Save</div>

<!-- ✅ Good -->
<img src="trophy.png" alt="Gold trophy for first place">
<button onclick="save()">Save</button>
```

**3. Fast – Performance**

Users leave if a page takes more than a few seconds to load.

- Compress and resize images
- Load only the JavaScript you need
- Use caching and a CDN
- Test with **Lighthouse** in Chrome DevTools

**4. Findable – SEO (Search Engine Optimization)**

Help Google understand and rank your pages.

- Use a clear `<title>` and `<meta name="description">` on every page
- Use headings (`<h1>`, `<h2>`) in a logical order
- Use readable URLs, like `/blog/what-is-docker` instead of `/page?id=123`

**5. Secure**

Use HTTPS, validate input, hash passwords, and protect against SQL injection and XSS (see the security section in the [Web Application article](../Web-Application/what-is-web-application-en.md)).

## 9. Testing

Testing means writing code that **checks your code**. When you change something later, the tests tell you immediately if you broke anything.

| Test Type | What It Checks | Restaurant Example |
|---|---|---|
| **Unit Test** | One small function | Is the sauce salty enough? |
| **Integration Test** | Several parts working together (e.g., API + database) | Does the dish taste right when the sauce and noodles are combined? |
| **End-to-End (E2E) Test** | The whole app, like a real user clicking in a browser | A mystery customer orders, eats, and pays |

**Example: Testing the leaderboard API** from the Web Application article with **pytest**:

**test_main.py**

```python
from fastapi.testclient import TestClient

from main import app

client = TestClient(app)


def test_add_score():
    response = client.post("/api/scores", json={"player": "Tester", "score": 100})
    assert response.status_code == 201
    assert response.json()["player"] == "Tester"


def test_scores_are_sorted_highest_first():
    client.post("/api/scores", json={"player": "Low", "score": 1})
    client.post("/api/scores", json={"player": "High", "score": 9999})

    scores = [s["score"] for s in client.get("/api/scores").json()]
    assert scores == sorted(scores, reverse=True)


def test_invalid_score_is_rejected():
    response = client.post("/api/scores", json={"player": "Cheater", "score": "lots"})
    assert response.status_code == 422
```

```bash
pip install pytest httpx
pytest
```

Popular testing tools:

- **Python:** pytest
- **JavaScript:** Jest, Vitest
- **End-to-end (browser):** Playwright, Cypress

## 10. CI/CD – Automatic Testing and Deployment

**CI/CD** stands for **Continuous Integration / Continuous Deployment**.

- **Continuous Integration (CI)** – Every time someone pushes code, tests run **automatically**.
- **Continuous Deployment (CD)** – If the tests pass, the new version is **automatically** deployed.

Instead of a person remembering to run tests and upload files, a robot does it every time.

**Example: GitHub Actions** – Save this file as `.github/workflows/tests.yml` in your project:

```yaml
name: Tests

on: [push, pull_request]

jobs:
  test:
    runs-on: ubuntu-latest
    steps:
      - uses: actions/checkout@v4

      - uses: actions/setup-python@v5
        with:
          python-version: "3.12"

      - name: Install dependencies
        run: pip install fastapi uvicorn pytest httpx

      - name: Run tests
        run: pytest
```

Now every push and every Pull Request shows a ✅ or ❌ on GitHub. Teams usually don't allow merging a Pull Request until the tests pass.

## 11. Popular Tech Stacks

A **tech stack** is the set of technologies used together to build an app.

| Stack | Frontend | Backend | Database | Good For |
|---|---|---|---|---|
| **MERN** | React | Node.js + Express | MongoDB | Full JavaScript apps |
| **Python Stack** | React or HTML templates | Django or FastAPI | PostgreSQL | Data-heavy apps, AI integration |
| **LAMP** | HTML/PHP | PHP (Laravel) | MySQL | Classic websites, WordPress |
| **Next.js Stack** | Next.js (React) | Next.js API routes | PostgreSQL | Modern full-stack apps with great SEO |
| **Java Enterprise** | Angular or React | Spring Boot | PostgreSQL / Oracle | Banks and large companies |

**There is no "best" stack.** Pick one, learn it well, and build real projects. Once you understand the concepts, switching to another stack is much easier.

## 12. AI in Web Development

AI tools are now part of everyday web development:

- **Writing code** – Generating components, API endpoints, and tests
- **Explaining code** – Understanding unfamiliar code quickly
- **Debugging** – Finding the cause of errors
- **Learning** – Asking questions as you study

But AI can be wrong (see "hallucination" in the [Prompt Engineering article](../Artificial-Intelligence/prompt-engineering-en.md)). Always:

- **Read and understand** the code before using it
- **Test** it
- **Check security**, especially for authentication and database code

AI makes good developers faster. It doesn't replace understanding the fundamentals.

## 13. Learning Roadmap

**Stage 1 – Foundations (1–3 months)**

- HTML, CSS, and basic JavaScript
- Git and GitHub
- *Projects:* A personal profile page, a responsive landing page

**Stage 2 – Interactive Frontend (2–3 months)**

- JavaScript in depth (DOM, `fetch`, async/await)
- Calling public APIs
- A frontend framework (React or Vue)
- *Projects:* A weather app using a public API, a to-do list app

**Stage 3 – Backend and Databases (2–4 months)**

- One backend language and framework (e.g., Python + FastAPI, or Node.js + Express)
- SQL and a database (PostgreSQL)
- Building REST APIs, user login
- *Projects:* A blog with login, the game leaderboard from the [Web Application article](../Web-Application/what-is-web-application-en.md)

**Stage 4 – Professional Skills (ongoing)**

- Testing and CI/CD
- Docker and deployment to the cloud
- Security, performance, accessibility
- Real-time features with [WebSocket](../WebSocket/what-is-websocket-en.md)
- *Projects:* A real-time chat app, a full project deployed online with its own domain

These timelines are only a guide. Everyone learns at a different speed, and consistency matters more than speed.

## 14. Tips for Beginners

- **Build, don't just watch.** Tutorials are a start, but you learn most by building your own projects and getting stuck.
- **Make a portfolio.** Put your projects on GitHub and deploy them online, so others can try them.
- **Read error messages.** They usually tell you exactly what's wrong and where.
- **Learn to search.** Developers search documentation, Stack Overflow, and GitHub issues every day.
- **Read official documentation.** MDN Web Docs is the best reference for HTML, CSS, and JavaScript.
- **Write about what you learn.** Like this blog! Explaining something is the best way to truly understand it.
- **Be patient.** Every senior developer was once confused by their first bug.

## Conclusion

Web development is the full journey of creating a web application: planning, designing, building the frontend and backend, testing, deploying, and maintaining it, just like building and running a restaurant.

It's a field with many roles, tools, and technologies, but you don't need to learn everything at once. Start with HTML, CSS, and JavaScript, build small projects, use Git, and add new skills one step at a time.

**The best way to learn web development is to build something, break it, fix it, and build again.**
