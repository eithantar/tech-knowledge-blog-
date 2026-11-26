# Docker နဲ့ Docker Compose ဆိုတာဘာလဲ?

> ဖတ်ရန်: [English](docker-and-docker-compose-en.md) | **မြန်မာ**

Developer တွေဆီကနေ *"ကျွန်တော့်စက်မှာတော့ အလုပ်လုပ်တယ်လေ!"* ဆိုတဲ့ စကားကို ကြားဖူးကြမှာပါ။

Application တစ်ခုဟာ Computer တစ်လုံးမှာ ကောင်းကောင်း အလုပ်လုပ်ပေမဲ့ နောက် Computer တစ်လုံးမှာတော့ Operating System မတူတာ၊ Library တစ်ခုခု မပါတာ ဒါမှမဟုတ် Python ဒါမှမဟုတ် Database Version မတူတာကြောင့် အလုပ်မလုပ်တာမျိုး ဖြစ်တတ်ပါတယ်။

Computer နဲ့ Server တိုင်းမှာ လိုအပ်တာတွေကို ကိုယ်တိုင် Install လုပ်၊ Setting ချိန်နေရမယ်ဆိုရင် အချိန်ကုန်သလို အမှားတွေလည်း ဖြစ်လွယ်ပါတယ်။

ဒီပြဿနာကို ဖြေရှင်းပေးတဲ့ နည်းပညာကတော့ **Docker** ဖြစ်ပါတယ်။

## ၁။ Docker ဆိုတာဘာလဲ?

ရိုးရိုးရှင်းရှင်းပြောရရင် Docker ဆိုတာ Application တစ်ခုနဲ့ အဲဒီ Application အလုပ်လုပ်ဖို့ လိုအပ်တဲ့ Code, Library, Setting နဲ့ Runtime အားလုံးကို **Container** လို့ခေါ်တဲ့ အထုပ်တစ်ခုထဲမှာ စုစည်းထုပ်ပိုးပေးတဲ့ Tool တစ်ခုဖြစ်ပါတယ်။

Docker ကို အလွယ်ဆုံး နားလည်နိုင်ဖို့ **ဂိမ်းစက်** တစ်လုံးနဲ့ နှိုင်းယှဉ်ကြည့်ရအောင်။

ဂိမ်းခွေတစ်ခွေ ဝယ်လာတဲ့အခါ Graphics Engine တွေ၊ Sound Driver တွေ၊ Setting တွေကို ကိုယ်တိုင် Install လုပ်စရာ မလိုပါဘူး။ ဂိမ်းခွေကို ဂိမ်းစက်ထဲ ထည့်လိုက်ရုံနဲ့ ကစားလို့ရပါပြီ။ အဲဒီဂိမ်းခွေကို ကိုယ့်အိမ်မှာဖြစ်ဖြစ်၊ သူငယ်ချင်းအိမ်မှာဖြစ်ဖြစ်၊ ဂိမ်းဆိုင်မှာဖြစ်ဖြစ် ကိုက်ညီတဲ့ ဂိမ်းစက်တိုင်းမှာ အတူတူပဲ ကစားလို့ရပါတယ်။

Docker လည်း အဲဒီအတိုင်းပါပဲ -

- ဂိမ်းအတွက် လိုအပ်တာအားလုံး ပါဝင်တဲ့ **ဂိမ်းခွေ** → Application အတွက် လိုအပ်တာအားလုံး ပါဝင်တဲ့ Docker **Image**
- ဂိမ်းခွေကို Run ပေးတဲ့ **ဂိမ်းစက်** → Image ကို Run ပေးတဲ့ **Docker**
- လက်ရှိ **ကစားနေတဲ့ ဂိမ်း** → Run နေတဲ့ **Container**

Docker Install လုပ်ထားရင် ကိုယ့် Laptop မှာဖြစ်ဖြစ်၊ အဖွဲ့သားတစ်ယောက်ရဲ့ Computer မှာဖြစ်ဖြစ်၊ Cloud Server မှာဖြစ်ဖြစ် Application ဟာ အတူတူပဲ အလုပ်လုပ်ပါတယ်။

## ၂။ Docker ရဲ့ အဓိက အယူအဆများ (ဂိမ်းစက်နဲ့ နှိုင်းယှဉ်ချက်)

