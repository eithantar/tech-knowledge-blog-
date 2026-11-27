# API ဆိုတာဘာလဲ။ ဘယ်လိုအလုပ်လုပ်သလဲ?

> ဖတ်ရန်: [English](what-is-api-en.md) | **မြန်မာ**

နေ့စဉ်နဲ့အမျှ ကျွန်တော်တို့ သုံးနေတဲ့ App တွေဟာ ကျွန်တော်တို့ မသိလိုက်ဘဲ တခြား System တွေနဲ့ ဆက်သွယ်နေကြပါတယ်။

Weather App က ဒီနေ့ ရာသီဥတုကို ပြပေးတယ်။ Shopping Website က Bank Card နဲ့ ငွေချေခွင့်ပေးတယ်။ Game တစ်ခုက Google Account နဲ့ Login ဝင်ခွင့်ပေးတယ်။ Food Delivery App ထဲမှာ Map ပေါ်လာတယ်။

ဒီ App တွေက အရာအားလုံးကို ကိုယ်တိုင် တည်ဆောက်ထားတာ မဟုတ်ပါဘူး။ တခြား System တွေဆီကနေ Data နဲ့ Feature တွေကို "ငှားသုံး" နေကြတာပါ။

ဒါကို ဖြစ်နိုင်အောင် လုပ်ပေးတဲ့ နည်းပညာကတော့ **API** ဖြစ်ပါတယ်။

## ၁။ API ဆိုတာဘာလဲ?

**API** ဆိုတာ **Application Programming Interface** ရဲ့ အတိုကောက် ဖြစ်ပါတယ်။

ရိုးရိုးရှင်းရှင်းပြောရရင် API ဆိုတာ Software Application တစ်ခုက တခြား Application တစ်ခုဆီကနေ **Data ဒါမှမဟုတ် Service တွေကို တောင်းဆို** ပြီး Response ပြန်ရနိုင်အောင် သတ်မှတ်ထားတဲ့ စည်းမျဉ်းတွေ ဖြစ်ပါတယ်။

API ကို အလွယ်ဆုံး နားလည်နိုင်ဖို့ **စားသောက်ဆိုင်** တစ်ဆိုင်နဲ့ နှိုင်းယှဉ်ကြည့်ရအောင်။

- **ကိုယ် (Customer)** က အစားအသောက် စားချင်တယ်၊ ဒါပေမဲ့ မီးဖိုချောင်ထဲကို ကိုယ်တိုင် ဝင်လို့မရဘူး။
- **မီးဖိုချောင် (Kitchen)** မှာ အစားအသောက်တွေ ရှိတယ်၊ ဘယ်လိုချက်ရမလဲဆိုတာလည်း သိတယ်။
- **စားပွဲထိုး (Waiter)** က ကိုယ့် Order ကို မီးဖိုချောင်ဆီ ယူသွားပြီး အစားအသောက်ကို ပြန်ယူလာပေးတယ်။
- **Menu** က ဘာတွေ မှာလို့ရလဲဆိုတာ ပြောပြတယ်။

| စားသောက်ဆိုင် | API လောက |
|---|---|
| Customer | **Client** (ကိုယ့် App, Website ဒါမှမဟုတ် Program) |
| မီးဖိုချောင် | **Server** (Data ရှိတဲ့ System) |
| စားပွဲထိုး | **API** |
| Menu | **API Documentation** |
| ကိုယ်မှာတဲ့ Order | **Request** |
| ပြန်ရလာတဲ့ အစားအသောက် | **Response** |

မီးဖိုချောင်က ဘယ်လိုချက်လဲဆိုတာ ကိုယ်သိစရာ မလိုပါဘူး။ Menu ကြည့်ပြီး ဘယ်လိုမှာရမလဲဆိုတာပဲ သိဖို့လိုပါတယ်။ အဲဒီလိုပဲ တခြား System တစ်ခုရဲ့ အတွင်းပိုင်း ဘယ်လိုအလုပ်လုပ်လဲဆိုတာ သိစရာမလိုဘဲ သူ့ရဲ့ API ကို ဘယ်လိုသုံးရမလဲဆိုတာပဲ သိဖို့လိုပါတယ်။

