# Client-Server Architecture နဲ့ Three-Tier Architecture

> ဖတ်ရန်: [English](client-server-and-three-tier-architecture-en.md) | **မြန်မာ**

Facebook ဖွင့်တာ၊ Email ပို့တာ၊ ATM ကနေ ငွေထုတ်တာ ဒါမှမဟုတ် Online Game ကစားတာ လုပ်တဲ့အခါ **ကိုယ့် Device** နဲ့ **တခြားနေရာက Computer တစ်လုံး** ကြား ခွဲဝေထားတဲ့ Software ကို သုံးနေတာ ဖြစ်ပါတယ်။

အဲဒီ Software ကို ဘယ်လို ခွဲထားလဲ၊ အစိတ်အပိုင်းတွေ အချင်းချင်း ဘယ်လို ဆက်သွယ်လဲဆိုတာကို **Architecture** လို့ ခေါ်ပါတယ်။

ဒီဆောင်းပါးမှာ Software Engineering ရဲ့ အရေးအကြီးဆုံး Architecture ၂ ခုကို လေ့လာပါမယ် -

- **Client-Server Architecture** – Internet ပေါ်က အရာအားလုံးနီးပါးရဲ့ အုတ်မြစ်။
- **Three-Tier Architecture** – Web နဲ့ Business Application တွေကို စီစဉ်တဲ့ အသုံးအများဆုံး နည်းလမ်း။

## ၁။ Client-Server Architecture ဆိုတာဘာလဲ?

**Client-Server Architecture** ဆိုတာ အလုပ်ကို Role ၂ ခုကြား ခွဲဝေထားတဲ့ Model တစ်ခု ဖြစ်ပါတယ် -

- **Client** – တစ်ခုခုကို တောင်းဆိုတယ် (**Request** ပို့တယ်)။
- **Server** – အဲဒါကို ပေးတယ် (**Response** ပို့တယ်)။

```
┌──────────┐      Request       ┌──────────┐
│          │ ─────────────────► │          │
│  Client  │                    │  Server  │
│          │ ◄───────────────── │          │
└──────────┘      Response      └──────────┘
```

အဓိက ထူးခြားချက်တွေ -

- **Client က စကားစပြောတယ်။** Server က Request တွေကို စောင့်ပြီး နားထောင်နေတယ်။
- **Server တစ်ခုက Client အများကြီးကို** တစ်ပြိုင်နက် ဝန်ဆောင်မှုပေးတယ်။
- **Server က မျှဝေသုံးတဲ့ Resource တွေကို ထိန်းထားတယ်** - Data, File, Business Logic နဲ့ Computing Power။
- **Network ကနေ ဆက်သွယ်ကြတယ်** - **Protocol** လို့ခေါ်တဲ့ သဘောတူထားတဲ့ စည်းမျဉ်းတွေ (ဥပမာ HTTP) ကို သုံးပြီးပါ။

## ၂။ စားသောက်ဆိုင် ဥပမာ

အရင်ဆောင်းပါးတွေမှာလိုပဲ **စားသောက်ဆိုင်** တစ်ဆိုင်ကို စဉ်းစားကြည့်ပါ -

| စားသောက်ဆိုင် | Client-Server |
|---|---|
| Customer တွေ | **Client** တွေ |
| စားသောက်ဆိုင် | **Server** |
| Order မှာတာ | **Request** |
| အစားအသောက် ရတာ | **Response** |
| စားပွဲထိုးနဲ့ ဘာသာစကား တူတူ ပြောတာ | **Protocol** |
| ဆိုင်တစ်ဆိုင်က Customer အများကြီးကို တစ်ပြိုင်နက် ကျွေးတာ | **Server တစ်ခု၊ Client အများကြီး** |

Customer တွေက ကိုယ်တိုင် မချက်ကြသလို အိမ်မှာ မီးဖိုချောင် ရှိစရာလည်း မလိုပါဘူး။ ပါဝင်ပစ္စည်း၊ ကိရိယာနဲ့ စားဖိုမှူးတွေ အားလုံးရှိတဲ့ ဆိုင်ကို မှာရုံပါပဲ။ အဲဒီလိုပဲ ကိုယ့် Phone က Facebook တစ်ခုလုံးကို သိမ်းထားစရာ မလိုပါဘူး။ Facebook ရဲ့ Server တွေကို တောင်းရုံပါပဲ။