| Docker | ဂိမ်းစက် ဥပမာ | အဓိပ္ပာယ် |
|---|---|---|
| **Docker Engine** | ဂိမ်းစက် | Container တွေကို Run ပေးတဲ့ Software |
| **Image** | ဂိမ်းခွေ | Application နဲ့ Environment ပါဝင်တဲ့ Read-only Package |
| **Container** | လက်ရှိ ကစားနေတဲ့ ဂိမ်း | Image ကနေ Run နေတဲ့ Instance |
| **Dockerfile** | ဂိမ်းခွေ ထုတ်လုပ်ဖို့ ညွှန်ကြားချက် | Image တည်ဆောက်ဖို့ အဆင့်ဆင့် ညွှန်ကြားချက် |
| **Registry (Docker Hub)** | Online ဂိမ်းဆိုင် | Image တွေကို Download လုပ်ပြီး မျှဝေနိုင်တဲ့ နေရာ |
| **Volume** | Memory Card / Save Data | Data မပျောက်အောင် Container အပြင်မှာ သိမ်းထားတဲ့ နေရာ |
| **Network** | Multiplayer ချိတ်ဆက်မှု | Container တွေ အချင်းချင်း ဆက်သွယ်နိုင်အောင် လုပ်ပေးတယ် |
| **Docker Compose** | ဂိမ်းဆိုင်ရဲ့ Control Panel | စက်အများကြီးကို တစ်ပြိုင်နက် စတင်၊ စီမံပေးတယ် |

**Image – ဂိမ်းခွေ**

ဂိမ်းခွေလိုပါပဲ Image ကို တစ်ခါ ဖန်တီးပြီးရင် ပြောင်းလဲလို့ မရပါဘူး။ ဂိမ်းခွေတစ်ခွေတည်းကို အကြိမ်ကြိမ် ကစားလို့ရသလို Image တစ်ခုတည်းကို အကြိမ်ကြိမ် Run လို့ရပါတယ်။

**Container – ကစားနေတဲ့ ဂိမ်း**

ဂိမ်းခွေ တစ်မျိုးတည်းကို ဂိမ်းစက် အများကြီးမှာ တစ်ပြိုင်နက် ကစားလို့ရပါတယ်။ အဲဒီလိုပဲ Image တစ်ခုတည်းကနေ Container အများကြီး Run နိုင်ပါတယ်။

**Volume – Memory Card**

Memory Card မရှိဘဲ ဂိမ်းစက်ကို ပိတ်လိုက်ရင် ကစားထားသမျှ Progress တွေ ပျောက်သွားမှာပါ။ Container လည်း အတူတူပါပဲ။ Container ကို ဖျက်လိုက်ရင် အထဲက Data တွေ ပျောက်သွားပါတယ်။ Volume က Memory Card လို အလုပ်လုပ်ပြီး Database လို အရေးကြီးတဲ့ Data တွေကို လုံခြုံစွာ သိမ်းထားပေးပါတယ်။

**Network – Multiplayer**

Multiplayer ဂိမ်းတွေမှာ ဂိမ်းစက်တွေ အချင်းချင်း ချိတ်ဆက်ကြပါတယ်။ Docker Network ကလည်း Container တွေ အချင်းချင်း ဆက်သွယ်နိုင်အောင် လုပ်ပေးပါတယ်။ ဥပမာ Game Server က Database နဲ့ ချိတ်ဆက်တာမျိုးပါ။

## ၃။ Container နဲ့ Virtual Machine ဘာကွာလဲ?

Container ရော Virtual Machine (VM) ရော သီးခြား Environment တွေ ဖန်တီးပေးပေမဲ့ အလုပ်လုပ်ပုံ မတူပါဘူး။

ဂိမ်းနဲ့ ဥပမာပေးရရင် **Virtual Machine** က ဂိမ်းတစ်ခုကစားဖို့ ဂိမ်းစက် အသစ်တစ်လုံးလုံး ဝယ်ရသလိုပါပဲ။ **Container** ကတော့ ဂိမ်းစက်တစ်လုံးတည်းထဲကို ဂိမ်းခွေ အမျိုးမျိုး လဲထည့်သလိုပါ။

