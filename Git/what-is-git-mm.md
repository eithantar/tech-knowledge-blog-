# Git ဆိုတာဘာလဲ? Version Control အတွက် အစပြုသူများ လမ်းညွှန်

> ဖတ်ရန်: [English](what-is-git-en.md) | **မြန်မာ**

ဒီလို File တွေ ရှိဖူးလား?

```
report.docx
report_final.docx
report_final_v2.docx
report_final_v2_REALLY_FINAL.docx
report_final_v2_REALLY_FINAL_fixed.docx
```

အခု ဒါကို **Code File ရာချီ** နဲ့ လုပ်နေရပြီး **အဖွဲ့သား ၅ ယောက်** က Project တစ်ခုတည်းကို တစ်ပြိုင်နက် ပြင်နေတယ်လို့ စဉ်းစားကြည့်ပါ။ ဘယ်သူ ဘာပြောင်းခဲ့လဲ? ဘယ် Version က အလုပ်လုပ်လဲ? တစ်ခုခု ပျက်သွားရင် ဘယ်လို ပြန်သွားမလဲ?

ဒီပြဿနာကို ဖြေရှင်းပေးတာကတော့ **Git** ဖြစ်ပါတယ်။

## ၁။ Git ဆိုတာဘာလဲ?

**Git** ဆိုတာ **Version Control System** တစ်ခု ဖြစ်ပါတယ်။ ကိုယ့် File တွေမှာ လုပ်တဲ့ ပြောင်းလဲမှုတိုင်းကို မှတ်တမ်းတင်ထားတဲ့အတွက် -

- **ဘာ** ပြောင်းလဲ၊ **ဘယ်အချိန်** ပြောင်းလဲ၊ **ဘယ်သူ** ပြောင်းလဲဆိုတာ ကြည့်နိုင်တယ်
- ဘယ်အချိန်မဆို **အရင် Version တစ်ခုခုကို ပြန်သွား** နိုင်တယ်
- အလုပ်လုပ်နေတဲ့ Version ကို **မပျက်စေဘဲ** စိတ်ကူးအသစ်တွေ စမ်းနိုင်တယ်
- တခြားသူတွေရဲ့ အလုပ်ကို ထပ်မရေးမိဘဲ Project တစ်ခုတည်းမှာ **အတူတူ အလုပ်လုပ်** နိုင်တယ်

Git ကို 2005 ခုနှစ်မှာ Linux ကို ဖန်တီးခဲ့သူ **Linus Torvalds** က ဖန်တီးခဲ့ပြီး ဒီနေ့မှာ ကမ္ဘာပေါ်က Software Team တိုင်းနီးပါးက သုံးနေကြပါတယ်။

Git ဟာ **Distributed** Version Control System ဖြစ်ပါတယ်။ Developer တိုင်းမှာ Project နဲ့ သူ့ရဲ့ History တစ်ခုလုံးကို ကိုယ့် Computer ပေါ်မှာ အပြည့်အစုံ ရှိတဲ့အတွက် Internet မရှိရင်တောင် ဆက်အလုပ်လုပ်နိုင်ပါတယ်။

## ၂။ Git နဲ့ GitHub ဘာကွာလဲ?

ဒီနာမည် နှစ်ခုကို မကြာခဏ ရောထွေးကြပါတယ်။

| | Git | GitHub |
|---|---|---|
| ဘာလဲ | ကိုယ့် Computer ပေါ် Install လုပ်ရတဲ့ **Tool** | Git Project တွေကို Online မှာ သိမ်းပေးတဲ့ **Website** |
| Offline အလုပ်လုပ်လား? | လုပ်တယ် | မလုပ်ဘူး |
| အဓိက တာဝန် | ကိုယ့် File တွေရဲ့ ပြောင်းလဲမှုကို မှတ်တမ်းတင်တယ် | Git Project တွေကို သိမ်း၊ မျှဝေပြီး အတူတူ အလုပ်လုပ်တယ် |
| ဖန်တီးသူ | Linus Torvalds (Open Source) | GitHub Inc. (Microsoft ပိုင်) |
| အစားထိုးစရာများ | – | GitLab, Bitbucket |

အလွယ်မှတ်နည်း - **Git က Camera နဲ့တူပြီး GitHub ကတော့ ကိုယ့်ဓာတ်ပုံတွေကို Upload လုပ်ပြီး မျှဝေတဲ့ Online Photo Album နဲ့ တူပါတယ်။**

## ၃။ Game Save ဥပမာ

Git ကို အလွယ်ဆုံး နားလည်နိုင်ဖို့ **Video Game မှာ Progress သိမ်းတာ** ကို စဉ်းစားကြည့်ပါ။

