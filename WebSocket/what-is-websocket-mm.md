# WebSocket ဆိုတာဘာလဲ။ ဘယ်လိုအလုပ်လုပ်သလဲ?

> ဖတ်ရန်: [English](what-is-websocket-en.md) | **မြန်မာ**

[API ဆောင်းပါး](../API/what-is-api-mm.md) မှာ Client က **Request** ပို့တယ်၊ Server က **Response** ပြန်ပို့တယ်၊ ပြီးရင် ဆက်သွယ်မှု ပြီးဆုံးသွားတယ်ဆိုတာ လေ့လာခဲ့ပြီးပါပြီ။

Website Page ဖွင့်တာ၊ ရာသီဥတု Data ယူတာ၊ Game Score သိမ်းတာ စတဲ့ အလုပ်အများစုအတွက် ဒါက အဆင်ပြေပါတယ်။

ဒါပေမဲ့ တချို့ App တွေမှာ Data ပြောင်းလဲတာနဲ့ **ချက်ချင်း** ရောက်လာဖို့ လိုပါတယ် -

- Chat Message အသစ်က ချက်ချင်း ပေါ်လာရမယ်။
- Online Game မှာ တခြား Player တွေ လှုပ်ရှားတာကို Real-time မြင်ရမယ်။
- ဘောလုံးပွဲ Score တွေ၊ Stock Price တွေ Live Update ဖြစ်ရမယ်။
- တစ်ယောက်ယောက်က ကိုယ့် Post ကို Like လုပ်တာနဲ့ Notification ချက်ချင်း ပေါ်လာရမယ်။

ပုံမှန် HTTP မှာ Client က အရင်မမေးရင် Server က ဘာမှ ပို့လို့မရပါဘူး။ ဒါဆို ဒီ App တွေက ဘယ်လို အလုပ်လုပ်နေတာလဲ?

အဖြေကတော့ **WebSocket** ဖြစ်ပါတယ်။

## ၁။ WebSocket ဆိုတာဘာလဲ?

**WebSocket** ဆိုတာ Client နဲ့ Server ကြားမှာ **Connection တစ်ခုကို ဖွင့်ထားပြီး** **နှစ်ဘက်စလုံးက ဘယ်အချိန်မဆို Message ပို့နိုင်အောင်** လုပ်ပေးတဲ့ Communication Protocol တစ်ခု ဖြစ်ပါတယ်။

အလွယ်ဆုံး နားလည်နိုင်ဖို့ **စာပို့တာ** နဲ့ **ဖုန်းခေါ်တာ** ကို နှိုင်းယှဉ်ကြည့်ရအောင်။

- **HTTP က စာပို့တာနဲ့ တူပါတယ်။** စာတစ်စောင်ရေးပို့တယ် (Request)၊ စာပြန်လာတာကို စောင့်တယ် (Response)၊ ပြီးရင် ပြီးသွားတယ်။ အသစ်တစ်ခုခု သိချင်ရင် နောက်ထပ် စာတစ်စောင် ထပ်ရေးရတယ်။
- **WebSocket က ဖုန်းခေါ်တာနဲ့ တူပါတယ်။** တစ်ခါခေါ်လိုက်ရင် Line က ပွင့်နေတယ်။ တစ်ယောက်ယောက် ဖုန်းမချမချင်း နှစ်ယောက်စလုံး ကြိုက်တဲ့အချိန် စကားပြောလို့ရတယ်။

API ဆောင်းပါးက စားသောက်ဆိုင်ကိုလည်း ပြန်သွားကြည့်ရအောင် -