| | Container | Virtual Machine |
|---|---|---|
| Operating System | Host OS ရဲ့ Kernel ကို မျှဝေသုံးတယ် | Guest OS တစ်ခုလုံး Run တယ် |
| အရွယ်အစား | သေးတယ် (MB) | ကြီးတယ် (GB) |
| စတင်ချိန် | စက္ကန့်ပိုင်း | မိနစ်ပိုင်း |
| Resource အသုံးပြုမှု | ပေါ့ပါးတယ် | လေးလံတယ် |

Container တွေက ပေါ့ပါးတဲ့အတွက် Computer တစ်လုံးတည်းမှာ အများကြီး Run နိုင်ပါတယ်။

## ၄။ Dockerfile ရေးသားခြင်း

ဒီဆောင်းပါးမှာ ဥပမာအဖြစ် **Game Score Server** တစ်ခုကို အသုံးပြုပါမယ်။ ကစားသမားတွေရဲ့ အမှတ်တွေကို သိမ်းပြီး Leaderboard ပြပေးတဲ့ Python Web API လေးတစ်ခုပါ။

Project ဖွဲ့စည်းပုံ -

```
game-server/
├── app.py
├── requirements.txt
└── Dockerfile
```

**Dockerfile** (ကျွန်တော်တို့ရဲ့ "ဂိမ်းခွေ" ထုတ်လုပ်ဖို့ ညွှန်ကြားချက်)

```dockerfile
# ၁။ Official Python Image ကနေ စတင်မယ်
FROM python:3.12-slim

# ၂။ Container ထဲမှာ အလုပ်လုပ်မယ့် Folder သတ်မှတ်မယ်
WORKDIR /app

# ၃။ လိုအပ်တဲ့ Library တွေ Install လုပ်မယ်
COPY requirements.txt .
RUN pip install --no-cache-dir -r requirements.txt

# ၄။ Application Code တွေကို Copy ကူးမယ်
COPY . .

# ၅။ Container စတင်တဲ့အခါ Run မယ့် Command
CMD ["python", "app.py"]
```

## ၅။ အခြေခံ Docker Command များ

```bash
# "ဂိမ်းခွေ" ထုတ်မယ် (Image တည်ဆောက်မယ်)
docker build -t game-server:1.0 .

# ဂိမ်းခွေထည့်ပြီး ကစားမယ် (Container Run မယ်)
docker run -d -p 5000:5000 --name game-server game-server:1.0

# ဘယ်ဂိမ်းတွေ Run နေလဲ ကြည့်မယ်
docker ps

# Container ရဲ့ Log တွေကို ကြည့်မယ်
docker logs game-server

# ဂိမ်းကို ရပ်ပြီး ဖယ်ရှားမယ်
docker stop game-server
docker rm game-server

# ကိုယ့်မှာရှိတဲ့ ဂိမ်းခွေ (Image) တွေကို ကြည့်မယ်
docker images

# ဂိမ်းဆိုင် (Docker Hub) ကနေ ဂိမ်းခွေ Download လုပ်မယ်
docker pull postgres:16
```

## ၆။ Docker Compose ဆိုတာဘာလဲ?

လက်တွေ့ Application တွေမှာ Service တစ်ခုထက်ပိုပြီး လိုအပ်လေ့ရှိပါတယ်။

ကျွန်တော်တို့ရဲ့ Game Score Server အတွက် -
- **Game Server** (Python API)
- အမှတ်တွေ သိမ်းဖို့ **Database** (PostgreSQL)
- နောက်ပိုင်းမှာ ကစားသမားတွေကို Server အများကြီးဆီ ခွဲဝေပေးဖို့ **Load Balancer** (Nginx)

**ဂိမ်းဆိုင်** တစ်ဆိုင် ဖွင့်ထားတယ်ဆိုပါစို့။ မနက်တိုင်း ဂိမ်းစက်တစ်လုံးချင်းစီကို ဖွင့်၊ ဂိမ်းခွေ မှန်မှန်ထည့်၊ ကြိုးတွေ ချိတ်နေရမယ်ဆိုရင် အရမ်းပင်ပန်းမှာပါ။