| Video Game | Git |
|---|---|
| Game ရဲ့ သိမ်းထားတဲ့ Progress | **Repository (Repo)** – ကိုယ့် Project နဲ့ History တစ်ခုလုံး |
| Save Point တစ်ခု ဖန်တီးတာ | **Commit** – အချိန်တစ်ခုမှာ ကိုယ့် Project ရဲ့ Snapshot |
| "Boss ကို မတိုက်ခင်" လို Save ရဲ့ နာမည် | **Commit Message** |
| Save အဟောင်းကို ပြန် Load လုပ်တာ | **Checkout / Revert** – အရင် Version ကို ပြန်သွားတာ |
| စွန့်စားတဲ့ လမ်းကြောင်း စမ်းဖို့ Save Slot သီးခြား စတာ | **Branch** |
| Save Slot နှစ်ခုက Progress ကို ပေါင်းတာ | **Merge** |
| Cloud Save | **Remote Repository** (GitHub) |
| Save ကို Cloud ပေါ် Upload လုပ်တာ | **Push** |
| နောက်ဆုံး Save ကို Cloud ကနေ Download လုပ်တာ | **Pull** |
| Save ကို Device အသစ်ဆီ Copy ကူးတာ | **Clone** |

Game မှာ ခက်ခဲတဲ့ Boss Fight မတိုင်ခင် Save လုပ်ထားပါတယ်။ ရှုံးသွားရင် Save ကို Load လုပ်ပြီး ပြန်ကြိုးစားပါတယ်။ Git ကလည်း ကိုယ့် Code အတွက် အဲဒီလို လုံခြုံမှုမျိုး ပေးပါတယ် - **စွန့်စားတာ တစ်ခုခု မစမ်းခင် Commit လုပ်ထားရင် အမြဲတမ်း ပြန်သွားလို့ရပါတယ်။**

## ၄။ Git ကို Install လုပ်ပြီး Setup လုပ်ခြင်း

**Git Install ရှိမရှိ စစ်ပါ**

```bash
git --version
```