## ၂။ နေ့စဉ်ဘဝမှာ API ကို ဘယ်နေရာတွေမှာ သုံးနေလဲ?

- **Weather App** – Weather Service API ကနေ မိုးလေဝသ ခန့်မှန်းချက် Data ကို ယူတယ်။
- **"Login with Google"** – ကိုယ်ဘယ်သူလဲဆိုတာ စစ်ဆေးဖို့ Google ရဲ့ API ကို သုံးတယ်။
- **Online Payment** – Shopping Website တွေက Card တွေကို စီမံဖို့ Payment API (ဥပမာ Stripe, PayPal) ကို သုံးတယ်။
- **Map** – Delivery နဲ့ Taxi App တွေက Map API ကို သုံးပြီး Map ပြတယ်။
- **AI Chatbot** – App တွေက ကိုယ့်မေးခွန်းကို AI Model ရဲ့ API ဆီ ပို့ပြီး အဖြေကို ပြန်ပြတယ်။
- **Currency Exchange Rate** – Finance App တွေက နောက်ဆုံးရ ငွေလဲနှုန်းတွေကို Exchange Rate API ကနေ ယူတယ်။

## ၃။ API ဘယ်လိုအလုပ်လုပ်သလဲ?

API ဆက်သွယ်မှုမှာ အမြဲတမ်း အပိုင်း ၂ ပိုင်း ပါပါတယ် - **Request** နဲ့ **Response** ဖြစ်ပါတယ်။

**အဆင့် ၁ – Client က Request ပို့တယ်**

Request ထဲမှာ ပါဝင်တာတွေက -

- **Endpoint (URL)** – Request ကို ဘယ်ကို ပို့မလဲ။ ဥပမာ: `https://api.example.com/users/1`
- **Method** – ဘာလုပ်ချင်လဲ (Data ယူမလား၊ အသစ်ဖန်တီးမလား၊ ပြင်မလား၊ ဖျက်မလား)။
- **Headers** – Data Format ဒါမှမဟုတ် API Key လို အပို အချက်အလက်တွေ။
- **Body** – ပို့မယ့် Data (Data အသစ်ဖန်တီးတာလို Method အချို့မှာပဲ ပါတယ်)။

**အဆင့် ၂ – Server က Request ကို စီမံတယ်**

Server က Request ကို စစ်ဆေးပြီး Data ကို ရှာတာ ဒါမှမဟုတ် ပြောင်းလဲတာ လုပ်ကာ အဖြေကို ပြင်ဆင်ပါတယ်။

**အဆင့် ၃ – Server က Response ပြန်ပို့တယ်**

Response ထဲမှာ ပါဝင်တာတွေက -

- **Status Code** – Request အောင်မြင်လား၊ မအောင်မြင်ဘူးလားဆိုတာ ပြတဲ့ ဂဏန်း။
- **Body** – ကိုယ်တောင်းထားတဲ့ Data (များသောအားဖြင့် **JSON** Format နဲ့)။

## ၄။ HTTP Method များ – ဘာလုပ်ချင်တာလဲ?

Web API အများစုက HTTP Method တွေကို သုံးပါတယ်။ Method တစ်ခုချင်းစီဟာ လုပ်ဆောင်ချက်တစ်ခုနဲ့ ကိုက်ညီပါတယ်။ စားသောက်ဆိုင်မှာ မတူတဲ့ အရာတွေ မှာသလိုပါပဲ။

