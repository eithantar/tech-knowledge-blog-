# What Is WebSocket and How Does It Work?

> Read in: **English** | [မြန်မာ](what-is-websocket-mm.md)

In the [API article](../API/what-is-api-en.md), we learned that the client sends a **request**, the server sends back a **response**, and then the conversation ends.

This works well for most things: loading a web page, getting the weather, saving a game score.

But some apps need data to arrive **the moment it changes**:

- A new chat message appears instantly.
- In an online game, you see other players move in real time.
- Football scores and stock prices update live.
- A notification pops up as soon as someone likes your post.

With normal HTTP, the server can't send anything unless the client asks first. So how do these apps work?

The answer is **WebSocket**.

## 1. What Is WebSocket?

**WebSocket** is a communication protocol that keeps **one connection open** between the client and the server, so **both sides can send messages to each other at any time**.

The easiest way to understand it is to compare **letters** with a **phone call**.

- **HTTP is like sending letters.** You write a letter (request), wait for a reply (response), and the exchange ends. If you want to know something new, you have to write another letter.
- **WebSocket is like a phone call.** You call once, and the line stays open. Both people can talk whenever they want, until someone hangs up.

Let's also go back to the restaurant from the API article:

- **With HTTP**, you keep asking the waiter, "Is my food ready? … Is it ready now? … How about now?" Most of the time the answer is "Not yet."
- **With WebSocket**, the restaurant gives you a **buzzer**. You sit down and relax, and the buzzer rings **the moment** your food is ready.

## 2. HTTP vs WebSocket

| | HTTP | WebSocket |
|---|---|---|
| Connection | Opens and closes for each request | Stays open |
| Who can start talking | Only the client | Both client and server |
| Direction | One way at a time (request → response) | Two-way at the same time (full-duplex) |
| Real-time updates | Client must keep asking | Server pushes instantly |
| Overhead | Headers sent with every request | Small message frames after connecting |
| URL | `http://` / `https://` | `ws://` / `wss://` |
| Best for | Loading pages, REST APIs, forms | Chat, games, live data, notifications |

## 3. How Did We Do This Before WebSocket?

**1. Polling – "Are we there yet?"**

The client sends a request every few seconds to check for new data.

```
Client: Any new messages?   Server: No.
Client: Any new messages?   Server: No.
Client: Any new messages?   Server: No.
Client: Any new messages?   Server: Yes! Here's 1.
```

This is simple, but wastes a lot of requests, and updates can be delayed by up to the polling interval.

**2. Long Polling – "Tell me when there's something."**

The client sends a request, and the server holds it open until there is new data. Then the client immediately sends another request. It's better than polling, but still opens a new request after every message.

**3. Server-Sent Events (SSE) – A one-way radio**

The server can keep sending updates to the client over one connection, but the client cannot reply on the same connection. It's great for live news feeds or streaming AI responses, but not for two-way chat or games.

**4. WebSocket – A phone call**

One connection, two-way, real time.

## 4. How Does WebSocket Work?

A WebSocket connection has three stages.

**Step 1 – The Handshake (Dialing the Phone)**

The connection starts as a normal HTTP request, asking the server to "upgrade" to WebSocket.

```http
GET /ws/chat HTTP/1.1
Host: game.example.com
Upgrade: websocket
Connection: Upgrade
Sec-WebSocket-Key: dGhlIHNhbXBsZSBub25jZQ==
Sec-WebSocket-Version: 13
```

If the server agrees, it replies with status code **101 Switching Protocols**:

```http
HTTP/1.1 101 Switching Protocols
Upgrade: websocket
Connection: Upgrade
Sec-WebSocket-Accept: s3pPLMBiTxaQ9kYGzzhZRbK+xOo=
```

The phone has been answered. From now on, the connection is no longer HTTP. It's WebSocket.

**Step 2 – Sending Messages (Talking)**

Both sides can now send messages at any time. Messages are sent as small **frames**, which can contain:

- **Text** (usually JSON)
- **Binary data** (images, audio, game data)

There are also special **ping/pong** frames to check that the other side is still there ("Hello? Are you still on the line?").

**Step 3 – Closing (Hanging Up)**

Either side can send a **close** frame to end the connection politely. If the network drops, the connection also closes, and the app should try to reconnect.

## 5. Where Is WebSocket Used?

- **Chat apps** – Messages appear instantly for everyone in the chat.
- **Multiplayer online games** – Player positions, actions, and scores update in real time.
- **Live sports scores and stock prices** – Numbers update the moment they change.
- **Notifications** – "Someone commented on your post" appears without refreshing.
- **Collaborative editing** – Several people edit the same document and see each other's changes live.
- **Live dashboards** – Server monitoring, delivery tracking, and IoT sensor data.

## 6. Example: A Live Game Chat Server

Let's build a game lobby chat. When a player sends a message, **every connected player** receives it instantly. We'll use **FastAPI** again.

**main.py**

```python
from fastapi import FastAPI, WebSocket, WebSocketDisconnect

app = FastAPI()


class ConnectionManager:
    """Keeps track of every player who is connected."""

    def __init__(self):
        self.active: list[WebSocket] = []

    async def connect(self, websocket: WebSocket):
        await websocket.accept()  # Answer the phone
        self.active.append(websocket)

    def disconnect(self, websocket: WebSocket):
        self.active.remove(websocket)

    async def broadcast(self, message: str):
        for connection in self.active:
            await connection.send_text(message)


manager = ConnectionManager()


@app.websocket("/ws/{player}")
async def game_chat(websocket: WebSocket, player: str):
    await manager.connect(websocket)
    await manager.broadcast(f"🎮 {player} joined the game")
    try:
        while True:
            message = await websocket.receive_text()  # Wait for a message
            await manager.broadcast(f"{player}: {message}")
    except WebSocketDisconnect:
        manager.disconnect(websocket)
        await manager.broadcast(f"👋 {player} left the game")
```