မရှိရင် [git-scm.com](https://git-scm.com) ကနေ Download လုပ်ပါ၊ ဒါမှမဟုတ် Package Manager နဲ့ Install လုပ်ပါ (ဥပမာ Ubuntu မှာ `sudo apt install git`)။

**ကိုယ်ဘယ်သူလဲဆိုတာ Git ကို ပြောပါ** (Computer တစ်လုံးမှာ တစ်ခါပဲ လုပ်ရပါတယ်)

```bash
git config --global user.name "Your Name"
git config --global user.email "you@example.com"
git config --global init.defaultBranch main
```

ကိုယ်လုပ်တဲ့ Commit တိုင်းမှာ ကိုယ့်နာမည်နဲ့ Email ပါတဲ့အတွက် ပြောင်းလဲမှု တစ်ခုချင်းစီကို ဘယ်သူလုပ်ခဲ့လဲဆိုတာ အဖွဲ့သားတွေ သိနိုင်ပါတယ်။

## ၅။ Git ရဲ့ Area ၃ ခု

ဒါက Git မှာ အရေးအကြီးဆုံး Concept ဖြစ်ပါတယ်။ ကိုယ့် File တွေဟာ Area ၃ ခုကို ဖြတ်သန်းသွားပါတယ် -

```
┌───────────────────┐   git add   ┌───────────────────┐  git commit  ┌───────────────────┐
│ Working Directory │ ──────────► │   Staging Area    │ ───────────► │    Repository     │
│ (files you edit)  │             │ (ready to save)   │              │ (saved history)   │
└───────────────────┘             └───────────────────┘              └───────────────────┘
```

1. **Working Directory** – ကိုယ့် Project Folder ထဲမှာ မြင်ရပြီး ပြင်နေတဲ့ File တွေ။
2. **Staging Area** – နောက် Commit မှာ ထည့်ဖို့ ရွေးထားတဲ့ ပြောင်းလဲမှုတွေ။
3. **Repository** – Hidden `.git` Folder ထဲမှာ သိမ်းထားတဲ့ Commit အားလုံးရဲ့ အမြဲတမ်း History။

ဒါကို **ပို့ဖို့ သေတ္တာထုပ်တာ** နဲ့ နှိုင်းယှဉ်ကြည့်ပါ -

- **Working Directory** = ကိုယ့်အခန်းထဲမှာ ပြန့်ကျဲနေတဲ့ ပစ္စည်းအားလုံး
- **Staging Area** = ဖွင့်ထားတဲ့ သေတ္တာ။ ဘယ်ပစ္စည်းတွေ ထည့်မလဲ ကိုယ်ရွေးတယ် (`git add`)
- **Commit** = သေတ္တာကို ပိတ်ပြီး Label ကပ်တာ (`git commit -m "..."`)

Staging Area ဘာကြောင့် ရှိရတာလဲ? File ၅ ခု ပြင်ထားပေမဲ့ အဓိပ္ပာယ်ရှိတဲ့ Commit ၂ ခု သီးခြားစီ လုပ်ချင်လို့ပါ။ ဥပမာ "Login Bug ပြင်တာ" အတွက် Commit တစ်ခုနဲ့ "Homepage Design Update" အတွက် နောက်တစ်ခုပါ။

## ၆။ ကိုယ့်ရဲ့ ပထမဆုံး Repository

[Web Application ဆောင်းပါး](../Web-Application/what-is-web-application-mm.md) ထဲက Game Leaderboard Project ကို Git နဲ့ မှတ်တမ်းတင်ကြည့်ရအောင်။

```bash
# ၁။ Project Folder ဖန်တီးပြီး Git နဲ့ စမှတ်တမ်းတင်မယ်
mkdir leaderboard
cd leaderboard
git init
```

```
Initialized empty Git repository in /home/you/leaderboard/.git/
```

```bash
# ၂။ File တစ်ခု ဖန်တီးမယ်
echo "<h1>🏆 Game Leaderboard</h1>" > index.html

# ၃။ Status စစ်မယ်
git status
```

```
On branch main

No commits yet

Untracked files:
  (use "git add <file>..." to include in what will be committed)
	index.html

nothing added to commit but untracked files present (use "git add" to track)
```

Git က File ကို မြင်ပေမဲ့ မှတ်တမ်း မတင်ရသေးပါဘူး။

```bash
# ၄။ Staging Area ထဲ ထည့်မယ်
git add index.html

# ၅။ Commit လုပ်မယ် (Save Point ဖန်တီးမယ်)
git commit -m "Add leaderboard page"
```

```
[main (root-commit) a1b2c3d] Add leaderboard page
 1 file changed, 1 insertion(+)
 create mode 100644 index.html
```

ကိုယ့်ရဲ့ ပထမဆုံး Save Point လုပ်ပြီးပါပြီ! 🎉

```bash
# ၆။ History ကို ကြည့်မယ်
git log --oneline
```

```
a1b2c3d (HEAD -> main) Add leaderboard page
```

Commit တိုင်းမှာ **Commit Hash** လို့ခေါ်တဲ့ သီးသန့် ID (ဥပမာ `a1b2c3d`) ရှိပါတယ်။

## ၇။ နေ့စဉ် Workflow

Repository Setup ပြီးသွားရင် ဒီအဆင့်တွေကို တစ်နေ့လုံး ထပ်ခါထပ်ခါ လုပ်ရပါမယ် -

```bash
# File တချို့ ပြင်ပြီးရင်...

git status                 # ဘာတွေ ပြောင်းသွားလဲ?
git diff                   # ပြောင်းသွားတဲ့ Line တွေကို အတိအကျ ပြမယ်
git add index.html         # File တစ်ခုကို Stage လုပ်မယ်
git add .                  # ဒါမှမဟုတ် ပြောင်းလဲမှုအားလုံးကို Stage လုပ်မယ်
git commit -m "Add score form to leaderboard"
git log --oneline          # History ကြည့်မယ်
```

`git diff` က ဖယ်ရှားလိုက်တဲ့ Line တွေကို `-` နဲ့၊ ထည့်လိုက်တဲ့ Line တွေကို `+` နဲ့ ပြပါတယ် -

```diff
-<h1>🏆 Game Leaderboard</h1>
+<h1>🏆 Game Leaderboard</h1>
+<form id="score-form"></form>
```

## ၈။ ကောင်းမွန်တဲ့ Commit Message ရေးခြင်း

Commit Message တွေဟာ Save နာမည်တွေနဲ့ တူပါတယ်။ "Save 1, Save 2, Save 3" က အသုံးမဝင်ပါဘူး။ "နောက်ဆုံး Boss မတိုက်ခင်" ကတော့ အသုံးဝင်ပါတယ်။

| ❌ မကောင်းဘူး | ✅ ကောင်းတယ် |
|---|---|
| `update` | `Add score validation to API` |
| `fix` | `Fix leaderboard sorting for equal scores` |
| `asdfgh` | `Update README with setup instructions` |
| `changes` | `Remove unused CSS from homepage` |

အကြံပြုချက်များ -

- Verb နဲ့ စပါ: **Add**, **Fix**, **Update**, **Remove**, **Refactor**
- ပထမ Line ကို တိုတိုထားပါ (စာလုံး ၅၀ ဝန်းကျင်)
- **ဘာ** ပြောင်းလဲလဲ၊ လိုအပ်ရင် **ဘာကြောင့်** လဲ ဖော်ပြပါ
- Commit တစ်ခုချင်းစီကို Logical ပြောင်းလဲမှု **တစ်ခု** အကြောင်းပဲ ဖြစ်ပါစေ

## ၉။ .gitignore နဲ့ File တွေကို လျစ်လျူရှုခြင်း

တချို့ File တွေကို Git ထဲမှာ ဘယ်တော့မှ မသိမ်းသင့်ပါဘူး -

- Password နဲ့ API Key တွေ (`.env`)
- Install လုပ်ထားတဲ့ Library တွေ (`node_modules/`, `venv/`)
- အလိုအလျောက် ထွက်လာတဲ့ File တွေ (`__pycache__/`, `*.log`)
- Local Database နဲ့ System File တွေ (`*.db`, `.DS_Store`)

ကိုယ့် Project ထဲမှာ `.gitignore` လို့ နာမည်ပေးထားတဲ့ File တစ်ခု ဖန်တီးပါ -

```gitignore
# Secrets
.env

# Python
__pycache__/
venv/

# Node.js
node_modules/

# Databases and logs
*.db
*.log

# OS files
.DS_Store
```

အခုဆိုရင် Git က ဒီ File တွေကို လုံးဝ လျစ်လျူရှုပါတော့မယ်။

> ⚠️ **Password ဒါမှမဟုတ် API Key တွေကို ဘယ်တော့မှ Commit မလုပ်ပါနဲ့။** နောက် Commit တစ်ခုမှာ ဖျက်လိုက်ရင်တောင် History ထဲမှာ ထာဝရ ကျန်နေပြီး Repository ကို ဝင်ခွင့်ရှိသူ ဘယ်သူမဆို ရှာတွေ့နိုင်ပါတယ်။ ဖြစ်သွားခဲ့ရင် Password ဒါမှမဟုတ် Key ကို ချက်ချင်း ပြောင်းပါ။

## ၁၀။ ပြန်ပြင်ခြင်း (Undo)

လူတိုင်း အမှားလုပ်တတ်ပါတယ်။ အလုံခြုံဆုံးကနေ အစွမ်းအထက်ဆုံးအထိ ပြန်ပြင်နည်းတွေကတော့ -

| အခြေအနေ | Command |
|---|---|
| Stage မလုပ်ရသေးတဲ့ File ရဲ့ ပြောင်းလဲမှုကို ပစ်မယ် | `git restore index.html` |
| File ကို Staging Area ကနေ ဖယ်မယ် (ပြောင်းလဲမှုတော့ ထားမယ်) | `git restore --staged index.html` |
| နောက်ဆုံး Commit ရဲ့ Message ကို ပြင်မယ် (Push မလုပ်ခင်) | `git commit --amend -m "Better message"` |
| "ဆန့်ကျင်ဘက်" Commit အသစ် ဖန်တီးပြီး Commit ကို **လုံခြုံစွာ** Undo လုပ်မယ် | `git revert a1b2c3d` |
| Commit အဟောင်းကို ပြန်သွားပြီး ပိုသစ်တဲ့ Commit တွေကို **ဖျက်** မယ် | `git reset --hard a1b2c3d` ⚠️ |
| ဘာမှ မပြောင်းဘဲ Version အဟောင်းကို ကြည့်မယ် | `git switch --detach a1b2c3d` (`git switch main` နဲ့ ပြန်လာပါ) |

> ⚠️ `git reset --hard` က Commit မလုပ်ရသေးတဲ့ ပြောင်းလဲမှုတွေနဲ့ ပိုသစ်တဲ့ Commit တွေကို အပြီးတိုင် ဖျက်ပစ်ပါတယ်။ Push လုပ်ပြီး တခြားသူတွေနဲ့ မျှဝေပြီးသား Commit တွေမှာ ဘယ်တော့မှ မသုံးပါနဲ့။ `git revert` ကို အစားသုံးပါ။

**Game အခေါ်အဝေါ်နဲ့ Revert နဲ့ Reset:**

- **Revert** = အမှားကို ပြန်ပြင်တဲ့ Save Point အသစ် ထည့်တာပါ။ History မှာ ဖြစ်ခဲ့သမျှ အားလုံး ကျန်နေတုန်းပါပဲ။
- **Reset** = နောက်ပိုင်း Save Point တွေကို ဘယ်တုန်းကမှ မဖြစ်ခဲ့သလို ဖျက်ပစ်တာပါ။

## ၁၁။ Branch – သီးခြား Save Slot များ

**Branch** ဆိုတာ သီးခြား Development လမ်းကြောင်း တစ်ခု ဖြစ်ပါတယ်။ အလုပ်လုပ်နေတဲ့ Main Version ကို မထိခိုက်စေဘဲ Feature အသစ်တွေကို Branch ပေါ်မှာ စမ်းနိုင်ပါတယ်။

```
main:         A───B───────────E (merge)
                   \         /
feature/title:      C───────D
```

Game အခေါ်အဝေါ်နဲ့ဆိုရင် - `main` မှာ Save ကောင်းတစ်ခု ရှိတယ်။ စွန့်စားတဲ့ လမ်းကြောင်း မစမ်းခင် Save Slot အသစ် (`feature/title`) ဆီ Copy ကူးလိုက်တယ်။ စွန့်စားတဲ့ လမ်းကြောင်း အောင်မြင်ရင် Progress ကို Main Save ထဲ ပြန်ယူလာတယ် (**Merge**)။ မအောင်မြင်ရင် အဲဒီ Slot ကို ဖျက်ပစ်ရုံပဲ၊ Main Save က ဘာမှ မဖြစ်ပါဘူး။

```bash
# Branch အားလုံးကို ကြည့်မယ် (* က လက်ရှိ Branch)
git branch

# Branch အသစ် ဖန်တီးပြီး အဲဒီကို ပြောင်းမယ်
git switch -c feature/new-title

# ...File တွေ ပြင်ပြီး ပုံမှန်အတိုင်း Commit လုပ်မယ်...
git add .
git commit -m "Change leaderboard title"

# main ကို ပြန်သွားမယ်
git switch main

# Feature ရဲ့ ပြောင်းလဲမှုတွေကို main ထဲ ယူလာမယ်
git merge feature/new-title

# ပြီးသွားရင် Branch ကို ဖျက်မယ်
git branch -d feature/new-title
```

> `git checkout -b` နဲ့ `git checkout` ကိုလည်း တွေ့ရနိုင်ပါတယ်။ သူတို့က `git switch -c` နဲ့ `git switch` နဲ့ အလုပ်အတူတူ လုပ်ပါတယ်။ `switch` က ပိုသစ်ပြီး ပိုရှင်းလင်းတဲ့ Command ဖြစ်ပါတယ်။

**အသုံးများတဲ့ Branch နာမည်များ:**

- `main` – တည်ငြိမ်ပြီး အလုပ်လုပ်နေတဲ့ Version
- `feature/...` – Feature အသစ်၊ ဥပမာ `feature/login-page`
- `fix/...` – Bug ပြင်ဆင်မှု၊ ဥပမာ `fix/score-sorting`

## ၁၂။ Merge Conflict

တစ်ခါတလေ Branch နှစ်ခုက File တစ်ခုတည်းရဲ့ **Line တစ်ခုတည်း** ကို မတူတဲ့ပုံစံနဲ့ ပြောင်းထားတတ်ပါတယ်။ ဘယ် Version ကို ထားရမလဲ Git က မဆုံးဖြတ်နိုင်တဲ့အတွက် ကိုယ့်ကို မေးပါတယ်။ ဒါကို **Merge Conflict** လို့ ခေါ်ပါတယ်။

`git merge` Run လိုက်တဲ့အခါ Git က ဒီလို ပြောပါတယ် -

```
Auto-merging index.html
CONFLICT (content): Merge conflict in index.html
Automatic merge failed; fix conflicts and then commit the result.
```

Git က File ထဲမှာ Conflict ကို အမှတ်အသား လုပ်ထားပါတယ် -

```html
<<<<<<< HEAD
<h1>🏆 Top Players</h1>
=======
<h1>🏆 Hall of Fame</h1>
>>>>>>> feature/new-title
```

- `<<<<<<< HEAD` နဲ့ `=======` ကြားက **လက်ရှိ Branch** ရဲ့ Version ဖြစ်ပါတယ်။
- `=======` နဲ့ `>>>>>>>` ကြားက **Merge လုပ်နေတဲ့ Branch** ရဲ့ Version ဖြစ်ပါတယ်။

**ဖြေရှင်းနည်း:**

1. ကိုယ်လိုချင်တဲ့ Version ကို ထားခဲ့ပြီး (ဒါမှမဟုတ် နှစ်ခုပေါင်းပြီး) အမှတ်အသား Line တွေကို ဖျက်ပါ -

   ```html
   <h1>🏆 Hall of Fame</h1>
   ```

2. ရလဒ်ကို Stage လုပ်ပြီး Commit လုပ်ပါ -

   ```bash
   git add index.html
   git commit -m "Merge new title from feature branch"
   ```

Conflict တွေကို မကြောက်ပါနဲ့။ Team Project တွေမှာ ပုံမှန်ပါပဲ။ **VS Code** လို Code Editor တွေက "Accept Current"၊ "Accept Incoming" လို Button တွေနဲ့ Conflict တွေကို ပြပေးလို့ ပိုလွယ်ပါတယ်။

## ၁၃။ GitHub နဲ့ အလုပ်လုပ်ခြင်း (Remote Repository)

အခုထိ အားလုံးက ကိုယ့် Computer ပေါ်မှာပဲ ရှိပါသေးတယ်။ **Remote** ဆိုတာ GitHub လို Server ပေါ်က ကိုယ့် Repository ရဲ့ Copy ဖြစ်ပြီး Cloud Save လို အလုပ်လုပ်ပါတယ်။

**ရှိပြီးသား Project ကို GitHub ပေါ် Upload လုပ်ခြင်း**

1. [github.com](https://github.com) မှာ Repository အသစ် (အလွတ်) တစ်ခု ဖန်တီးပါ။
2. ချိတ်ဆက်ပြီး Push လုပ်ပါ -

```bash
git remote add origin https://github.com/your-username/leaderboard.git
git push -u origin main
```

`origin` က ကိုယ့်ရဲ့ အဓိက Remote အတွက် ပုံမှန်သုံးတဲ့ နာမည်ပါ။ `-u` က မှတ်ထားပေးတဲ့အတွက် နောက်တစ်ခါ `git push` လို့ပဲ ရိုက်ရုံပါပဲ။

**ရှိပြီးသား Project ကို Download လုပ်ခြင်း**

```bash
git clone https://github.com/your-username/leaderboard.git
```

**Sync ဖြစ်နေအောင် ထားခြင်း**

```bash
git pull     # GitHub ကနေ နောက်ဆုံး ပြောင်းလဲမှုတွေကို Download လုပ်ပြီး Merge လုပ်မယ်
git push     # ကိုယ့် Commit အသစ်တွေကို GitHub ပေါ် Upload လုပ်မယ်
git fetch    # ပြောင်းလဲမှုတွေကို Download လုပ်ပေမဲ့ Merge မလုပ်သေးဘူး (အရင် Review လုပ်ဖို့)
```

**ရွှေစည်းမျဉ်း:** အလုပ် မစခင် `git pull` လုပ်ပါ၊ ပြီးရင် `git push` လုပ်ပါ။ မဟုတ်ရင် အဖွဲ့သားတွေရဲ့ အလုပ်နဲ့ Conflict ဖြစ်နိုင်ပါတယ်။

## ၁၄။ GitHub ကို Sign In လုပ်ခြင်း

GitHub က `git push` အတွက် Account Password ကို လက်မခံတော့ပါဘူး။ ဒီလို Error မျိုး တွေ့ရရင် -

```
fatal: could not read Username for 'https://github.com'
```

ဒါမှမဟုတ် `Authentication failed` ဆိုရင် အောက်ပါ နည်းလမ်း ၂ ခုထဲက တစ်ခုကို Setup လုပ်ဖို့ လိုပါတယ်။

**နည်းလမ်း ၁: Personal Access Token နဲ့ HTTPS**

1. GitHub မှာ **Settings → Developer settings → Personal access tokens** ကို သွားပြီး `repo` Access ပါတဲ့ Token တစ်ခု ဖန်တီးပါ။
2. ကိုယ့် Login ကို မှတ်ထားဖို့ Git ကို ပြောပါ -

   ```bash
   git config --global credential.helper store
   ```

3. `git push` ကို Run ပါ။ GitHub **Username** ထည့်ပြီး Password နေရာမှာ **Token** ကို Paste လုပ်ပါ။

Git က သိမ်းထားတဲ့အတွက် တစ်ခါပဲ လုပ်ရပါတယ်။ (`store` Helper က Token ကို ကိုယ့် Home Folder ထဲက Plain Text File မှာ သိမ်းပါတယ်။ မျှဝေသုံးတဲ့ Computer မှာဆိုရင် Git Credential Manager ရဲ့ `manager` လို ပိုလုံခြုံတဲ့ Helper ကို သုံးပါ။)

**နည်းလမ်း ၂: SSH Key**

```bash
# ၁။ Key တစ်ခု ဖန်တီးမယ် (Default တွေ လက်ခံဖို့ Enter နှိပ်ပါ)
ssh-keygen -t ed25519 -C "you@example.com"

# ၂။ Public Key ကို ပြပြီး Copy ကူးမယ်
cat ~/.ssh/id_ed25519.pub
```

3. GitHub မှာ **Settings → SSH and GPG keys → New SSH key** ကို သွားပြီး Paste လုပ်ပါ။
4. Connection ကို Test လုပ်ပြီး ကိုယ့် Project ကို SSH ကို ပြောင်းပါ -

```bash
ssh -T git@github.com
git remote set-url origin git@github.com:your-username/leaderboard.git
```

ဒါပြီးရင် `git push` နဲ့ `git pull` က Password မမေးတော့ဘဲ အလုပ်လုပ်ပါပြီ။

## ၁၅။ အတူတူ အလုပ်လုပ်ခြင်း: Pull Request

Team တစ်ခုမှာ လူတွေက `main` ကို တိုက်ရိုက် Push မလုပ်လေ့ ရှိပါဘူး။ အဲဒီအစား -

1. Branch တစ်ခု ဖန်တီးပါ: `git switch -c feature/add-search`
2. ကိုယ့်အလုပ်ကို Commit လုပ်ပြီး Branch ကို Push လုပ်ပါ: `git push -u origin feature/add-search`
3. GitHub ပေါ်မှာ ကိုယ့် Branch ကို `main` ထဲ Merge လုပ်ပေးဖို့ **Pull Request (PR)** ဖွင့်ပါ။
4. အဖွဲ့သားတွေက ကိုယ့် Code ကို **Review** လုပ်ပြီး Comment ပေးပါတယ်။
5. Automated Test တွေ Run ပါတယ် ([Web Development ဆောင်းပါး](../Web-Development/what-is-web-development-mm.md) ထဲက CI/CD ကို ကြည့်ပါ)။
6. အားလုံး Approve ဖြစ်သွားရင် PR ကို **Merge** လုပ်ပါတယ်။

**Fork:** တခြားသူရဲ့ Project (ဥပမာ Open-source Library) ကို ပါဝင်ကူညီချင်ရင် အရင်ဆုံး **Fork** လုပ်ပါတယ်။ ဒါက GitHub ပေါ်မှာ ကိုယ်ပိုင် Copy တစ်ခု ဖန်တီးပေးပါတယ်။ ပြီးရင် ကိုယ့် Fork ကနေ မူရင်း Project ဆီ Pull Request ဖွင့်ပါတယ်။

## ၁၆။ Merge နဲ့ Rebase

Branch တစ်ခုက ပြောင်းလဲမှုတွေကို နောက် Branch တစ်ခုထဲ ယူလာဖို့ နည်းလမ်း ၂ ခု ရှိပါတယ်။

| | Merge | Rebase |
|---|---|---|
| ဘာလုပ်လဲ | "Merge Commit" အသစ်နဲ့ Branch တွေကို ပေါင်းတယ် | ကိုယ့် Commit တွေကို တခြား Branch ရဲ့ အပေါ်မှာ ပြန်ထပ်တယ် |
| History | Branch တွေ အပါအဝင် ဖြစ်ခဲ့သမျှကို အတိအကျ ပြတယ် | သန့်ရှင်းပြီး တန်းတဲ့ History |
| လုံခြုံမှု | မျှဝေထားတဲ့ Branch တွေအတွက် လုံခြုံတယ် | တခြားသူတွေ သုံးနေပြီးသား Commit တွေကို Rebase မလုပ်ပါနဲ့ |
| Command | `git merge main` | `git rebase main` |

**အစပြုသူတွေက `merge` ကို သုံးသင့်ပါတယ်။** Git နဲ့ ရင်းနှီးသွားမှ `rebase` ကို လေ့လာပါ။

## ၁၇။ သိထားသင့်တဲ့ အသုံးဝင် Command များ

```bash
# မပြီးသေးတဲ့ အလုပ်ကို Commit မလုပ်ဘဲ ယာယီ သိမ်းမယ်
git stash
git stash pop          # ပြန်ယူမယ်

# History ကို Graph အနေနဲ့ ကြည့်မယ်
git log --oneline --graph --all

# File တစ်ခုရဲ့ Line တစ်ခုချင်းစီကို နောက်ဆုံး ဘယ်သူ ပြင်ခဲ့လဲ ကြည့်မယ်
git blame index.html

# Release Version ကို အမှတ်အသား လုပ်မယ်
git tag v1.0
git push origin v1.0

# Commit တစ်ခုရဲ့ အသေးစိတ်ကို ပြမယ်
git show a1b2c3d
```

`git stash` က Level တစ်ခုရဲ့ အလယ်မှာ Save မလုပ်ဘဲ Game ကို Pause လုပ်ထားတာနဲ့ တူပါတယ်။ အရေးပေါ် တစ်ခုခုကို ပြောင်းလုပ်ပြီး ပြီးရင် ကိုယ်ရောက်နေခဲ့တဲ့ နေရာကို အတိအကျ ပြန်လာနိုင်ပါတယ်။

## ၁၈။ ကောင်းမွန်တဲ့ အလေ့အကျင့်များ (Best Practices)

- **ခဏခဏ Commit လုပ်ပါ** – သေးငယ်ပြီး မကြာခဏ လုပ်တဲ့ Commit တွေက နားလည်ရ၊ Undo လုပ်ရ ပိုလွယ်ပါတယ်။
- **Commit တစ်ခု = Logical ပြောင်းလဲမှု တစ်ခု** – Bug Fix နဲ့ Feature အသစ်ကို Commit တစ်ခုထဲ မရောပါနဲ့။
- **ရှင်းလင်းတဲ့ Commit Message ရေးပါ** – နောင်တချိန် ကိုယ့်ကိုယ်ကိုယ် ကျေးဇူးတင်ပါလိမ့်မယ်။
- **Push မလုပ်ခင် Pull လုပ်ပါ** – ကိုယ့် Team နဲ့ Sync ဖြစ်နေပါစေ။
- Feature အသစ် ဒါမှမဟုတ် Fix တိုင်းအတွက် **Branch သုံးပါ**။ `main` ကို အလုပ်လုပ်နေအောင် ထားပါ။
- **Secret တွေကို ဘယ်တော့မှ Commit မလုပ်ပါနဲ့** – `.gitignore` နဲ့ `.env` File တွေကို သုံးပါ။
- **မျှဝေထားတဲ့ History ကို ပြန်မရေးပါနဲ့** – တခြားသူတွေ သုံးနေတဲ့ Branch တွေမှာ `reset --hard` နဲ့ `rebase` ကို ရှောင်ပါ။
- **Commit မလုပ်ခင် ကိုယ့်ပြောင်းလဲမှုတွေကို Review လုပ်ပါ** – `git status` နဲ့ `git diff` ကို အရင် Run ပါ။

## Git Cheat Sheet

| Command | ဘာလုပ်လဲ |
|---|---|
| `git init` | Project ကို စမှတ်တမ်းတင်မယ် |
| `git clone <url>` | Project ကို Download လုပ်မယ် |
| `git status` | ဘာပြောင်းလဲလဲ ပြမယ် |
| `git diff` | Line ပြောင်းလဲမှုတွေကို အတိအကျ ပြမယ် |
| `git add <file>` / `git add .` | ပြောင်းလဲမှုတွေကို Stage လုပ်မယ် |
| `git commit -m "message"` | Snapshot တစ်ခု သိမ်းမယ် |
| `git log --oneline` | History ပြမယ် |
| `git switch -c <branch>` | Branch ဖန်တီးပြီး ပြောင်းမယ် |
| `git switch <branch>` | Branch ပြောင်းမယ် |
| `git merge <branch>` | Branch တစ်ခုကို လက်ရှိ Branch ထဲ Merge လုပ်မယ် |
| `git pull` | Remote ကနေ နောက်ဆုံး ပြောင်းလဲမှုတွေ ယူမယ် |
| `git push` | ကိုယ့် Commit တွေကို Remote ပေါ် Upload လုပ်မယ် |
| `git restore <file>` | Stage မလုပ်ရသေးတဲ့ ပြောင်းလဲမှုတွေကို ပစ်မယ် |
| `git revert <commit>` | Commit တစ်ခုကို လုံခြုံစွာ Undo လုပ်မယ် |
| `git stash` / `git stash pop` | အလုပ်ကို ယာယီ သိမ်းပြီး ပြန်ယူမယ် |

## နိဂုံး

Git ဆိုတာ ကိုယ့် Code အတွက် Save System တစ်ခုနဲ့ တူပါတယ်။ **Commit** တိုင်းက Save Point တစ်ခု၊ **Branch** တိုင်းက စိတ်ကူးအသစ်တွေ စမ်းဖို့ သီးခြား Save Slot တစ်ခု ဖြစ်ပြီး **GitHub** ကတော့ ကိုယ့်အလုပ်ကို Backup လုပ်ပြီး Team နဲ့ မျှဝေနိုင်တဲ့ Cloud Save ဖြစ်ပါတယ်။

Command အားလုံးကို တစ်ပြိုင်နက် လေ့လာစရာ မလိုပါဘူး။ `init`, `status`, `add`, `commit`, `log`, `push` နဲ့ `pull` ကနေ စပါ။ ပြီးရင် Branch တွေ ထပ်ထည့်ပြီး ကျန်တာတွေကို လိုအပ်သလို လေ့လာပါ။

**Git ရှိရင် စမ်းသပ်ရမှာ မကြောက်တော့ပါဘူး၊ ဘာလို့လဲဆိုတော့ နောက်ဆုံး Save ကို အမြဲတမ်း ပြန် Load လုပ်လို့ရလို့ပါ။**