အဲဒီအစား ဂိမ်းဆိုင်မှာ **Control Panel** တစ်ခုရှိတယ်ဆိုပါစို့။ ခလုတ်တစ်ချက်နှိပ်လိုက်တာနဲ့ ဂိမ်းစက်အားလုံး မှန်ကန်တဲ့ ဂိမ်းနဲ့ ပွင့်လာပါတယ်။

**Docker Compose** ဆိုတာ အဲဒီ Control Panel ပါပဲ။ Service အားလုံးကို YAML File တစ်ခုထဲမှာ ရေးထားပြီး Command တစ်ကြောင်းတည်းနဲ့ အားလုံးကို စတင်နိုင်ပါတယ်။

## ၇။ Docker Compose File ရေးသားခြင်း

**compose.yaml** (သို့မဟုတ် `docker-compose.yml`)

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

ဒီ File ရဲ့ အဓိပ္ပာယ် -

- **services** – ကျွန်တော်တို့ ဂိမ်းဆိုင်ထဲက ဂိမ်းစက်တွေ။
- **game-server** – ဒီ Folder ထဲက Dockerfile ကနေ Build လုပ်ပြီး Port 5000 မှာ အသုံးပြုနိုင်တယ်။
- **db** – အမှတ်တွေ သိမ်းဖို့ Official PostgreSQL Image ကို အသုံးပြုတယ်။
- **depends_on** – Game Server မစခင် Database ကို အရင်စတင်တယ်။
- **volumes** – Memory Card ပါ။ Container ကို ဖျက်လိုက်ရင်တောင် ကစားသမားတွေရဲ့ အမှတ်တွေ မပျောက်ပါဘူး။

Game Server က Database ကို `db` ဆိုတဲ့ Hostname နဲ့ ချိတ်ဆက်ထားပါတယ်။ Docker Compose က Network တစ်ခုကို အလိုအလျောက် ဖန်တီးပေးတဲ့အတွက် Service တွေဟာ Service Name နဲ့ပဲ အချင်းချင်း ရှာတွေ့နိုင်ပါတယ်။ Multiplayer Room တစ်ခုတည်းထဲ ဝင်လာတဲ့ ကစားသမားတွေလိုပါပဲ။

## ၈။ အခြေခံ Docker Compose Command များ

```bash
# ဂိမ်းဆိုင်တစ်ခုလုံးရဲ့ "Power On" ခလုတ်ကို နှိပ်မယ်
docker compose up -d

# ဂိမ်းခွေတွေ ပြန်ထုတ်ပြီး စတင်မယ်
docker compose up -d --build

# Run နေတဲ့ Service တွေကို ကြည့်မယ်
docker compose ps

# Service အားလုံးရဲ့ Log တွေကို ကြည့်မယ်
docker compose logs -f

# အားလုံးကို ပိတ်မယ်
docker compose down

# အားလုံးကို ပိတ်ပြီး Memory Card တွေပါ ဖျက်မယ် (Data တွေ ပျက်သွားမယ်!)
docker compose down -v
```

## ၉။ Scalability – ဂိမ်းစက် ထပ်တိုးခြင်း

**ပြဿနာ**

ကိုယ့်ဂိမ်းဆိုင်မှာ လူကြိုက်များတဲ့ ဂိမ်းအတွက် စက်တစ်လုံးပဲ ရှိတယ်ဆိုပါစို့။ ကြားရက်တွေမှာ အဆင်ပြေပေမဲ့ စနေနေ့ကျရင် လူ ၁၀၀ လောက် တန်းစီစောင့်နေရပါတယ်။

ဖြေရှင်းနည်းက ရိုးရှင်းပါတယ်။ **ဂိမ်းခွေ အတူတူထည့်ထားတဲ့ စက်တွေ ထပ်တိုးလိုက်ပြီး** အဝင်ဝမှာ ဝန်ထမ်းတစ်ယောက်ထားကာ ရောက်လာတဲ့ ကစားသမားတိုင်းကို အားနေတဲ့ စက်ဆီ လွှတ်ပေးရုံပါပဲ။

Software မှာ **Scalability** ဆိုတာလည်း အဲဒီအတိုင်းပါပဲ။ User တွေ များလာတဲ့အခါ Application Copy တွေ ပိုပြီး Run ကာ Traffic ကို ခွဲဝေပေးတာ ဖြစ်ပါတယ်။