- **HTTP နဲ့ဆိုရင်** စားပွဲထိုးကို "ကျွန်တော့် အစားအသောက် ရပြီလား? … အခုရော ရပြီလား? … အခုရော?" လို့ ခဏခဏ မေးနေရတယ်။ အများအားဖြင့် အဖြေက "မရသေးဘူး" ပါပဲ။
- **WebSocket နဲ့ဆိုရင်** ဆိုင်က **Buzzer** လေးတစ်ခု ပေးလိုက်တယ်။ ကိုယ်က ထိုင်ပြီး အေးအေးဆေးဆေး စောင့်နေရုံပဲ။ အစားအသောက် အဆင်သင့်ဖြစ်တာနဲ့ **ချက်ချင်း** Buzzer မြည်လာပါတယ်။

## ၂။ HTTP နဲ့ WebSocket ဘာကွာလဲ?

| | HTTP | WebSocket |
|---|---|---|
| Connection | Request တစ်ခုချင်းစီအတွက် ဖွင့်ပြီး ပိတ်တယ် | ဖွင့်ထားတယ် |
| ဘယ်သူ စပြောလို့ရလဲ | Client ပဲ | Client ရော Server ရော |
| ဦးတည်ချက် | တစ်ကြိမ်မှာ တစ်ဖက်တည်း (Request → Response) | နှစ်ဖက်စလုံး တစ်ပြိုင်နက် (Full-duplex) |
| Real-time Update | Client က ခဏခဏ မေးနေရတယ် | Server က ချက်ချင်း Push လုပ်ပေးတယ် |
| Overhead | Request တိုင်းမှာ Header တွေ ပါတယ် | Connect ပြီးရင် Message Frame သေးသေးလေးတွေပဲ |
| URL | `http://` / `https://` | `ws://` / `wss://` |
| သင့်တော်တဲ့နေရာ | Page ဖွင့်တာ၊ REST API၊ Form | Chat၊ Game၊ Live Data၊ Notification |

## ၃။ WebSocket မပေါ်ခင်က ဘယ်လိုလုပ်ခဲ့ကြလဲ?

**၁။ Polling – "ရောက်ပြီလား?"**

Client က စက္ကန့်အနည်းငယ်တိုင်း Data အသစ်ရှိလား Request ပို့ပြီး စစ်ပါတယ်။

```
Client: Message အသစ် ရှိလား?   Server: မရှိဘူး။
Client: Message အသစ် ရှိလား?   Server: မရှိဘူး။
Client: Message အသစ် ရှိလား?   Server: မရှိဘူး။
Client: Message အသစ် ရှိလား?   Server: ရှိတယ်! ၁ ခု ရှိတယ်။
```

ရိုးရှင်းပေမဲ့ Request တွေ အများကြီး အလဟဿ ဖြစ်သလို Update တွေလည်း နောက်ကျနိုင်ပါတယ်။

**၂။ Long Polling – "တစ်ခုခုရှိရင် ပြောပါ"**

Client က Request ပို့ပြီး Server က Data အသစ်မရှိမချင်း Request ကို ဖွင့်ထားပေးပါတယ်။ Data ရောက်လာရင် Client က နောက်ထပ် Request တစ်ခု ချက်ချင်း ပြန်ပို့ပါတယ်။ Polling ထက်တော့ ကောင်းပေမဲ့ Message တိုင်းအပြီးမှာ Request အသစ် ဖွင့်ရပါသေးတယ်။

**၃။ Server-Sent Events (SSE) – တစ်လမ်းသွား ရေဒီယို**

Server က Connection တစ်ခုတည်းကနေ Client ဆီ Update တွေ ဆက်တိုက် ပို့နိုင်ပေမဲ့ Client က အဲဒီ Connection ကနေ ပြန်ပြောလို့ မရပါဘူး။ Live News Feed ဒါမှမဟုတ် AI Response တွေ Stream လုပ်တာမျိုးအတွက် ကောင်းပေမဲ့ နှစ်ဖက်ပြောရတဲ့ Chat နဲ့ Game တွေအတွက် မသင့်တော်ပါဘူး။

**၄။ WebSocket – ဖုန်းခေါ်ခြင်း**

Connection တစ်ခုတည်း၊ နှစ်ဖက်ပြော၊ Real-time ပါ။