| Method | လုပ်ဆောင်ချက် | စားသောက်ဆိုင် ဥပမာ | API ဥပမာ |
|---|---|---|---|
| **GET** | Data ဖတ်ခြင်း | "Menu ကြည့်ပါရစေ" | User စာရင်းကို ယူမယ် |
| **POST** | Data အသစ်ဖန်တီးခြင်း | "ဟင်းအသစ်တစ်ပွဲ မှာမယ်" | User အသစ် ဖန်တီးမယ် |
| **PUT** | Data တစ်ခုလုံး အစားထိုးခြင်း | "Order တစ်ခုလုံး ပြောင်းပေးပါ" | User ရဲ့ အချက်အလက်အားလုံးကို ပြင်မယ် |
| **PATCH** | Data တစ်စိတ်တစ်ပိုင်း ပြင်ခြင်း | "အစပ်လျှော့ပေးပါ" | User ရဲ့ Email ကိုပဲ ပြင်မယ် |
| **DELETE** | Data ဖျက်ခြင်း | "Order ကို Cancel လုပ်ပေးပါ" | User ကို ဖျက်မယ် |

ဒီလုပ်ဆောင်ချက် ၄ မျိုး — Create, Read, Update, Delete — ကို **CRUD** လို့ ခေါ်လေ့ရှိပါတယ်။

## ၅။ Status Code များ – အောင်မြင်လား?

Server က အမြဲတမ်း Status Code တစ်ခုနဲ့ ပြန်ဖြေပါတယ်။ ပထမဆုံး ဂဏန်းကို ကြည့်ရုံနဲ့ ဘာဖြစ်သွားလဲဆိုတာ သိနိုင်ပါတယ်။

| Code | အဓိပ္ပာယ် | စားသောက်ဆိုင် ဥပမာ |
|---|---|---|
| **200 OK** | အောင်မြင်တယ် | အစားအသောက် ရောက်လာပြီ။ |
| **201 Created** | Data အသစ် ဖန်တီးပြီးပြီ | Order အသစ်ကို လက်ခံလိုက်ပြီ။ |
| **400 Bad Request** | Request မှားနေတယ် | အဓိပ္ပာယ်မရှိတဲ့ အရာကို မှာနေတယ်။ |
| **401 Unauthorized** | Login မဝင်ထားဘူး ဒါမှမဟုတ် Key မမှန်ဘူး | Member Card အရင်ပြပါ။ |
| **403 Forbidden** | ခွင့်ပြုချက် မရှိဘူး | ဒါက VIP အခန်းပါ၊ ဝင်ခွင့်မရှိပါဘူး။ |
| **404 Not Found** | Data မရှိဘူး | အဲဒီဟင်းက Menu ထဲမှာ မရှိပါဘူး။ |
| **429 Too Many Requests** | Request အရမ်းများနေတယ် | ခဏစောင့်ပါ၊ မီးဖိုချောင် အရမ်းအလုပ်များနေတယ်။ |
| **500 Internal Server Error** | Server ဘက်မှာ ပြဿနာရှိတယ် | မီးဖိုချောင်ထဲမှာ ပြဿနာတက်နေတယ်။ |

အလွယ်မှတ်နည်း -

- **2xx** – အောင်မြင်တယ်
- **4xx** – Client ဘက်က မှားတယ်
- **5xx** – Server ဘက်က မှားတယ်

## ၆။ JSON ဆိုတာဘာလဲ?

ခေတ်မီ API အများစုက Data တွေကို **JSON** (JavaScript Object Notation) Format နဲ့ ပို့ပြီး လက်ခံပါတယ်။ လူရော Computer ရော ဖတ်ရလွယ်ပါတယ်။

```json
{
  "id": 1,
  "name": "Aung Aung",
  "email": "aung@example.com",
  "skills": ["Python", "Docker", "AWS"],
  "is_active": true
}
```

- Data တွေကို **key: value** အတွဲလိုက် ရေးပါတယ်။
- `[ ]` က List တစ်ခုကို ဆိုလိုတယ်။
- `{ }` က Object တစ်ခုကို ဆိုလိုတယ်။

## ၇။ API အမျိုးအစားများ

**ဒီဇိုင်းပုံစံအလိုက်:**