Docker မှာ Copy တိုင်းကို Image တစ်ခုတည်းကနေ စတင်တဲ့အတွက် "စက်" တိုင်းဟာ ဂိမ်းအတူတူကိုပဲ ကစားနေတာ သေချာပါတယ်။

**အဆင့် ၁ – Load Balancer ထည့်မယ် (အဝင်ဝက ဝန်ထမ်း)**

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

**အဆင့် ၂ – compose.yaml ကို ပြင်မယ်**

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
    # ဒီနေရာမှာ Host Port သတ်မှတ်မထားပါဘူး။ Nginx ကပဲ Game Server တွေနဲ့
    # ဆက်သွယ်တဲ့အတွက် Port မတိုက်ဘဲ Copy အများကြီး Run နိုင်ပါတယ်။
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

**အဆင့် ၃ – စနေ၊ တနင်္ဂနွေအတွက် စက်တိုးမယ်**

```bash
# Game Server ၁ လုံးအစား ၅ လုံး Run မယ်
docker compose up -d --scale game-server=5

# Server အသစ်တွေကို Nginx သိအောင် ပြန်စမယ်
docker compose restart nginx

# စစ်ကြည့်မယ်: game-server-1 ကနေ game-server-5 အထိ မြင်ရပါမယ်
docker compose ps
```

**အဆင့် ၄ – တနင်္လာနေ့ကျရင် စက်လျှော့မယ်**

```bash
docker compose up -d --scale game-server=2
docker compose restart nginx
```

ကစားသမားတွေက လိပ်စာတစ်ခုတည်း (Port 80) ကိုပဲ ချိတ်ဆက်ပါတယ်။ Nginx က Request တစ်ခုချင်းစီကို Game Server တစ်လုံးလုံးဆီ ခွဲပို့ပေးတဲ့အတွက် ဘယ်စက်မှ ဝန်ပိမနေပါဘူး။

**အရမ်းကြီးမားတဲ့ Scale အတွက်ကော?**

Docker Compose က Server တစ်လုံးအတွက် အလွန်ကောင်းပါတယ်။ ဂိမ်းက တကယ်ကို လူကြိုက်များလာလို့ Server အများကြီး လိုအပ်လာရင်၊ ဒါမှမဟုတ် Traffic များလာတာနဲ့ စက်တွေ **အလိုအလျောက်** တိုးပေးစေချင်ရင် **Kubernetes** ဒါမှမဟုတ် **AWS ECS** လို Tool တွေက Docker Image အတူတူကိုပဲ Computer အများကြီးပေါ်မှာ Scale လုပ်ပေးပါတယ်။

## ၁၀။ Manageability – ဂိမ်းဆိုင်ကို လွယ်လွယ်ကူကူ စီမံခြင်း

ဂိမ်းစက် ၅၀ ရှိတဲ့ ဂိမ်းဆိုင်တစ်ဆိုင်ကို စီမံနေရတယ်ဆိုပါစို့။ လုပ်ရမယ့်အလုပ်တွေက -

- စက်တိုင်းမှာ ဂိမ်းကို Version အသစ်ပြောင်းရမယ်
- Version အသစ်မှာ Bug ရှိရင် Version အဟောင်းကို ပြန်ပြောင်းရမယ်
- ဟန်းသွားတဲ့ (Freeze ဖြစ်တဲ့) စက်တွေကို ပြန်စရမယ်
- စက်တစ်လုံးက လျှပ်စစ်အားလုံး မသုံးပစ်အောင် ထိန်းရမယ်

ဒါတွေကို စက်တစ်လုံးချင်းစီ ကိုယ်တိုင်လုပ်ရမယ်ဆိုရင် အိပ်မက်ဆိုးပါပဲ။ Docker က ဒါတွေအားလုံးကို လွယ်ကူစေပါတယ်။

**ဥပမာ ၁ – စက်အားလုံးကို တစ်ပြိုင်နက် Update လုပ်ခြင်း**

Docker မပါရင် - Server တစ်ခုချင်းစီ ဝင်၊ Code အသစ် Install လုပ်၊ Library တွေ Update လုပ်ပြီး ဘာမှ မပျက်ပါစေနဲ့လို့ ဆုတောင်းရမယ်။

Docker ပါရင် - ဂိမ်းခွေ အသစ်ထုတ်ပြီး နေရာတိုင်းမှာ လဲထည့်လိုက်ရုံပါပဲ။