## ၄။ WebSocket ဘယ်လိုအလုပ်လုပ်သလဲ?

WebSocket Connection မှာ အဆင့် ၃ ဆင့် ရှိပါတယ်။

**အဆင့် ၁ – Handshake (ဖုန်းခေါ်ခြင်း)**

Connection က ပုံမှန် HTTP Request တစ်ခုအနေနဲ့ စတင်ပြီး Server ကို WebSocket အဖြစ် "Upgrade" လုပ်ပေးဖို့ တောင်းဆိုပါတယ်။

```http
GET /ws/chat HTTP/1.1
Host: game.example.com
Upgrade: websocket
Connection: Upgrade
Sec-WebSocket-Key: dGhlIHNhbXBsZSBub25jZQ==
Sec-WebSocket-Version: 13
```

Server က သဘောတူရင် **101 Switching Protocols** Status Code နဲ့ ပြန်ဖြေပါတယ် -

```http
HTTP/1.1 101 Switching Protocols
Upgrade: websocket
Connection: Upgrade
Sec-WebSocket-Accept: s3pPLMBiTxaQ9kYGzzhZRbK+xOo=
```

ဖုန်းကို ကိုင်လိုက်ပါပြီ။ အခုကစပြီး ဒီ Connection က HTTP မဟုတ်တော့ဘဲ WebSocket ဖြစ်သွားပါပြီ။

**အဆင့် ၂ – Message ပို့ခြင်း (စကားပြောခြင်း)**

အခု နှစ်ဖက်စလုံးက ဘယ်အချိန်မဆို Message ပို့နိုင်ပါပြီ။ Message တွေကို **Frame** လို့ခေါ်တဲ့ အပိုင်းသေးသေးလေးတွေအဖြစ် ပို့ပြီး အထဲမှာ -

- **Text** (များသောအားဖြင့် JSON)
- **Binary Data** (ပုံ၊ အသံ၊ Game Data)

တွေ ပါနိုင်ပါတယ်။

တစ်ဖက်က ရှိနေသေးလားဆိုတာ စစ်ဖို့ **Ping/Pong** ဆိုတဲ့ အထူး Frame တွေလည်း ရှိပါတယ် ("ဟဲလို၊ Line ပေါ်မှာ ရှိသေးလား?")။

**အဆင့် ၃ – ပိတ်ခြင်း (ဖုန်းချခြင်း)**

ဘယ်ဘက်ကမဆို **Close** Frame ပို့ပြီး Connection ကို ယဉ်ယဉ်ကျေးကျေး ပိတ်နိုင်ပါတယ်။ Network ပြတ်သွားရင်လည်း Connection ပိတ်သွားမှာဖြစ်ပြီး App က ပြန်ချိတ်ဆက်ဖို့ ကြိုးစားသင့်ပါတယ်။

## ၅။ WebSocket ကို ဘယ်နေရာတွေမှာ သုံးလဲ?

- **Chat App** – Chat ထဲက လူတိုင်းဆီ Message တွေ ချက်ချင်း ပေါ်လာတယ်။
- **Multiplayer Online Game** – Player တွေရဲ့ နေရာ၊ လုပ်ဆောင်ချက်နဲ့ Score တွေ Real-time Update ဖြစ်တယ်။
- **Live Sports Score နဲ့ Stock Price** – ဂဏန်းတွေ ပြောင်းတာနဲ့ ချက်ချင်း Update ဖြစ်တယ်။
- **Notification** – Page ကို Refresh မလုပ်ဘဲ "တစ်ယောက်က ကိုယ့် Post မှာ Comment ပေးထားတယ်" ဆိုတာ ပေါ်လာတယ်။
- **Collaborative Editing** – လူအများက Document တစ်ခုတည်းကို တစ်ပြိုင်နက် ပြင်ပြီး အချင်းချင်း ပြင်တာတွေကို Live မြင်ရတယ်။
- **Live Dashboard** – Server Monitoring၊ Delivery Tracking နဲ့ IoT Sensor Data တွေ။

