# What Is an API and How Does It Work?

> Read in: **English** | [မြန်မာ](what-is-api-mm.md)

Every day, we use apps that talk to other systems without us noticing.

A weather app shows today's forecast. A shopping website lets you pay with your bank card. A game lets you log in with your Google account. A map appears inside a food delivery app.

None of these apps built everything by themselves. They "borrow" data and features from other systems.

The technology that makes this possible is called an **API**.

## 1. What Is an API?

**API** stands for **Application Programming Interface**.

In simple terms, an API is a set of rules that lets one software application **request data or services** from another application, and get a response back.

The easiest way to understand an API is to think about a **restaurant**.

- **You (the customer)** want food, but you can't go into the kitchen yourself.
- **The kitchen** has the food and knows how to cook it.
- **The waiter** takes your order to the kitchen and brings the food back to you.
- **The menu** tells you what you can order.

| Restaurant | API World |
|---|---|
| Customer | **Client** (your app, website or program) |
| Kitchen | **Server** (the system that has the data) |
| Waiter | **API** |
| Menu | **API Documentation** |
| Your order | **Request** |
| The food you receive | **Response** |

You don't need to know how the kitchen cooks the food. You only need to know how to order from the menu. In the same way, you don't need to know how another system works inside. You only need to know how to use its API.

## 2. Where Do We Use APIs Every Day?

- **Weather apps** – Get forecast data from a weather service API.
- **"Login with Google"** – Uses Google's API to check who you are.
- **Online payments** – Shopping websites use payment APIs (such as Stripe or PayPal) to process cards.
- **Maps** – Delivery and taxi apps show maps using a map API.
- **AI chatbots** – Apps send your question to an AI model's API and show the answer.
- **Currency exchange rates** – Finance apps get the latest rates from an exchange rate API.

## 3. How Does an API Work?

An API conversation always has two parts: a **Request** and a **Response**.

**Step 1 – The client sends a request**

The request contains:

- **Endpoint (URL)** – Where to send the request. For example: `https://api.example.com/users/1`
- **Method** – What you want to do (get, create, update, or delete data).
- **Headers** – Extra information, such as the data format or an API key.
- **Body** – The data you send (only for some methods, such as creating new data).

**Step 2 – The server processes the request**

The server checks the request, finds or changes the data, and prepares an answer.

**Step 3 – The server sends a response**

The response contains:

- **Status Code** – A number that shows whether the request succeeded or failed.
- **Body** – The data you asked for, usually in **JSON** format.

## 4. HTTP Methods – What Do You Want to Do?

Most web APIs use HTTP methods. Each method matches an action, like ordering different things at the restaurant.

| Method | Action | Restaurant Example | API Example |
|---|---|---|---|
| **GET** | Read data | "Can I see the menu?" | Get a list of users |
| **POST** | Create new data | "I'd like to order a new dish." | Create a new user |
| **PUT** | Replace existing data | "Please change my whole order." | Update all of a user's information |
| **PATCH** | Update part of the data | "Less spicy, please." | Change only a user's email |
| **DELETE** | Remove data | "Please cancel my order." | Delete a user |

These four actions — Create, Read, Update, Delete — are often called **CRUD**.

## 5. Status Codes – Did It Work?

The server always replies with a status code. You can tell what happened from the first digit.

| Code | Meaning | Restaurant Example |
|---|---|---|
| **200 OK** | Success | Your food arrived. |
| **201 Created** | New data was created | Your new order was accepted. |
| **400 Bad Request** | The request is wrong | You ordered something that doesn't make sense. |
| **401 Unauthorized** | You are not logged in or have no valid key | You must show your membership card first. |
| **403 Forbidden** | You don't have permission | This is the VIP room. You can't enter. |
| **404 Not Found** | The data doesn't exist | That dish isn't on the menu. |
| **429 Too Many Requests** | You sent too many requests | Please slow down. The kitchen is too busy. |
| **500 Internal Server Error** | Something broke on the server | There's a problem in the kitchen. |

An easy way to remember:

- **2xx** – Success
- **4xx** – The client made a mistake
- **5xx** – The server made a mistake

## 6. What Is JSON?

Most modern APIs send and receive data in **JSON** (JavaScript Object Notation). It's easy for both humans and computers to read.

```json
{
  "id": 1,
  "name": "Aung Aung",
  "email": "aung@example.com",
  "skills": ["Python", "Docker", "AWS"],
  "is_active": true
}
```

- Data is written as **key: value** pairs.
- `[ ]` holds a list.
- `{ }` holds an object.

## 7. Types of APIs

**By design style:**

- **REST API** – The most common style. Uses URLs and HTTP methods (GET, POST, etc.) and usually JSON.
- **GraphQL** – The client asks for exactly the fields it needs in one request, no more and no less.
- **WebSocket** – Keeps a connection open so the server can send data instantly. Used for chat apps, live games, and live prices.
- **SOAP** – An older style that uses XML. Still found in banks and large enterprise systems.

**By who can use them:**