- **REST API** – အသုံးအများဆုံး ပုံစံပါ။ URL နဲ့ HTTP Method (GET, POST စသည်) တွေကို သုံးပြီး များသောအားဖြင့် JSON နဲ့ ဆက်သွယ်ပါတယ်။
- **GraphQL** – Client က ကိုယ်လိုချင်တဲ့ Field တွေကိုပဲ Request တစ်ခုတည်းနဲ့ အတိအကျ တောင်းနိုင်ပါတယ်။ ပိုလည်းမပို၊ လိုလည်းမလိုပါဘူး။
- **WebSocket** – Connection ကို ဖွင့်ထားပြီး Server က Data တွေကို ချက်ချင်း ပို့ပေးနိုင်ပါတယ်။ Chat App, Live Game, Live Price တွေမှာ သုံးပါတယ်။
- **SOAP** – XML ကို သုံးတဲ့ ပုံစံအဟောင်း ဖြစ်ပါတယ်။ Bank တွေနဲ့ လုပ်ငန်းကြီးတွေရဲ့ System တွေမှာ အခုထိ တွေ့ရပါသေးတယ်။

**ဘယ်သူသုံးနိုင်လဲ အလိုက်:**

- **Public API** – ဘယ်သူမဆို သုံးနိုင်ပါတယ်။ တစ်ခါတလေ အခမဲ့ API Key လိုပါတယ် (ဥပမာ Weather API)။
- **Private API** – ကုမ္ပဏီတစ်ခုရဲ့ ကိုယ်ပိုင် System တွေကြားမှာပဲ သုံးပါတယ်။
- **Partner API** – သတ်မှတ်ထားတဲ့ စီးပွားရေး Partner တွေနဲ့ပဲ မျှဝေသုံးပါတယ်။

## ၈။ API ကို ခေါ်သုံးခြင်း (လက်တွေ့ဥပမာ)

**JSONPlaceholder** ဆိုတဲ့ အခမဲ့ Test API ကို ခေါ်ကြည့်ရအောင်။

**curl (Terminal) နဲ့**

```bash
# GET – Post တစ်ခုကို ဖတ်မယ်
curl https://jsonplaceholder.typicode.com/posts/1

# POST – Post အသစ် ဖန်တီးမယ်
curl -X POST https://jsonplaceholder.typicode.com/posts \
  -H "Content-Type: application/json" \
  -d '{"title": "Hello API", "body": "My first request", "userId": 1}'
```

**Python နဲ့**

```python
import requests

# GET – Data ဖတ်မယ်
response = requests.get("https://jsonplaceholder.typicode.com/posts/1", timeout=10)
print(response.status_code)      # 200
print(response.json()["title"])

# POST – Data အသစ် ပို့မယ်
new_post = {"title": "Hello API", "body": "My first request", "userId": 1}
response = requests.post("https://jsonplaceholder.typicode.com/posts", json=new_post, timeout=10)
print(response.status_code)      # 201
print(response.json())
```

Library ကို အောက်ပါအတိုင်း Install လုပ်ပါ -

```bash
pip install requests
```

## ၉။ ကိုယ်ပိုင် API တည်ဆောက်ခြင်း (လက်တွေ့ဥပမာ)

အခု ကျွန်တော်တို့က "မီးဖိုချောင်" ဖြစ်ကြည့်ရအောင်။ လူကြိုက်များတဲ့ Python Framework ဖြစ်တဲ့ **FastAPI** ကို သုံးပြီး **Game Score API** လေးတစ်ခု တည်ဆောက်ပါမယ်။

**main.py**

```python
from fastapi import FastAPI, HTTPException
from pydantic import BaseModel

app = FastAPI()

class Score(BaseModel):
    player: str
    score: int

scores: list[Score] = []

# GET – Leaderboard ကို ပြမယ်
@app.get("/scores")
def get_scores():
    return sorted(scores, key=lambda s: s.score, reverse=True)

# POST – Score အသစ် ထည့်မယ်
@app.post("/scores", status_code=201)
def add_score(score: Score):
    scores.append(score)
    return score

# GET – Player တစ်ယောက်ရဲ့ Score ကို ရှာမယ်
@app.get("/scores/{player}")
def get_player_score(player: str):
    for s in scores:
        if s.player == player:
            return s
    raise HTTPException(status_code=404, detail="Player not found")
```