## ၃။ နေ့စဉ်ဘဝထဲက Client-Server ဥပမာများ

| Client | Server | Protocol |
|---|---|---|
| Web Browser (Chrome, Firefox) | Web Server | HTTP / HTTPS |
| Email App (Gmail App, Outlook) | Mail Server | SMTP, IMAP |
| Mobile Banking App | Bank ရဲ့ API Server | HTTPS |
| ATM | Bank ရဲ့ Central Server | Bank Network Protocol များ |
| Online Game | Game Server | TCP / UDP / WebSocket |
| `google.com` ကို ရှာနေတဲ့ ကိုယ့် Computer | DNS Server | DNS |

## ၄။ Client က Server ကို ဘယ်လိုရှာပြီး ဆက်သွယ်လဲ?

Server ဆီ ရောက်ဖို့ Client မှာ ၂ ခု လိုပါတယ် -

- **IP Address** – Network ပေါ်က Server ရဲ့ လိပ်စာ ဖြစ်ပါတယ်။ စားသောက်ဆိုင်ရဲ့ လမ်းလိပ်စာ လိုပါပဲ။ ဥပမာ: `142.250.190.78`
- **Port** – Server ပေါ်က Service တစ်ခုအတွက် သတ်မှတ်ထားတဲ့ "တံခါး" ဖြစ်ပါတယ်။ ဆိုင်ရဲ့ ရှေ့တံခါးနဲ့ Delivery တံခါး ကွာသလိုပါပဲ။ ဥပမာ: HTTP အတွက် `80`၊ HTTPS အတွက် `443`၊ PostgreSQL အတွက် `5432`။

IP Address တွေက မှတ်ရခက်တဲ့အတွက် **Domain Name** (ဥပမာ `google.com`) တွေကို သုံးပြီး **DNS** က IP Address အဖြစ် ပြောင်းပေးပါတယ်။

## ၅။ ဥပမာ - Python နဲ့ Client-Server Program သေးသေးလေး

Python မှာ ပါပြီးသား `socket` Module ကိုပဲ သုံးပြီး အရိုးရှင်းဆုံး Client နဲ့ Server တစ်ခု တည်ဆောက်ကြည့်ရအောင်။ Server က Menu မေးခွန်းတွေကို ဖြေပေးတဲ့ လက်ဖက်ရည်ဆိုင် ဖြစ်ပါတယ်။

**server.py**

```python
import socket

HOST = "127.0.0.1"  # ဒီ Computer
PORT = 9000         # ကျွန်တော်တို့ Server နားထောင်မယ့် "တံခါး"

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
        conn, address = server.accept()  # Customer ကို စောင့်မယ်
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
    client.connect(("127.0.0.1", 9000))  # လက်ဖက်ရည်ဆိုင်ကို သွားမယ်
    client.sendall(b"mohinga")            # Order မှာမယ် (Request)
    answer = client.recv(1024).decode()   # အဖြေကို ယူမယ် (Response)
    print("Server replied:", answer)
```

**Run မယ်** (Terminal ၂ ခု သီးခြားစီမှာ)

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

`client.py` ကို အကြိမ်ကြိမ် Run ကြည့်ပါ၊ ဒါမှမဟုတ် Order ကို `tea` ဒါမှမဟုတ် `pizza` လို့ ပြောင်းကြည့်ပါ။ Server တစ်ခုတည်းက Client အများကြီးကို ဆက်ဖြေပေးနေပါတယ်။ ဒါဟာ Code ကြောင်း ၃၀ အောက်နဲ့ Client-Server Architecture ပါပဲ။

တကယ့် Web Server တွေလည်း အောက်ခြေမှာ ဒီအတိုင်းပဲ အလုပ်လုပ်ပါတယ်။ FastAPI နဲ့ Django လို Framework တွေက အောက်ခြေ အသေးစိတ်တွေ (HTTP, Client အများကြီး တစ်ပြိုင်နက်, Security) ကို ကိုယ့်အစား Handle လုပ်ပေးတာပါ။

## ၆။ Thin Client နဲ့ Thick Client

Client တွေက အလုပ်နည်းနည်း ဒါမှမဟုတ် အများကြီး လုပ်နိုင်ပါတယ်။