## ၆။ ဥပမာ - Live Game Chat Server

Game Lobby Chat တစ်ခု တည်ဆောက်ကြည့်ရအောင်။ Player တစ်ယောက်က Message ပို့လိုက်တာနဲ့ **Connect ဖြစ်နေတဲ့ Player အားလုံး** ဆီ ချက်ချင်း ရောက်သွားပါမယ်။ **FastAPI** ကိုပဲ ပြန်သုံးပါမယ်။

**main.py**

```python
from fastapi import FastAPI, WebSocket, WebSocketDisconnect

app = FastAPI()


class ConnectionManager:
    """Connect ဖြစ်နေတဲ့ Player အားလုံးကို မှတ်ထားမယ်"""

    def __init__(self):
        self.active: list[WebSocket] = []

    async def connect(self, websocket: WebSocket):
        await websocket.accept()  # ဖုန်းကိုင်မယ်
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
            message = await websocket.receive_text()  # Message ကို စောင့်မယ်
            await manager.broadcast(f"{player}: {message}")
    except WebSocketDisconnect:
        manager.disconnect(websocket)
        await manager.broadcast(f"👋 {player} left the game")
```

**Run မယ်**

```bash
pip install fastapi "uvicorn[standard]"
uvicorn main:app --reload
```

`uvicorn[standard]` ထဲမှာ Server အတွက် လိုအပ်တဲ့ WebSocket Support ပါဝင်ပါတယ်။

## ၇။ Browser ကနေ ချိတ်ဆက်ခြင်း (JavaScript)

ခေတ်မီ Browser တိုင်းမှာ WebSocket ပါပြီးသား ဖြစ်ပါတယ်။

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

ဒီ File ကို **Browser Window ၂ ခု** မှာ ဖွင့်ပြီး နာမည်မတူတာ ထည့်ကာ Message ပို့ကြည့်ပါ။ Page ကို Refresh မလုပ်ဘဲ Window နှစ်ခုစလုံးမှာ ချက်ချင်း ပေါ်လာပါလိမ့်မယ်။

မှတ်ထားရမယ့် Event ၄ ခု -

| Event | ဘယ်အချိန်မှာ ဖြစ်လဲ |
|---|---|
| `onopen` | Connection အဆင်သင့်ဖြစ်ပြီ |
| `onmessage` | Server ဆီက Message ရောက်လာပြီ |
| `onclose` | Connection ပိတ်သွားပြီ |
| `onerror` | တစ်ခုခု မှားသွားပြီ |

## ၈။ Python ကနေ ချိတ်ဆက်ခြင်း

Python Program ကနေလည်း ချိတ်ဆက်နိုင်ပါတယ်။ ဥပမာ Game Chat ထဲ ဝင်လာမယ့် Bot တစ်ခုပါ။

```python
import asyncio
import websockets


async def main():
    async with websockets.connect("ws://127.0.0.1:8000/ws/Bot") as ws:
        await ws.send("Hello everyone! I'm a bot 🤖")
        async for message in ws:  # Message အသစ်တွေကို ဆက်နားထောင်မယ်
            print(message)


asyncio.run(main())
```

```bash
pip install websockets
```

## ၉။ စနစ်တကျ Message ပို့ခြင်း (JSON)

လက်တွေ့ App တွေမှာ Client က Message ကို ဘာလုပ်ရမလဲ သိအောင် Message တွေမှာ **type** တစ်ခု ပါလေ့ရှိပါတယ်။

```json
{ "type": "chat", "player": "Aung", "text": "Good game!" }
```

```json
{ "type": "move", "player": "Su", "x": 120, "y": 45 }
```

```json
{ "type": "score", "player": "Aung", "score": 1500 }
```

Client ဘက်မှာ -

```javascript
ws.onmessage = (event) => {
  const data = JSON.parse(event.data);

  if (data.type === "chat") showChatMessage(data);
  if (data.type === "move") movePlayer(data);
  if (data.type === "score") updateLeaderboard(data);
};
```