**Run it**

```bash
pip install fastapi "uvicorn[standard]"
uvicorn main:app --reload
```

`uvicorn[standard]` includes the WebSocket support that the server needs.

## 7. Connecting From the Browser (JavaScript)

Every modern browser has WebSocket built in.

**index.html**

```html
<!doctype html>
<html>
<body>
  <h2>Game Lobby Chat</h2>
  <input id="message" placeholder="Type a message">
  <button onclick="sendMessage()">Send</button>
  <ul id="chat"></ul>

  <script>
    const player = prompt("Your name?") || "Guest";
    const ws = new WebSocket(`ws://127.0.0.1:8000/ws/${player}`);

    ws.onopen = () => console.log("Connected");

    ws.onmessage = (event) => {
      const li = document.createElement("li");
      li.textContent = event.data;
      document.getElementById("chat").appendChild(li);
    };

    ws.onclose = () => console.log("Disconnected");

    function sendMessage() {
      const input = document.getElementById("message");
      ws.send(input.value);
      input.value = "";
    }
  </script>
</body>
</html>
```

Open this file in **two browser windows**, enter different names, and send a message. It appears in both windows instantly, without refreshing the page.

The four events to remember:

| Event | When It Happens |
|---|---|
| `onopen` | The connection is ready |
| `onmessage` | A message arrives from the server |
| `onclose` | The connection is closed |
| `onerror` | Something went wrong |

## 8. Connecting From Python

You can also connect from a Python program, for example a bot that joins the game chat.

```python
import asyncio
import websockets


async def main():
    async with websockets.connect("ws://127.0.0.1:8000/ws/Bot") as ws:
        await ws.send("Hello everyone! I'm a bot 🤖")
        async for message in ws:  # Keep listening for new messages
            print(message)


asyncio.run(main())
```

```bash
pip install websockets
```

## 9. Sending Structured Messages (JSON)

In real apps, messages usually have a **type** so the client knows what to do with them.

```json
{ "type": "chat", "player": "Aung", "text": "Good game!" }
```

```json
{ "type": "move", "player": "Su", "x": 120, "y": 45 }
```

```json
{ "type": "score", "player": "Aung", "score": 1500 }
```

On the client:

```javascript
ws.onmessage = (event) => {
  const data = JSON.parse(event.data);

  if (data.type === "chat") showChatMessage(data);
  if (data.type === "move") movePlayer(data);
  if (data.type === "score") updateLeaderboard(data);
};
```

## 10. Scaling WebSocket

WebSocket connections are **long-lived**. Each connected player keeps a connection open to one specific server. This creates two challenges when you scale.

**Challenge 1 – The load balancer must support WebSocket**

If you use Nginx in front of several game servers (like in the [Docker article](../Docker/docker-and-docker-compose-en.md)), you must tell it to pass the "Upgrade" request through:

```nginx
location /ws/ {
  proxy_pass http://game_servers;
  proxy_http_version 1.1;
  proxy_set_header Upgrade $http_upgrade;
  proxy_set_header Connection "upgrade";
  proxy_read_timeout 3600s;  # Don't close idle connections too quickly
}
```

**Challenge 2 – Players on different servers can't see each other**

Imagine 3 game servers. Aung is connected to Server 1, and Su is connected to Server 2. When Aung sends a message, Server 1 only broadcasts to **its own** players, so Su never sees it.

The common solution is a **message broker** such as **Redis Pub/Sub**:

```
Aung ──► Server 1 ──► Redis ──► Server 1 ──► players on Server 1
                          ├───► Server 2 ──► players on Server 2 (Su)
                          └───► Server 3 ──► players on Server 3
```

Every server publishes messages to Redis, and every server subscribes to Redis. Now everyone receives every message, no matter which server they're connected to.

On AWS, **Amazon API Gateway WebSocket APIs** can manage the connections for you.

## 11. Security

- **Use `wss://`** (WebSocket Secure) in production. It's like `https://` and encrypts the data.
- **Authenticate on connect** – Check the user's token before accepting the connection. Don't let anyone join the game chat without logging in.
- **Validate every message** – Never trust data from the client. Check the type, length, and content of each message.
- **Check the Origin** – Accept connections only from your own website.
- **Rate-limit messages** – Stop one user from flooding the chat with thousands of messages.

## 12. Best Practices

- **Reconnect automatically** – Networks drop. When the connection closes unexpectedly, wait a moment and try again, waiting a little longer after each failed attempt (exponential backoff).
- **Use heartbeats** – Send ping/pong messages regularly to detect dead connections.
- **Give messages a `type`** – Makes it easy to handle chat, moves, scores, and errors separately.
- **Keep messages small** – Send only what changed, not the whole game state every time.
- **Don't use WebSocket for everything** – Normal actions like logging in, loading a profile, or saving settings work better with a normal REST API.

## When Should You Use WebSocket?

| Use WebSocket When | Use a Normal HTTP API When |
|---|---|
| Data changes many times per second or minute | Data changes rarely |
| The server needs to push updates instantly | The client asks only when it needs something |
| Both sides need to talk freely (chat, games) | It's a simple question and answer (get profile, save score) |

## Conclusion

HTTP is like sending letters: ask, wait for a reply, done. WebSocket is like a phone call: connect once, and both sides can talk instantly, at any time.

That's why WebSocket powers chat apps, multiplayer games, live scores, and real-time notifications. With FastAPI on the server and the built-in `WebSocket` in the browser, you can build a real-time app in just a few lines of code.

**HTTP asks. WebSocket listens.**