| | Thin Client | Thick (Fat) Client |
|---|---|---|
| အလုပ်အများစု ဘယ်မှာ လုပ်လဲ | Server ပေါ်မှာ | Client ပေါ်မှာ |
| Client က လိုအပ်တာ | Browser ဒါမှမဟုတ် ရိုးရှင်းတဲ့ App ပဲ | Processing Power နဲ့ Storage ပိုလိုတယ် |
| ဥပမာ | ရိုးရှင်းတဲ့ Web Page, Google Docs | PC Video Game, Photoshop |
| Update | Server ကို တစ်ခါ Update လုပ်ရုံ | User တွေက Update ကို Install လုပ်ရတယ် |

ခေတ်မီ App အများစုက နှစ်ခုကြားမှာ ရှိပါတယ်။ ဥပမာ Single-Page Web App က Browser ထဲမှာ အလုပ်အများကြီး လုပ်ပေမဲ့ Data ကိုတော့ Server ကနေပဲ ယူပါတယ်။

## ၇။ Client-Server နဲ့ Peer-to-Peer (P2P)

အရာအားလုံးက Client-Server ကို သုံးတာ မဟုတ်ပါဘူး။ **Peer-to-Peer** မှာ Computer တိုင်းက Client ရော Server ရော ဖြစ်နိုင်ပါတယ်။

| | Client-Server | Peer-to-Peer |
|---|---|---|
| ဖွဲ့စည်းပုံ | ဗဟို Server တစ်ခု၊ Client အများကြီး | Computer အားလုံး တန်းတူ "Peer" တွေ |
| Data သိမ်းတဲ့နေရာ | Server ပေါ်မှာ | Peer အားလုံးမှာ ဖြန့်ကျက်ထားတယ် |
| Server ပျက်သွားရင် | Service ရပ်သွားတယ် | တခြား Peer တွေ ဆက်အလုပ်လုပ်တယ် |
| ထိန်းချုပ်မှုနဲ့ Security | ဗဟိုကနေ စီမံရ လွယ်တယ် | ထိန်းချုပ်ရ ခက်တယ် |
| ဥပမာ | Website, Banking, Email | BitTorrent, Blockchain Network |

## ၈။ Client-Server ရဲ့ အားသာချက်နဲ့ အားနည်းချက်များ

**အားသာချက်များ**

- **Data ကို ဗဟိုမှာ စုထားတယ်** – လူတိုင်း တူညီပြီး နောက်ဆုံးရ Data ကို မြင်ရတယ်။
- **Security စီမံရ ပိုလွယ်တယ်** – Access Rule တွေကို နေရာတစ်ခုတည်းမှာ ထိန်းချုပ်တယ်။
- **Update လုပ်ရ ပိုလွယ်တယ်** – Server ကို Update လုပ်လိုက်ရင် Client အားလုံး အကျိုးရှိတယ်။
- **Scalability** – Client အရေအတွက် များလာရင် Server တွေ ထပ်တိုးနိုင်တယ်။

**အားနည်းချက်များ**

- **Single Point of Failure** – Server ပျက်သွားရင် Client တွေ အလုပ်မလုပ်နိုင်ဘူး (Backup နဲ့ Server အများကြီးထားပြီး ဖြေရှင်းတယ်)။
- **Network ကို မှီခိုတယ်** – Network မရှိရင် Service မရှိဘူး။
- **Server ဝန်ပိခြင်း** – Client တွေ တစ်ပြိုင်နက် အရမ်းများရင် Server နှေးသွားနိုင်တယ် (Load Balancing နဲ့ Scaling နဲ့ ဖြေရှင်းတယ်)။

## ၉။ Client-Server ကနေ Tier တွေဆီ

Application တွေ ကြီးလာတဲ့အခါ Developer တွေက **Server ဘက်** ကိုလည်း သီးခြား အစိတ်အပိုင်းတွေအဖြစ် ခွဲလာကြပါတယ်။ သီးခြား အစိတ်အပိုင်း တစ်ခုချင်းစီကို **Tier** လို့ ခေါ်ပါတယ်။

> **Tier နဲ့ Layer:** **Layer** ဆိုတာ Code ထဲက *Logical* ခွဲခြားမှု ဖြစ်ပါတယ် (ဥပမာ UI, Logic, Data အတွက် Folder သီးခြားစီ)။ **Tier** ကတော့ *Physical* ခွဲခြားမှု ဖြစ်ပြီး အစိတ်အပိုင်း တစ်ခုချင်းစီက မတူတဲ့ Machine ဒါမှမဟုတ် Container မှာ Run နိုင်ပါတယ်။ ဒီစကားလုံး နှစ်ခုကို ရောသုံးတာ မကြာခဏ ကြားရပေမဲ့ နည်းပညာအရ ကွာခြားချက်က ဒါပါပဲ။