```yaml
  game-server:
    build: .
    image: game-server:1.1   # အရင်က 1.0
```

```bash
docker compose up -d --build
```

Game Server အားလုံး Version 1.1 နဲ့ အစားထိုးသွားပါပြီ။

**ဥပမာ ၂ – ပြဿနာတက်ရင် Version အဟောင်း ပြန်ပြောင်းခြင်း (Rollback)**

Version 1.1 မှာ Bug ပါပြီး အမှတ်တွေ မသိမ်းတော့ဘူးလား? ဂိမ်းခွေ အဟောင်းကို ပြန်ထည့်လိုက်ပါ။

```yaml
    image: game-server:1.0
```

```bash
docker compose up -d
```

Image အဟောင်း ရှိနေသေးတဲ့အတွက် Rollback လုပ်တာ စက္ကန့်ပိုင်းပဲ ကြာပါတယ်။

**ဥပမာ ၃ – စက်ဟန်းသွားရင် အလိုအလျောက် ပြန်စခြင်း**

ဂိမ်းဆိုင်မှာ ဝန်ထမ်းက ဟန်းသွားတဲ့စက်ကို ပြန်စပေးပါတယ်။ Docker ကတော့ အလိုအလျောက် လုပ်ပေးနိုင်ပါတယ်။

```yaml
  game-server:
    restart: unless-stopped
```

Game Server Crash ဖြစ်သွားရင် Docker က သူ့အလိုလို ပြန်စတင်ပေးပါတယ်။

**ဥပမာ ၄ – Health Check**

Load လုပ်နေတုန်း စက်ပေါ်ကို ကစားသမား မတင်ပါနဲ့။ Health Check က Service တစ်ခု တကယ် အသင့်ဖြစ်ပြီလားဆိုတာ Docker ကို ပြောပြပေးပါတယ်။

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

အခုဆိုရင် Database က ချိတ်ဆက်မှုတွေ လက်ခံဖို့ အသင့်ဖြစ်မှသာ Game Server စတင်ပါတော့မယ်။

**ဥပမာ ၅ – Resource ကန့်သတ်ခြင်း**

ပျက်နေတဲ့ စက်တစ်လုံးက ဂိမ်းဆိုင်တစ်ဆိုင်လုံးရဲ့ လျှပ်စစ်ကို မသုံးပစ်သင့်ပါဘူး။ Container တစ်ခုချင်းစီ သုံးနိုင်တဲ့ CPU နဲ့ Memory ကို ကန့်သတ်ထားနိုင်ပါတယ်။

```yaml
  game-server:
    deploy:
      resources:
        limits:
          cpus: "0.5"
          memory: 256M
```

**ဥပမာ ၆ – Setting တွေကို နေရာတစ်ခုတည်းမှာ ထားခြင်း**

စက်တိုင်းမှာ Setting လိုက်ပြင်နေမယ့်အစား `.env` File ထဲမှာ စုထားပါ။

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

တန်ဖိုးကို တစ်ခါပြင်လိုက်ရုံနဲ့ Service အားလုံးက Setting အသစ်ကို သုံးပါတယ်။ (တကယ့် Password တွေပါတဲ့ `.env` File ကို Git ထဲ Commit မလုပ်ပါနဲ့။)

**ဥပမာ ၇ – အားလုံးကို နေရာတစ်ခုတည်းကနေ စောင့်ကြည့်ခြင်း**

```bash
# စက်အားလုံးရဲ့ Log တွေကို Screen တစ်ခုတည်းမှာ ကြည့်မယ်
docker compose logs -f

# Game Server တွေရဲ့ Log ကိုပဲ ကြည့်မယ်
docker compose logs -f game-server

# Container တိုင်းရဲ့ CPU နဲ့ Memory အသုံးပြုမှုကို ကြည့်မယ်
docker stats
```

## ၁၁။ Docker ကို ဘယ်နေရာတွေမှာ အသုံးချနိုင်လဲ?

**၁။ Development**

အဖွဲ့သားတိုင်း Command တစ်ကြောင်းတည်းနဲ့ တူညီတဲ့ Environment ကို ရရှိတဲ့အတွက် Setup လုပ်ချိန် နာရီပိုင်းကနေ မိနစ်ပိုင်းအထိ လျော့သွားပါတယ်။