**Run မယ်**

```bash
pip install fastapi uvicorn
uvicorn main:app --reload
```

**စမ်းကြည့်မယ်**

```bash
# Score ထည့်မယ်
curl -X POST http://127.0.0.1:8000/scores \
  -H "Content-Type: application/json" \
  -d '{"player": "Aung", "score": 1200}'

# Leaderboard ကို ကြည့်မယ်
curl http://127.0.0.1:8000/scores

# မရှိတဲ့ Player ကို ရှာမယ် → 404
curl http://127.0.0.1:8000/scores/Nobody
```

FastAPI က **Interactive Documentation** ("Menu") ကိုလည်း အလိုအလျောက် ဖန်တီးပေးပါတယ်။ Browser မှာ `http://127.0.0.1:8000/docs` ကို ဖွင့်ပြီး Endpoint အားလုံးကို ကြည့်ရှု စမ်းသပ်နိုင်ပါတယ်။

> ဒီ API က Score တွေကို Memory ထဲမှာပဲ သိမ်းထားတဲ့အတွက် Server ရပ်လိုက်ရင် ပျောက်သွားပါမယ်။ လက်တွေ့ Project မှာဆိုရင် PostgreSQL လို Database ထဲမှာ သိမ်းရမှာဖြစ်ပြီး Docker နဲ့ အားလုံးကို ထုပ်ပိုးနိုင်ပါတယ် ([Docker ဆောင်းပါး](../Docker/docker-and-docker-compose-mm.md) ကို ကြည့်ပါ)။

## ၁၀။ API Security – ဘယ်သူ ဝင်ခွင့်ရှိလဲ?

API တိုင်းကို လူတိုင်း သုံးခွင့်ရှိသင့်တာ မဟုတ်ပါဘူး။ Access ကို ထိန်းချုပ်တဲ့ နည်းလမ်းတွေက -

- **API Key** – ကိုယ့် App ကို ခွဲခြားသိနိုင်တဲ့ လျှို့ဝှက် စာသားတစ်ခုပါ။ စားသောက်ဆိုင်ရဲ့ Member Card လိုပါပဲ။
- **Bearer Token / OAuth** – Login ဝင်ပြီးရင် ရတဲ့ ယာယီ Token ဖြစ်ပါတယ်။ "Login with Google" လို Feature တွေမှာ သုံးပါတယ်။
- **HTTPS** – Data တွေကို Encrypt လုပ်ပေးလို့ လမ်းမှာ ဘယ်သူမှ ဖတ်လို့ မရပါဘူး။
- **Rate Limiting** – Server ဝန်မပိအောင် Client တစ်ခုက တစ်မိနစ်မှာ Request ဘယ်နှစ်ခု ပို့နိုင်လဲဆိုတာ ကန့်သတ်ထားတာပါ။

API Key ကို လုံခြုံစွာ ပို့တဲ့ ဥပမာ -

```python
import os
import requests

api_key = os.environ["WEATHER_API_KEY"]  # Code ထဲမှာ တိုက်ရိုက်မရေးဘဲ Environment Variable ကနေ ဖတ်မယ်

response = requests.get(
    "https://api.example.com/weather?city=Yangon",
    headers={"Authorization": f"Bearer {api_key}"},
    timeout=10,
)
```

API Key တွေကို Code ထဲမှာ တိုက်ရိုက် **ဘယ်တော့မှ** မရေးပါနဲ့၊ GitHub ပေါ်ကိုလည်း မတင်ပါနဲ့။ Environment Variable ဒါမှမဟုတ် `.gitignore` ထဲ ထည့်ထားတဲ့ `.env` File ကို သုံးပါ။

