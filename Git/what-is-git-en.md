# What Is Git? A Beginner's Guide to Version Control

> Read in: **English** | [မြန်မာ](what-is-git-mm.md)

Have you ever had files like these?

```
report.docx
report_final.docx
report_final_v2.docx
report_final_v2_REALLY_FINAL.docx
report_final_v2_REALLY_FINAL_fixed.docx
```

Now imagine doing that with **hundreds of code files**, while **five teammates** edit the same project at the same time. Who changed what? Which version works? How do you go back when something breaks?

This is the problem that **Git** solves.

## 1. What Is Git?

**Git** is a **version control system**. It records every change you make to your files, so you can:

- See **what** changed, **when**, and **who** changed it
- Go **back to any earlier version** at any time
- Try new ideas **without breaking** the working version
- **Work together** with other people on the same project without overwriting each other's work

Git was created in 2005 by **Linus Torvalds**, the creator of Linux, and today it is used by almost every software team in the world.

Git is a **distributed** version control system. Every developer has a full copy of the project and its entire history on their own computer, so you can keep working even without the Internet.

## 2. Git vs GitHub

These two names are often confused.

| | Git | GitHub |
|---|---|---|
| What it is | A **tool** installed on your computer | A **website** that hosts Git projects online |
| Works offline? | Yes | No |
| Main job | Track changes to your files | Store, share, and collaborate on Git projects |
| Made by | Linus Torvalds (open source) | GitHub Inc. (owned by Microsoft) |
| Alternatives | – | GitLab, Bitbucket |

A simple way to remember: **Git is like a camera, and GitHub is like an online photo album** where you upload and share your photos.

## 3. The Game Save Example

The easiest way to understand Git is to think about **saving progress in a video game**.

| Video Game | Git |
|---|---|
| Your game's saved progress | **Repository (repo)** – Your project and its full history |
| Creating a save point | **Commit** – A snapshot of your project at one moment |
| The name of the save, like "Before the boss fight" | **Commit message** |
| Loading an old save | **Checkout / Revert** – Going back to an earlier version |
| Starting a separate save slot to try a risky path | **Branch** |
| Combining progress from two save slots | **Merge** |
| Cloud save | **Remote repository** (GitHub) |
| Uploading your save to the cloud | **Push** |
| Downloading the latest save from the cloud | **Pull** |
| Copying a save to a new device | **Clone** |

In a game, you save before a difficult boss fight. If you lose, you load the save and try again. Git gives you the same safety for your code: **commit before trying something risky, and you can always go back.**

## 4. Installing and Setting Up Git

**Check if Git is installed**

```bash
git --version
```