| Architecture | Tier များ | ဥပမာ |
|---|---|---|
| **1-Tier** | အားလုံး Machine တစ်လုံးတည်းမှာ | Excel, Local Database File ပါတဲ့ Desktop App |
| **2-Tier** | Client + Database | MySQL Server ကို တိုက်ရိုက်ချိတ်တဲ့ ဆိုင်ဟောင်းတစ်ဆိုင်ရဲ့ Desktop App |
| **3-Tier** | Client + Application Server + Database | ခေတ်မီ Web Application အများစု |
| **N-Tier** | ၃ ခုထက်ပို (ဥပမာ + Cache, + Load Balancer, + သီးခြား Service များ) | Netflix, Amazon လို System ကြီးများ |

## ၁၀။ 2-Tier Architecture နဲ့ သူ့ရဲ့ ပြဿနာများ

**2-Tier Architecture** မှာ Client Application က **Database နဲ့ တိုက်ရိုက်** ဆက်သွယ်ပါတယ်။

```
┌──────────────────────┐         ┌──────────────┐
│  Client Application  │ ──SQL─► │   Database   │
│  (UI + Logic)        │ ◄────── │              │
└──────────────────────┘         └──────────────┘
```

စားသောက်ဆိုင်ကို ပြန်ကြည့်ရင် ဒါက **Customer တွေကို သိုလှောင်ခန်းထဲ ဝင်ခွင့်ပေးပြီး** ပါဝင်ပစ္စည်းတွေကို ကိုယ်တိုင် ယူခိုင်းတာနဲ့ တူပါတယ်။

ရိုးရှင်းပြီး ရုံးသေးသေးလေးတွေအတွက် အဆင်ပြေပေမဲ့ App ကြီးလာတာနဲ့အမျှ ပြဿနာကြီးတွေ ဖြစ်လာပါတယ် -

- **Security Risk** – Client တိုင်းမှာ Database Password လိုတယ်။ Computer တစ်လုံး Hack ခံရရင် Database တစ်ခုလုံး ပေါက်ကြားသွားနိုင်တယ်။
- **Update လုပ်ရ ခက်တယ်** – Business Rule တွေက Client App ထဲမှာ ရှိတဲ့အတွက် Rule တစ်ခု ပြောင်းတိုင်း Computer တိုင်းကို Update လုပ်ရတယ်။
- **လိမ်ရ လွယ်တယ်** – User တွေက Client ကို ပြင်ပြီး ကြိုက်တဲ့ Data ကို Database ထဲ တိုက်ရိုက် ပို့နိုင်တယ်။
- **Scalability ညံ့တယ်** – Database တွေက တိုက်ရိုက် Connection အရေအတွက် အကန့်အသတ်နဲ့ပဲ လက်ခံနိုင်တယ်။

Three-Tier Architecture က ဒီပြဿနာတွေကို ဖြေရှင်းပေးပါတယ်။

## ၁၁။ Three-Tier Architecture ဆိုတာဘာလဲ?

**Three-Tier Architecture** က Application တစ်ခုကို ကိုယ်ပိုင်တာဝန်ရှိတဲ့ သီးခြား Tier ၃ ခု အဖြစ် ခွဲထားပါတယ်။

```
┌───────────────────────────────┐
│     1. PRESENTATION TIER      │   User မြင်ပြီး အသုံးပြုရတဲ့အပိုင်း
│   Browser / Mobile App (UI)   │   HTML, CSS, JavaScript, React, Flutter
└───────────────┬───────────────┘
                │ HTTP / API (JSON)
┌───────────────▼───────────────┐
│     2. APPLICATION TIER       │   Business Logic နဲ့ Rule များ
│   Backend Server / API        │   Python, Node.js, Java, Go
└───────────────┬───────────────┘
                │ SQL / Query
┌───────────────▼───────────────┐
│        3. DATA TIER           │   Data သိမ်းဆည်း စီမံတယ်
│          Database             │   PostgreSQL, MySQL, MongoDB
└───────────────────────────────┘
```