## ၁၁။ API နဲ့ Web Scraping ဘာကွာလဲ?

| | API | Web Scraping |
|---|---|---|
| Data ယူပုံ | Server ကို တရားဝင် "တံခါး" ကနေ တောင်းတယ် | Website ရဲ့ HTML ကို ဖတ်တယ် |
| Data Format | စနစ်တကျ (JSON) | HTML ထဲကနေ ထုတ်ယူရတယ် |
| တည်ငြိမ်မှု | တည်ငြိမ်တယ်၊ ပြောင်းလဲမှုတွေကို ကြိုကြေညာလေ့ရှိတယ် | Website Design ပြောင်းရင် ပျက်သွားတတ်တယ် |
| ခွင့်ပြုချက် | Provider က တရားဝင် ခွင့်ပြုထားတယ် | Website ရဲ့ Terms အပေါ် မူတည်တယ် |

Official API ရှိနေတယ်ဆိုရင် Scraping လုပ်တာထက် API ကို သုံးတာ ပိုကောင်းပါတယ်။ ([Web Scraping ဆောင်းပါး](../Web-Scraping/what-is-web-scraping-mm.md) ကို ကြည့်ပါ)

## ၁၂။ ကောင်းမွန်တဲ့ အလေ့အကျင့်များ (Best Practices)

**API ကို သုံးတဲ့အခါ:**

- API Documentation ကို အရင်ဖတ်ပါ။
- API Key တွေကို လျှို့ဝှက်ထားပါ။
- Response ကို မသုံးခင် Status Code ကို အမြဲစစ်ပါ။
- ကိုယ့် App က အဆုံးမရှိ မစောင့်နေအောင် Timeout သတ်မှတ်ပါ။
- Rate Limit တွေကို လိုက်နာပါ။

**API တည်ဆောက်တဲ့အခါ:**

- ရှင်းလင်းတဲ့ နာမ်ပုံစံ URL တွေကို သုံးပါ (`/users`, `/scores`)။ လုပ်ဆောင်ချက်ကို HTTP Method က ဖော်ပြပါစေ။
- မှန်ကန်တဲ့ Status Code တွေကို ပြန်ပို့ပါ။
- ရှိပြီးသား App တွေ မပျက်အောင် API ကို Version ခွဲပါ (ဥပမာ `/v1/scores`)။
- Input Data အားလုံးကို စစ်ဆေးပါ (Validate လုပ်ပါ)။
- ကောင်းမွန်တဲ့ Documentation ရေးပါ (FastAPI နဲ့ OpenAPI/Swagger က ကူညီပေးပါတယ်)။

## နိဂုံး

API ဆိုတာ စားသောက်ဆိုင်က စားပွဲထိုးတစ်ယောက်လိုပါပဲ။ ကိုယ့် Request ကို Data ရှိတဲ့ System ဆီ ယူသွားပြီး Response ကို ပြန်ယူလာပေးပါတယ်။ မီးဖိုချောင်ထဲမှာ ဘယ်လိုအလုပ်လုပ်လဲဆိုတာ ကိုယ်သိစရာ မလိုပါဘူး။

ဒီနေ့ Digital ကမ္ဘာမှာ Weather App, Payment, Map, Login, AI Chatbot စတဲ့ အရာအားလုံးနီးပါးကို API တွေက ချိတ်ဆက်ပေးထားပါတယ်။ Request, Response, HTTP Method, Status Code နဲ့ JSON ကို နားလည်သွားပြီဆိုရင် တခြားသူတွေရဲ့ API ကိုလည်း သုံးနိုင်သလို ကိုယ်ပိုင် API ကိုလည်း တည်ဆောက်နိုင်ပါပြီ။

**API ဆိုတာ Software တွေ အချင်းချင်း စကားပြောနိုင်အောင် ဆက်သွယ်ပေးတဲ့ တံတားတွေ ဖြစ်ပါတယ်။**