- **Public API** – Anyone can use it, sometimes with a free API key (e.g., weather APIs).
- **Private API** – Used only inside a company, between its own systems.
- **Partner API** – Shared only with specific business partners.

## 8. Calling an API (Practical Example)

Let's call a free test API called **JSONPlaceholder**.

**Using curl (terminal)**

```bash
# GET – read a post
curl https://jsonplaceholder.typicode.com/posts/1

# POST – create a new post
curl -X POST https://jsonplaceholder.typicode.com/posts \
  -H "Content-Type: application/json" \
  -d '{"title": "Hello API", "body": "My first request", "userId": 1}'
```

**Using Python**

```python
import requests

# GET – read data
response = requests.get("https://jsonplaceholder.typicode.com/posts/1", timeout=10)
print(response.status_code)      # 200
print(response.json()["title"])

# POST – send new data
new_post = {"title": "Hello API", "body": "My first request", "userId": 1}
response = requests.post("https://jsonplaceholder.typicode.com/posts", json=new_post, timeout=10)
print(response.status_code)      # 201
print(response.json())
```

Install the library with:

```bash
pip install requests
```

## 9. Building Your Own API (Practical Example)

Now let's be the "kitchen." We'll build a small **game score API** with **FastAPI**, a popular Python framework.

**main.py**

```python
from fastapi import FastAPI, HTTPException
from pydantic import BaseModel

app = FastAPI()

class Score(BaseModel):
    player: str
    score: int

scores: list[Score] = []

# GET – show the leaderboard
@app.get("/scores")
def get_scores():
    return sorted(scores, key=lambda s: s.score, reverse=True)

# POST – add a new score
@app.post("/scores", status_code=201)
def add_score(score: Score):
    scores.append(score)
    return score

# GET – find one player's score
@app.get("/scores/{player}")
def get_player_score(player: str):
    for s in scores:
        if s.player == player:
            return s
    raise HTTPException(status_code=404, detail="Player not found")
```

**Run it**

```bash
pip install fastapi uvicorn
uvicorn main:app --reload
```

**Try it**

```bash
# Add a score
curl -X POST http://127.0.0.1:8000/scores \
  -H "Content-Type: application/json" \
  -d '{"player": "Aung", "score": 1200}'

# Show the leaderboard
curl http://127.0.0.1:8000/scores

# Find a player who doesn't exist → 404
curl http://127.0.0.1:8000/scores/Nobody
```

FastAPI also creates **interactive documentation** (the "menu") automatically. Open `http://127.0.0.1:8000/docs` in your browser to see and test every endpoint.

> This API stores scores in memory, so they disappear when the server stops. In a real project, you would save them in a database such as PostgreSQL, and you could package everything with Docker (see the [Docker article](../Docker/docker-and-docker-compose-en.md)).

## 10. API Security – Who Is Allowed In?

Not everyone should be able to use every API. Common ways to control access:

- **API Key** – A secret string that identifies your app. Like a membership card for the restaurant.
- **Bearer Token / OAuth** – A temporary token you get after logging in. Used for "Login with Google" and similar features.
- **HTTPS** – Encrypts the data so no one can read it on the way.
- **Rate Limiting** – Limits how many requests a client can send per minute, to protect the server from overload.

Example of sending an API key safely:

```python
import os
import requests

api_key = os.environ["WEATHER_API_KEY"]  # Read from an environment variable, not hard-coded

response = requests.get(
    "https://api.example.com/weather?city=Yangon",
    headers={"Authorization": f"Bearer {api_key}"},
    timeout=10,
)
```

**Never** put API keys directly in your code or push them to GitHub. Use environment variables or a `.env` file that is listed in `.gitignore`.

## 11. API vs Web Scraping

| | API | Web Scraping |
|---|---|---|
| How it gets data | Asks the server through an official "door" | Reads the website's HTML |
| Data format | Structured (JSON) | Must be extracted from HTML |
| Stability | Stable; changes are usually announced | Breaks when the website design changes |
| Permission | Officially allowed by the provider | Depends on the website's terms |

If an official API is available, it is usually better to use it than to scrape. (See the [Web Scraping article](../Web-Scraping/what-is-web-scraping-en.md).)

## 12. Best Practices

**When using an API:**

- Read the API documentation first.
- Keep API keys secret.
- Always check the status code before using the response.
- Set a timeout so your app doesn't wait forever.
- Respect rate limits.

**When building an API:**

- Use clear, noun-based URLs (`/users`, `/scores`), and let the HTTP method describe the action.
- Return the correct status codes.
- Version your API (e.g., `/v1/scores`) so you can change it without breaking existing apps.
- Validate all input data.
- Write good documentation (FastAPI and OpenAPI/Swagger help with this).

## Conclusion

An API is like a waiter in a restaurant. It takes your request to the system that has the data, and brings the response back — without you needing to know how the kitchen works.

APIs connect almost everything in today's digital world: weather apps, payments, maps, logins, and AI chatbots. Once you understand requests, responses, HTTP methods, status codes, and JSON, you can both use other people's APIs and build your own.

**APIs are the bridges that let software talk to each other.**