**ရွှေစည်းမျဉ်း: Tier တစ်ခုချင်းစီက သူ့ဘေးက Tier နဲ့ပဲ ဆက်သွယ်တယ်။** Presentation Tier က Database နဲ့ **ဘယ်တော့မှ** တိုက်ရိုက် မဆက်သွယ်ပါဘူး။

## ၁၂။ Tier ၃ ခု အသေးစိတ်

**၁။ Presentation Tier (ထမင်းစားခန်း)**

- **တာဝန်:** User တွေကို အချက်အလက် ပြပြီး သူတို့ရဲ့ Input ကို လက်ခံတယ်။
- **Run တဲ့နေရာ:** User ရဲ့ Browser ဒါမှမဟုတ် Phone။
- **နည်းပညာ:** HTML, CSS, JavaScript, React, Vue, Mobile App (Swift, Kotlin, Flutter)။
- **မပါသင့်တာ:** အရေးကြီးတဲ့ Business Rule တွေ ဒါမှမဟုတ် Database Password။ Client ထဲက ဘာမဆို User တွေ မြင်ပြီး ပြင်နိုင်ပါတယ်။

**၂။ Application Tier (မီးဖိုချောင်)**

- **တာဝန်:** Business Logic ကို အကောင်အထည်ဖော်တယ်။ ဥပမာ: "ဒီ User က Login ဝင်ထားလား?"၊ "Account ထဲမှာ ငွေလုံလောက်လား?"၊ "ဒီ Score က မှန်ကန်လား?"
- **Run တဲ့နေရာ:** ကိုယ်ထိန်းချုပ်ထားတဲ့ Server တွေ။
- **နည်းပညာ:** Python (FastAPI, Django), Node.js (Express), Java (Spring Boot), Go။
- **တခြားအမည်များ:** Logic Tier, Business Tier, Middle Tier။

**၃။ Data Tier (သိုလှောင်ခန်း)**

- **တာဝန်:** Data ကို သိမ်း၊ ဖတ်ပြီး ကာကွယ်တယ်။
- **Run တဲ့နေရာ:** များသောအားဖြင့် Private Network ထဲက Database Server တွေ။
- **နည်းပညာ:** PostgreSQL, MySQL, SQL Server, MongoDB။

စားသောက်ဆိုင်မှာ **Customer တွေက ထမင်းစားခန်းထဲမှာပဲ နေတယ်**၊ **စားပွဲထိုးနဲ့ စားဖိုမှူးတွေပဲ မီးဖိုချောင်ထဲ ဝင်တယ်**၊ **မီးဖိုချောင် ဝန်ထမ်းတွေပဲ သိုလှောင်ခန်းထဲ ဝင်တယ်**။ နေရာ တစ်ခုချင်းစီမှာ ကိုယ်ပိုင်တာဝန်နဲ့ ကိုယ်ပိုင် ဝင်ခွင့် စည်းမျဉ်း ရှိပါတယ်။

## ၁၃။ ဥပမာ - Request တစ်ခုကို Tier ၃ ခုထဲ လိုက်ကြည့်ခြင်း

Online Banking ငွေလွှဲခြင်းကို ဥပမာ ယူကြည့်ရအောင်။

1. **Presentation Tier** – Banking App ထဲမှာ "Su ဆီ 50,000 MMK ပို့မယ်" လို့ ထည့်ပြီး **Send** ကို နှိပ်တယ်။ App က API ဆီ Request ပို့တယ်။
2. **Application Tier** – Server က စစ်ဆေးတယ် -
   - Login ဝင်ထားလား?
   - ပမာဏက အပေါင်းကိန်း ဟုတ်လား?
   - ငွေလုံလောက်လား?
   - တစ်နေ့တာ Limit အတွင်းမှာ ရှိလား?
3. **Data Tier** – စစ်ဆေးချက်အားလုံး Pass ဖြစ်ရင် Server က Database ထဲမှာ Account နှစ်ခုစလုံးကို Update လုပ်တယ်။
4. **Tier တွေကို ပြန်တက်လာတယ်** – Database က အတည်ပြုတယ်၊ Server က "Transfer successful" ပြန်ပို့တယ်၊ App က ✅ Message ပြတယ်။

ကိုယ့် Phone က Database ကို ဘယ်တုန်းကမှ မထိခဲ့ပါဘူး။ Application Tier နဲ့ပဲ ဆက်သွယ်ခဲ့တာပါ။