## ၁၀။ WebSocket ကို Scale လုပ်ခြင်း

WebSocket Connection တွေက **အချိန်ကြာကြာ ဖွင့်ထားရ** ပါတယ်။ Connect ဖြစ်နေတဲ့ Player တစ်ယောက်ချင်းစီဟာ သတ်မှတ်ထားတဲ့ Server တစ်ခုနဲ့ Connection ဖွင့်ထားပါတယ်။ ဒါကြောင့် Scale လုပ်တဲ့အခါ စိန်ခေါ်မှု ၂ ခု ရှိလာပါတယ်။

**စိန်ခေါ်မှု ၁ – Load Balancer က WebSocket ကို Support လုပ်ရမယ်**

Game Server အများကြီးရဲ့ ရှေ့မှာ Nginx ကို သုံးထားရင် ([Docker ဆောင်းပါး](../Docker/docker-and-docker-compose-mm.md) မှာလို) "Upgrade" Request ကို ဖြတ်သန်းခွင့်ပေးဖို့ ပြောရပါမယ် -

```nginx
location /ws/ {
  proxy_pass http://game_servers;
  proxy_http_version 1.1;
  proxy_set_header Upgrade $http_upgrade;
  proxy_set_header Connection "upgrade";
  proxy_read_timeout 3600s;  # အသုံးမပြုတဲ့ Connection တွေကို မြန်မြန် မပိတ်ပါနဲ့
}
```

**စိန်ခေါ်မှု ၂ – Server မတူတဲ့ Player တွေက အချင်းချင်း မမြင်ရဘူး**

Game Server ၃ ခု ရှိတယ်ဆိုပါစို့။ Aung က Server 1 နဲ့ Connect ဖြစ်နေပြီး Su က Server 2 နဲ့ Connect ဖြစ်နေတယ်။ Aung က Message ပို့လိုက်တဲ့အခါ Server 1 က **သူ့ဆီမှာရှိတဲ့** Player တွေဆီပဲ Broadcast လုပ်တဲ့အတွက် Su က ဘယ်တော့မှ မမြင်ရပါဘူး။

အသုံးများတဲ့ ဖြေရှင်းနည်းကတော့ **Redis Pub/Sub** လို **Message Broker** တစ်ခုကို သုံးတာပါ -

```
Aung ──► Server 1 ──► Redis ──► Server 1 ──► Server 1 က Player တွေ
                          ├───► Server 2 ──► Server 2 က Player တွေ (Su)
                          └───► Server 3 ──► Server 3 က Player တွေ
```

Server တိုင်းက Message တွေကို Redis ဆီ Publish လုပ်ပြီး Server တိုင်းက Redis ကို Subscribe လုပ်ထားပါတယ်။ အခုဆိုရင် ဘယ် Server နဲ့ Connect ဖြစ်နေနေ လူတိုင်းက Message တိုင်းကို ရပါပြီ။

AWS မှာဆိုရင် **Amazon API Gateway WebSocket APIs** က Connection တွေကို စီမံပေးနိုင်ပါတယ်။

## ၁၁။ Security

- Production မှာ **`wss://`** (WebSocket Secure) ကို သုံးပါ။ `https://` လိုပဲ Data တွေကို Encrypt လုပ်ပေးပါတယ်။
- **Connect လုပ်တဲ့အခါ Authenticate လုပ်ပါ** – Connection ကို လက်မခံခင် User ရဲ့ Token ကို စစ်ပါ။ Login မဝင်ဘဲ Game Chat ထဲ ဘယ်သူမှ ဝင်ခွင့်မပေးပါနဲ့။
- **Message တိုင်းကို စစ်ဆေးပါ** – Client ဆီက Data ကို ဘယ်တော့မှ မယုံပါနဲ့။ Message တစ်ခုချင်းစီရဲ့ Type၊ အရှည်နဲ့ Content ကို စစ်ပါ။
- **Origin ကို စစ်ပါ** – ကိုယ့် Website ကလာတဲ့ Connection တွေကိုပဲ လက်ခံပါ။
- **Message တွေကို Rate Limit လုပ်ပါ** – User တစ်ယောက်က Message ထောင်ချီ ပို့ပြီး Chat ကို ပြည့်မသွားအောင် ကာကွယ်ပါ။