**၂။ Testing နဲ့ CI/CD**

Code Push လုပ်တိုင်း Automated Test တွေကို သန့်ရှင်းပြီး တူညီတဲ့ Container တွေထဲမှာ Run နိုင်ပါတယ်။

**၃။ Deployment**

Test လုပ်ပြီးသား Image ကိုပဲ Server တွေ ဒါမှမဟုတ် AWS (ECS, EKS), Google Cloud Run, Azure လို Cloud Platform တွေပေါ်ကို Deploy လုပ်နိုင်ပါတယ်။

**၄။ Microservices**

Application ကြီးတွေကို Service သေးသေးလေးတွေအဖြစ် ခွဲပြီး တစ်ခုချင်းစီကို သီးခြား Container တွေထဲမှာ Run နိုင်ပါတယ်။ ဂိမ်းစက်တစ်လုံးချင်းစီမှာ ကိုယ့်ဂိမ်းကိုယ် Run နေတဲ့ ဂိမ်းဆိုင်လိုပါပဲ။

**၅။ လေ့လာခြင်းနဲ့ စမ်းသပ်ခြင်း**

MySQL, Redis, Elasticsearch လို Tool တွေကို ကိုယ့် Computer ထဲ Install မလုပ်ဘဲ စမ်းသုံးကြည့်နိုင်ပါတယ်။

## ၁၂။ ကောင်းမွန်တဲ့ အလေ့အကျင့်များ (Best Practices)

- Official ဖြစ်ပြီး အရွယ်အစားသေးတဲ့ Base Image တွေကို သုံးပါ (ဥပမာ `python:3.12-slim`)။
- `.git`, `__pycache__`, `.env` လို မလိုအပ်တဲ့ File တွေကို ချန်ထားဖို့ `.dockerignore` File ထည့်ပါ။
- Password နဲ့ Secret တွေကို Dockerfile ဒါမှမဟုတ် Image ထဲမှာ တိုက်ရိုက် မထည့်ပါနဲ့။
- Database လို သိမ်းထားရမယ့် Data တွေအတွက် Volume ကို သုံးပါ။
- Container တစ်ခုမှာ အဓိက Process တစ်ခုပဲ Run ပါ။
- `latest` ကို အမြဲမသုံးဘဲ Image Version ကို သတ်မှတ်ပါ (ဥပမာ `postgres:16`)။
- Rollback လွယ်ကူအောင် ကိုယ့် Image တွေကို Version နဲ့ Tag လုပ်ပါ (`game-server:1.0`, `game-server:1.1`)။

## နိဂုံး

Docker ဆိုတာ ဂိမ်းစက်တစ်လုံးလိုပါပဲ။ ဂိမ်းခွေ (Image) ကို ထည့်လိုက်တာနဲ့ ဂိမ်း (Container) ဟာ ဘယ်နေရာမှာမဆို အတူတူ Run ပါတယ်။ Docker Compose ကတော့ ဂိမ်းစက်အားလုံးကို တစ်ပြိုင်နက် စတင်၊ စီမံပေးတဲ့ ဂိမ်းဆိုင်ရဲ့ Control Panel ဖြစ်ပါတယ်။

Docker ကို အသုံးပြုရင် ကစားသမားတွေ များလာတဲ့အခါ တူညီတဲ့ စက်တွေ ထပ်တိုးပြီး **Scale** လုပ်နိုင်သလို Update, Rollback, Restart နဲ့ Resource ကန့်သတ်ခြင်း စတာတွေကိုလည်း နေရာတစ်ခုတည်းကနေ လွယ်လွယ်ကူကူ **စီမံ** နိုင်ပါတယ်။

Web Scraper ဖြစ်ဖြစ်၊ AI Application ဖြစ်ဖြစ်၊ Game Server ဖြစ်ဖြစ် တည်ဆောက်နေသူတိုင်းအတွက် Docker ဟာ ခေတ်မီ Software Development မှာ မရှိမဖြစ် Tool တစ်ခုဖြစ်ပါတယ်။

**တစ်ကြိမ် Build လုပ်ပါ၊ ဘယ်နေရာမှာမဆို Run ပါ။**