## ၁၄။ Business Rule တွေက ဘာကြောင့် Application Tier မှာ ရှိရမလဲ?

[Web Application ဆောင်းပါး](../Web-Application/what-is-web-application-mm.md) ထဲက Game Leaderboard ကို ပြန်ကြည့်ရအောင်။

Score မှန်ကန်လားဆိုတာကို **Browser ရဲ့ JavaScript ထဲမှာပဲ** စစ်တယ်ဆိုပါစို့။ လိမ်ညာသူတစ်ယောက်က Browser DevTools ကို ဖွင့်ပြီး စစ်ဆေးချက်ကို ကျော်ကာ ဒါကို ပို့နိုင်ပါတယ် -

```json
{ "player": "Cheater", "score": 99999999 }
```

ဒါကြောင့် Rule က User တွေ ပြင်လို့မရတဲ့ **Application Tier** မှာ ရှိရပါမယ် -

```python
from fastapi import HTTPException

MAX_SCORE = 1_000_000


@app.post("/api/scores", status_code=201)
def add_score(score: Score):
    # Business Rule: Browser မှာ မဟုတ်ဘဲ Application Tier မှာ စစ်တယ်
    if not 0 <= score.score <= MAX_SCORE:
        raise HTTPException(status_code=400, detail="Invalid score")

    save_score(score)  # Application Tier ကပဲ Data Tier နဲ့ ဆက်သွယ်တယ်
    return score
```

> Browser မှာ Input စစ်တာက ပိုကောင်းတဲ့ User Experience (Error ကို ချက်ချင်းပြတာ) အတွက် အသုံးဝင်ပါသေးတယ်။ ဒါပေမဲ့ **တကယ့်** စစ်ဆေးမှုကတော့ Server ပေါ်မှာ အမြဲ ဖြစ်ရပါမယ်။

## ၁၅။ Docker Compose နဲ့ Three-Tier Architecture

Docker Compose က Tier ၃ ခုကို အရမ်းရှင်းလင်းစေပါတယ်။ Tier တစ်ခုချင်းစီက သီးခြား Service ဖြစ်ပြီး ဘယ်သူ ဘယ်သူနဲ့ ဆက်သွယ်ခွင့်ရှိလဲဆိုတာကို **Network** တွေက ထိန်းချုပ်ပါတယ်။

**Project ဖွဲ့စည်းပုံ**

```
leaderboard/
├── frontend/
│   └── index.html         # Presentation Tier File များ
├── backend/
│   ├── main.py            # Application Tier
│   └── Dockerfile
├── nginx.conf
└── compose.yaml
```

**compose.yaml**

```yaml
services:
  # 1. Presentation Tier: Browser တွေဆီ HTML/JS ပို့ပေးတယ်
  web:
    image: nginx:1.27
    ports:
      - "80:80"
    volumes:
      - ./frontend:/usr/share/nginx/html:ro
      - ./nginx.conf:/etc/nginx/conf.d/default.conf:ro
    networks:
      - frontend

  # 2. Application Tier: API နဲ့ Business Rule များ
  api:
    build: ./backend
    environment:
      DATABASE_URL: postgresql://user:password@db:5432/games
    networks:
      - frontend
      - backend

  # 3. Data Tier: Database
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

  # Frontend File တွေ ပို့မယ်
  location / {
    root /usr/share/nginx/html;
  }

  # API Request တွေကို Application Tier ဆီ လွှဲပေးမယ်
  location /api/ {
    proxy_pass http://api:8000;
  }
}
```

တခြား Container တွေ ချိတ်ဆက်နိုင်အောင် Backend ရဲ့ Dockerfile က Server ကို `uvicorn main:app --host 0.0.0.0 --port 8000` နဲ့ စတင်သင့်ပါတယ်။

**Security Design ကို သတိပြုပါ -**

- `web` က `frontend` Network ပေါ်မှာပဲ ရှိတဲ့အတွက် Database ကို **မရောက်နိုင်ပါဘူး**။
- `db` က `backend` Network ပေါ်မှာပဲ ရှိပြီး **Public Port မရှိတဲ့** အတွက် Internet ပေါ်က ဘယ်သူမှ မရောက်နိုင်ပါဘူး။
- `api` ကပဲ Network နှစ်ခုစလုံးပေါ်မှာ ရှိတဲ့အတွက် Data ဆီ သွားနိုင်တဲ့ **တစ်ခုတည်းသော တံတား** ဖြစ်ပါတယ်။