If not, download it from [git-scm.com](https://git-scm.com), or install it with your package manager (for example, `sudo apt install git` on Ubuntu).

**Tell Git who you are** (do this once per computer)

```bash
git config --global user.name "Your Name"
git config --global user.email "you@example.com"
git config --global init.defaultBranch main
```

Your name and email are attached to every commit you make, so teammates know who made each change.

## 5. The Three Areas of Git

This is the most important concept in Git. Your files move through three areas:

```
┌───────────────────┐   git add   ┌───────────────────┐  git commit  ┌───────────────────┐
│ Working Directory │ ──────────► │   Staging Area    │ ───────────► │    Repository     │
│ (files you edit)  │             │ (ready to save)   │              │ (saved history)   │
└───────────────────┘             └───────────────────┘              └───────────────────┘
```

1. **Working Directory** – The files you see and edit in your project folder.
2. **Staging Area** – The changes you've selected to include in the next commit.
3. **Repository** – The permanent history of all your commits, stored in a hidden `.git` folder.

Think of it like **packing a box to ship**:

- **Working directory** = All the items lying around your room
- **Staging area** = The open box. You choose which items to put in it (`git add`)
- **Commit** = Sealing the box and labeling it (`git commit -m "..."`)

Why have a staging area? Because you might change five files but want to save them as two separate, meaningful commits. For example, one commit for "Fix login bug" and another for "Update homepage design."

## 6. Your First Repository

Let's track the game leaderboard project from the [Web Application article](../Web-Application/what-is-web-application-en.md).

```bash
# 1. Create a project folder and start tracking it with Git
mkdir leaderboard
cd leaderboard
git init
```

```
Initialized empty Git repository in /home/you/leaderboard/.git/
```

```bash
# 2. Create a file
echo "<h1>🏆 Game Leaderboard</h1>" > index.html

# 3. Check the status
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

Git sees the file but isn't tracking it yet.

```bash
# 4. Add it to the staging area
git add index.html

# 5. Commit (create a save point)
git commit -m "Add leaderboard page"
```

```
[main (root-commit) a1b2c3d] Add leaderboard page
 1 file changed, 1 insertion(+)
 create mode 100644 index.html
```

You've made your first save point! 🎉

```bash
# 6. See the history
git log --oneline
```

```
a1b2c3d (HEAD -> main) Add leaderboard page
```

Each commit has a unique ID (like `a1b2c3d`), called a **commit hash**.

## 7. The Everyday Workflow

Once your repository is set up, you'll repeat these steps all day:

```bash
# Edit some files... then:

git status                 # What changed?
git diff                   # Show the exact lines that changed
git add index.html         # Stage one file
git add .                  # Or stage all changes
git commit -m "Add score form to leaderboard"
git log --oneline          # View history
```

`git diff` shows lines that were removed with `-` and lines that were added with `+`:

```diff
-<h1>🏆 Game Leaderboard</h1>
+<h1>🏆 Game Leaderboard</h1>
+<form id="score-form"></form>
```

## 8. Writing Good Commit Messages

Your commit messages are like save names. "Save 1, Save 2, Save 3" is useless. "Before the final boss" is helpful.

| ❌ Bad | ✅ Good |
|---|---|
| `update` | `Add score validation to API` |
| `fix` | `Fix leaderboard sorting for equal scores` |
| `asdfgh` | `Update README with setup instructions` |
| `changes` | `Remove unused CSS from homepage` |

Tips:

- Start with a verb: **Add**, **Fix**, **Update**, **Remove**, **Refactor**
- Keep the first line short (around 50 characters)
- Describe **what** changed and, if needed, **why**
- Make each commit about **one** logical change

## 9. Ignoring Files With .gitignore

Some files should never be saved in Git:

- Passwords and API keys (`.env`)
- Installed libraries (`node_modules/`, `venv/`)
- Generated files (`__pycache__/`, `*.log`)
- Local databases and system files (`*.db`, `.DS_Store`)

Create a file named `.gitignore` in your project:

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

Git will now ignore these files completely.

> ⚠️ **Never commit passwords or API keys.** Even if you delete them in a later commit, they stay in the history forever, and anyone with access to the repository can find them. If it happens, change the password or key immediately.

## 10. Undoing Things

Everyone makes mistakes. Here's how to undo them, from safest to most powerful:

| Situation | Command |
|---|---|
| Throw away changes to a file you haven't staged | `git restore index.html` |
| Remove a file from the staging area (keep the changes) | `git restore --staged index.html` |
| Fix the message of the last commit (before pushing) | `git commit --amend -m "Better message"` |
| Undo a commit **safely**, by creating a new "opposite" commit | `git revert a1b2c3d` |
| Move back to an old commit and **delete** newer commits | `git reset --hard a1b2c3d` ⚠️ |
| Look at an old version without changing anything | `git switch --detach a1b2c3d` (return with `git switch main`) |

> ⚠️ `git reset --hard` permanently deletes uncommitted changes and newer commits. Never use it on commits you've already pushed and shared with others. Use `git revert` instead.

**Revert vs Reset in game terms:**

- **Revert** = You add a new save point that undoes the mistake. The history still shows everything that happened.
- **Reset** = You delete the later save points as if they never happened.

## 11. Branches – Separate Save Slots

A **branch** is an independent line of development. You can try new features on a branch without affecting the main, working version.

```
main:         A───B───────────E (merge)
                   \         /
feature/title:      C───────D
```

In game terms: you have a good save on `main`. Before trying a risky path, you copy it to a new save slot (`feature/title`). If the risky path works, you bring the progress back into your main save (**merge**). If it fails, you just delete that slot, and your main save is untouched.

```bash
# See all branches (* marks the current one)
git branch

# Create a new branch and switch to it
git switch -c feature/new-title

# ...edit files, then commit as usual...
git add .
git commit -m "Change leaderboard title"

# Go back to main
git switch main

# Bring the feature's changes into main
git merge feature/new-title

# Delete the branch when you're done
git branch -d feature/new-title
```

> You may also see `git checkout -b` and `git checkout`. They do the same thing as `git switch -c` and `git switch`. `switch` is the newer, clearer command.

**Common branch names:**

- `main` – The stable, working version
- `feature/...` – A new feature, e.g., `feature/login-page`
- `fix/...` – A bug fix, e.g., `fix/score-sorting`

## 12. Merge Conflicts

Sometimes two branches change **the same line** of the same file in different ways. Git can't decide which version to keep, so it asks you. This is called a **merge conflict**.

When you run `git merge`, Git tells you:

```
Auto-merging index.html
CONFLICT (content): Merge conflict in index.html
Automatic merge failed; fix conflicts and then commit the result.
```

Git marks the conflict inside the file:

```html
<<<<<<< HEAD
<h1>🏆 Top Players</h1>
=======
<h1>🏆 Hall of Fame</h1>
>>>>>>> feature/new-title
```

- Between `<<<<<<< HEAD` and `=======` is the version on your **current branch**.
- Between `=======` and `>>>>>>>` is the version from the **branch you're merging**.

**To resolve it:**

1. Edit the file to keep the version you want (or combine both), and delete the marker lines:

   ```html
   <h1>🏆 Hall of Fame</h1>
   ```

2. Stage and commit the result:

   ```bash
   git add index.html
   git commit -m "Merge new title from feature branch"
   ```

Don't be scared of conflicts. They're normal in team projects. Code editors like **VS Code** show conflicts with buttons like "Accept Current" and "Accept Incoming" to make this easier.

## 13. Working With GitHub (Remote Repositories)

So far, everything has been on your own computer. A **remote** is a copy of your repository on a server like GitHub, which works as a cloud save.

**Upload an existing project to GitHub**

1. Create a new, empty repository on [github.com](https://github.com).
2. Connect it and push:

```bash
git remote add origin https://github.com/your-username/leaderboard.git
git push -u origin main
```

`origin` is the usual name for your main remote. `-u` remembers it, so next time you can just type `git push`.

**Download an existing project**

```bash
git clone https://github.com/your-username/leaderboard.git
```

**Stay in sync**

```bash
git pull     # Download and merge the latest changes from GitHub
git push     # Upload your new commits to GitHub
git fetch    # Download changes but don't merge them yet (to review first)
```

**Golden rule:** `git pull` before you start working, and `git push` when you finish. Otherwise you may get conflicts with your teammates' work.

## 14. Signing In to GitHub

GitHub no longer accepts your account password for `git push`. If you see an error like this:

```
fatal: could not read Username for 'https://github.com'
```

or `Authentication failed`, you need to set up one of these two methods.

**Option 1: HTTPS with a Personal Access Token**

1. On GitHub, go to **Settings → Developer settings → Personal access tokens**, and create a token with `repo` access.
2. Tell Git to remember your login:

   ```bash
   git config --global credential.helper store
   ```

3. Run `git push`. Enter your GitHub **username**, and paste the **token** as the password.

Git saves it, so you only do this once. (The `store` helper saves the token in a plain text file in your home folder. On a shared computer, use a more secure helper such as `manager` from Git Credential Manager.)

**Option 2: SSH Keys**

```bash
# 1. Create a key (press Enter to accept the defaults)
ssh-keygen -t ed25519 -C "you@example.com"

# 2. Show the public key, then copy it
cat ~/.ssh/id_ed25519.pub
```

3. On GitHub, go to **Settings → SSH and GPG keys → New SSH key**, and paste it.
4. Test the connection and switch your project to SSH:

```bash
ssh -T git@github.com
git remote set-url origin git@github.com:your-username/leaderboard.git
```

After this, `git push` and `git pull` work without asking for a password.

## 15. Collaborating: Pull Requests

On a team, people usually don't push directly to `main`. Instead:

1. Create a branch: `git switch -c feature/add-search`
2. Commit your work and push the branch: `git push -u origin feature/add-search`
3. On GitHub, open a **Pull Request (PR)** to ask for your branch to be merged into `main`.
4. Teammates **review** your code and leave comments.
5. Automated tests run (see CI/CD in the [Web Development article](../Web-Development/what-is-web-development-en.md)).
6. When everything is approved, the PR is **merged**.

**Fork:** To contribute to someone else's project (like an open-source library), you first **fork** it, which makes your own copy on GitHub. Then you open a Pull Request from your fork to the original project.

## 16. Merge vs Rebase

There are two ways to bring changes from one branch into another.

| | Merge | Rebase |
|---|---|---|
| What it does | Combines branches with a new "merge commit" | Replays your commits on top of the other branch |
| History | Shows exactly what happened, including branches | Clean, straight-line history |
| Safety | Safe for shared branches | Don't rebase commits others are already using |
| Command | `git merge main` | `git rebase main` |

**Beginners should use `merge`.** Learn `rebase` later, once you're comfortable with Git.

## 17. Useful Commands to Know

```bash
# Save unfinished work temporarily, without committing
git stash
git stash pop          # Bring it back

# See history as a graph
git log --oneline --graph --all

# See who last changed each line of a file
git blame index.html

# Mark a release version
git tag v1.0
git push origin v1.0

# Show details of one commit
git show a1b2c3d
```

`git stash` is like pausing a game in the middle of a level without saving. You can switch to something urgent, then come back exactly where you were.

## 18. Best Practices

- **Commit often** – Small, frequent commits are easier to understand and undo.
- **One commit = one logical change** – Don't mix a bug fix and a new feature in one commit.
- **Write clear commit messages** – Your future self will thank you.
- **Pull before you push** – Stay in sync with your team.
- **Use branches** for every new feature or fix. Keep `main` working.
- **Never commit secrets** – Use `.gitignore` and `.env` files.
- **Don't rewrite shared history** – Avoid `reset --hard` and `rebase` on branches others use.
- **Review your changes before committing** – Run `git status` and `git diff` first.

## Git Cheat Sheet

| Command | What It Does |
|---|---|
| `git init` | Start tracking a project |
| `git clone <url>` | Download a project |
| `git status` | Show what changed |
| `git diff` | Show exact line changes |
| `git add <file>` / `git add .` | Stage changes |
| `git commit -m "message"` | Save a snapshot |
| `git log --oneline` | Show history |
| `git switch -c <branch>` | Create and switch to a branch |
| `git switch <branch>` | Switch branches |
| `git merge <branch>` | Merge a branch into the current one |
| `git pull` | Get the latest changes from the remote |
| `git push` | Upload your commits to the remote |
| `git restore <file>` | Discard unstaged changes |
| `git revert <commit>` | Safely undo a commit |
| `git stash` / `git stash pop` | Temporarily save and restore work |

## Conclusion

Git is like a save system for your code. Every **commit** is a save point, every **branch** is a separate save slot for trying new ideas, and **GitHub** is the cloud save that lets you back up your work and share it with your team.

You don't need to learn every command at once. Start with `init`, `status`, `add`, `commit`, `log`, `push`, and `pull`. Then add branches, and learn the rest as you need it.

**With Git, you're never afraid to experiment, because you can always load your last save.**