## ၁၂။ ကောင်းမွန်တဲ့ အလေ့အကျင့်များ (Best Practices)

- **အလိုအလျောက် ပြန်ချိတ်ပါ (Reconnect)** – Network တွေ ပြတ်တတ်ပါတယ်။ Connection မမျှော်လင့်ဘဲ ပိတ်သွားရင် ခဏစောင့်ပြီး ပြန်ကြိုးစားပါ။ မအောင်မြင်တိုင်း စောင့်ချိန်ကို နည်းနည်းချင်း တိုးပါ (Exponential Backoff)။
- **Heartbeat သုံးပါ** – သေသွားတဲ့ Connection တွေကို သိနိုင်ဖို့ Ping/Pong Message တွေ ပုံမှန်ပို့ပါ။
- **Message တွေမှာ `type` ထည့်ပါ** – Chat၊ Move၊ Score၊ Error တွေကို သီးခြားစီ Handle လုပ်ရ လွယ်စေပါတယ်။
- **Message တွေကို သေးသေးထားပါ** – Game State တစ်ခုလုံးကို ခဏခဏ မပို့ဘဲ ပြောင်းသွားတာကိုပဲ ပို့ပါ။
- **အရာအားလုံးအတွက် WebSocket မသုံးပါနဲ့** – Login ဝင်တာ၊ Profile ဖွင့်တာ၊ Setting သိမ်းတာလို ပုံမှန်အလုပ်တွေအတွက် ပုံမှန် REST API က ပိုသင့်တော်ပါတယ်။

## WebSocket ကို ဘယ်အချိန်မှာ သုံးသင့်လဲ?

| WebSocket သုံးသင့်တဲ့အခါ | ပုံမှန် HTTP API သုံးသင့်တဲ့အခါ |
|---|---|
| Data က တစ်စက္ကန့် ဒါမှမဟုတ် တစ်မိနစ်အတွင်း အကြိမ်ကြိမ် ပြောင်းတယ် | Data က ခဏခဏ မပြောင်းဘူး |
| Server က Update တွေကို ချက်ချင်း Push လုပ်ဖို့ လိုတယ် | Client က လိုအပ်မှပဲ မေးတယ် |
| နှစ်ဖက်စလုံး လွတ်လပ်စွာ ပြောဖို့လိုတယ် (Chat၊ Game) | ရိုးရိုး မေးခွန်းနဲ့ အဖြေပဲ (Profile ယူတာ၊ Score သိမ်းတာ) |

## နိဂုံး

HTTP ဆိုတာ စာပို့တာနဲ့ တူပါတယ် - မေးမယ်၊ အဖြေကို စောင့်မယ်၊ ပြီးပြီ။ WebSocket ကတော့ ဖုန်းခေါ်တာနဲ့ တူပါတယ် - တစ်ခါ Connect လုပ်လိုက်ရင် နှစ်ဖက်စလုံး ဘယ်အချိန်မဆို ချက်ချင်း ပြောလို့ရပါတယ်။

ဒါကြောင့် Chat App၊ Multiplayer Game၊ Live Score နဲ့ Real-time Notification တွေမှာ WebSocket ကို သုံးကြတာပါ။ Server ဘက်မှာ FastAPI နဲ့ Browser ထဲက `WebSocket` ကို သုံးပြီး Code နည်းနည်းလေးနဲ့ Real-time App တစ်ခုကို တည်ဆောက်နိုင်ပါတယ်။

**HTTP က မေးတယ်။ WebSocket က နားထောင်တယ်။**