Customer တွေက ထမင်းစားခန်းထဲမှာပဲ နေပြီး မီးဖိုချောင်ကပဲ သိုလှောင်ခန်းထဲ ဝင်နိုင်ပါတယ်။ (Compose အကြောင်း ပိုသိချင်ရင် [Docker ဆောင်းပါး](../Docker/docker-and-docker-compose-mm.md) ကို ကြည့်ပါ။)

## ၁၆။ Three-Tier Architecture ရဲ့ အကျိုးကျေးဇူးများ

**၁။ Security**

Database ကို Application Tier နောက်မှာ ဖုံးကွယ်ထားပါတယ်။ User တွေ Database Password ကို ဘယ်တော့မှ မရဘဲ Request တိုင်းက Business Rule တွေကို ဖြတ်သန်းရပါတယ်။

**၂။ Scalability – Tier တစ်ခုချင်းစီကို သီးခြား Scale လုပ်နိုင်တယ်**

Visitor တွေ များလာလား? Load Balancer နောက်မှာ Application Server တွေ ထပ်တိုးပါ။ Database ဝန်ပိနေလား? Database ကိုပဲ Upgrade လုပ်ပါ ဒါမှမဟုတ် Read Replica တွေ ထည့်ပါ။ အားလုံးကို တစ်ပြိုင်နက် Scale လုပ်စရာ မလိုပါဘူး။

**၃။ Maintainability**

Tier တစ်ခုကို တခြား Tier တွေ ပြန်မရေးဘဲ ပြောင်းလဲနိုင်ပါတယ်။ Database ကို မထိဘဲ Frontend ကို Design အသစ် ပြောင်းနိုင်သလို Data Access Code ကိုပဲ ပြောင်းပြီး MySQL ကနေ PostgreSQL ကို ပြောင်းနိုင်ပါတယ်။

**၄။ Backend တစ်ခု၊ Frontend အများကြီး**

Application Tier တစ်ခုတည်းက API တစ်ခုတည်းကနေ Website, Android App, iOS App နဲ့ တခြားကုမ္ပဏီတွေရဲ့ System တွေကိုပါ ဝန်ဆောင်မှု ပေးနိုင်ပါတယ်။

```
  Website ──┐
  Android ──┼──► Application Tier (API) ──► Database
  iOS ──────┘
```

**၅။ Team အလိုက် အထူးပြုခြင်း**

Frontend, Backend နဲ့ Database ကျွမ်းကျင်သူတွေက ကိုယ့် Tier ပေါ်မှာ တစ်ပြိုင်နက် အလုပ်လုပ်နိုင်ပါတယ်။

## ၁၇။ အားနည်းချက်များ

- **ပိုရှုပ်ထွေးတယ်** – တစ်ခုအစား ၃ ခုကို တည်ဆောက်၊ Deploy လုပ်ပြီး စောင့်ကြည့်ရတယ်။
- **Network Hop ပိုများတယ်** – Request တိုင်းက Tier ပိုများများကို ဖြတ်ရတဲ့အတွက် Latency နည်းနည်း တိုးတယ်။
- **App သေးသေးလေးတွေအတွက် ပိုလွန်းတယ်** – ကိုယ်ပိုင် Script ဒါမှမဟုတ် Offline Tool သေးသေးလေးတွေအတွက် Tier ၃ ခု မလိုပါဘူး။

## ၁၈။ AWS ပေါ်က Three-Tier Architecture

AWS ပေါ်မှာ Tier ၃ ခု တည်ဆောက်တဲ့ အသုံးများတဲ့ နည်းလမ်း -

| Tier | AWS Service များ |
|---|---|
| **Presentation** | Amazon S3 + CloudFront (Static Frontend) ဒါမှမဟုတ် AWS Amplify |
| **Application** | Application Load Balancer နောက်မှာ Amazon EC2, ECS (Container) ဒါမှမဟုတ် AWS Lambda (Serverless) |
| **Data** | **Private Subnet** ထဲမှာ Amazon RDS (PostgreSQL/MySQL) ဒါမှမဟုတ် DynamoDB |

Private Subnet ထဲက Database က ကျွန်တော်တို့ Docker ဥပမာနဲ့ စည်းမျဉ်း အတူတူပါပဲ - Application Tier ကပဲ ရောက်နိုင်ပါတယ်။

## ၁၉။ Tier ၃ ခုထက် ကျော်ပြီး

System တွေ ပိုကြီးလာတဲ့အခါ Tier နဲ့ Pattern တွေ ထပ်ထည့်လာကြပါတယ် -

- **Load Balancer** – Traffic ကို Application Server အများကြီးဆီ ခွဲဝေပေးတယ်။
- **Cache Tier** (Redis) – မြန်ဆန်ဖို့ မကြာခဏသုံးတဲ့ Data တွေကို Memory ထဲမှာ ထားတယ်။
- **Message Queue** (RabbitMQ, Amazon SQS) – Email ပို့တာလို ကြာတဲ့ အလုပ်တွေကို Background မှာ Handle လုပ်တယ်။
- **Microservices** – Application Tier ကို ကိုယ်ပိုင် Database စီရှိတဲ့ သီးခြား Service သေးလေးတွေ (User, Payment, Order) အဖြစ် ခွဲတယ်။

ဒါပေမဲ့ သူတို့အားလုံးနီးပါးဟာ အယူအဆ တစ်ခုတည်းပေါ်မှာပဲ တည်ဆောက်ထားဆဲ ဖြစ်ပါတယ် - **Client က မေးတယ်၊ Server က ဖြေတယ်၊ အစိတ်အပိုင်း တစ်ခုချင်းစီမှာ ရှင်းလင်းတဲ့ တာဝန်တစ်ခု ရှိတယ်။**

## နှိုင်းယှဉ်ချက် အနှစ်ချုပ်

| | 1-Tier | 2-Tier | 3-Tier |
|---|---|---|---|
| ဖွဲ့စည်းပုံ | အားလုံး တစ်ခုတည်းထဲမှာ | Client → Database | Client → App Server → Database |
| Security | Local မှာပဲ | အားနည်းတယ် (Client တွေ DB ကို ဝင်နိုင်တယ်) | အားကောင်းတယ် (DB ကို ဖုံးကွယ်ထားတယ်) |
| Scalability | မရှိဘူး | အကန့်အသတ်ရှိတယ် | မြင့်တယ် |
| Logic Update | Install တစ်ခုချင်းစီကို Update | Client တိုင်းကို Update | Server ကို တစ်ခါ Update |
| သင့်တော်တဲ့နေရာ | ကိုယ်ပိုင် Tool | ရုံးသုံး App သေးသေးလေး | Web, Mobile နဲ့ Business App များ |

## နိဂုံး

**Client-Server Architecture** ဟာ Internet ရဲ့ အုတ်မြစ် ဖြစ်ပါတယ်။ Customer တွေနဲ့ စားသောက်ဆိုင်လိုပဲ Client တွေက Request ပို့ပြီး Server တွေက Response ပြန်ပို့ပါတယ်။

**Three-Tier Architecture** ကတော့ Server ဘက်ကို **Presentation Tier** (ထမင်းစားခန်း)၊ **Application Tier** (မီးဖိုချောင်) နဲ့ **Data Tier** (သိုလှောင်ခန်း) ဆိုပြီး ရှင်းလင်းတဲ့ အစိတ်အပိုင်းတွေအဖြစ် စီစဉ်ပေးပါတယ်။ Tier တစ်ခုချင်းစီမှာ တာဝန်တစ်ခုစီ ရှိပြီး ဘေးက Tier နဲ့ပဲ ဆက်သွယ်တဲ့အတွက် Application တွေ ပိုလုံခြုံ၊ Scale လုပ်ရ ပိုလွယ်ပြီး ထိန်းသိမ်းရ ပိုလွယ်လာပါတယ်။

ဒီ Architecture နှစ်ခုကို နားလည်သွားပြီဆိုရင် Banking App ကနေ Online Game အထိ နေရာတိုင်းမှာ သူတို့ကို မှတ်မိလာပါလိမ့်မယ်။

**ကောင်းမွန်တဲ့ Architecture ဆိုတာ အရာအားလုံးကို သင့်တော်တဲ့ နေရာမှာ ထားတာပါပဲ - Customer ကို ထမင်းစားခန်းမှာ၊ စားဖိုမှူးကို မီးဖိုချောင်မှာ၊ ပါဝင်ပစ္စည်းတွေကို သိုလှောင်ခန်းမှာ။**
