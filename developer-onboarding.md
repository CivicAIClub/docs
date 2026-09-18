# Civic AI Club — Developer Onboarding Guide

Welcome to the Civic AI Club dev team. This guide covers everything you need to get set up, understand how we work together, and start contributing code.

Read the whole thing before you start. It'll take 10 minutes and save you hours of confusion later.

> **Before you do anything else:** every project repo has Cursor rules committed in `.cursor/rules/`. When you open your repo in Cursor, the AI already knows our workflow, your project's architecture, and the rules below. You can still paste this guide into Cursor's chat (or Claude, ChatGPT, any assistant) and say: "This is my team's onboarding guide. Walk me through the setup and help me with Git commands as I go." Let the AI be your copilot; don't try to memorize the commands.
>
> If you pasted an older version of our rules into Cursor's **User Rules** or settings back when everything was one repo, delete it now. It describes a folder layout that no longer exists.

---

## What's Been Set Up For You

Cayden has created a GitHub organization called **CivicAIClub**. **Each project has its own repository.** You clone only the repo for your case; you never need the others' code on your computer.

| Case | Repository | What it is | Client | Team |
|---|---|---|---|---|
| A | [case-a-clc-workflow](https://github.com/CivicAIClub/case-a-clc-workflow) | AutoPlanner: Canvas assignments → per-student Google Docs planner (Python/FastAPI + Apps Script + static UI) | CLC Supported Study Hall | Luke Ryan, Jack Weinberg |
| B | [case-b-music-studio](https://github.com/CivicAIClub/case-b-music-studio) | Music Studio portal: profiles, scheduling, Drive resources, recaps (Vite/React + Apps Script) | Mr. O'Neal | Serena Xu, JT Gannon |
| C | [case-c-dei-timeline](https://github.com/CivicAIClub/case-c-dei-timeline) | Pomfret Voices: DEI interactive timeline and archive (Next.js) | Dr. McCarter | Zahir Williams, Keke Li |
| D | [case-d-roster-export](https://github.com/CivicAIClub/case-d-roster-export) | Canvas roster → Google Docs comment templates (Apps Script) | Mr. Ring | James Lake, Magnus Songhurst, Jay Youm |
| — | [docs](https://github.com/CivicAIClub/docs) | This guide and other club-wide docs | — | everyone |

Inside each repo, the layout is whatever that project needs (read its `README.md`). What every repo has in common:

```
your-repo/
├── README.md              ← what the project is, client, exact setup steps
├── .cursor/rules/         ← Cursor rules for this repo (already committed; nothing to paste)
├── .github/               ← pull request template, CODEOWNERS, CI workflows
├── .gitignore             ← keeps secrets and build junk out of Git
└── (the project's code)
```

The old single repository, `Civic-AI-Github-Repository`, is **archived**. Its history is preserved, but nothing new goes there. If you still have it cloned, you can delete that folder.

---

## What is Git and GitHub?

If you've never used Git before, here's the short version.

**Git** is a tool that tracks every change anyone makes to the code. Think of it like Google Docs version history, but way more powerful. If something breaks, you can always go back to a working version. Git runs on your own computer.

**GitHub** is the website where our code lives online. It's like Google Drive for code. Everyone pushes their work up to GitHub so the whole team can see it and collaborate. GitHub is the cloud copy; your computer has the local copy.

**Key vocabulary you'll need:**

| Term | What it means |
|------|---------------|
| **Repository (repo)** | A project folder that Git tracks. Each case has its own, named `case-<letter>-<name>`. It lives on GitHub, and you have a copy on your computer. |
| **Clone** | Downloading a repo from GitHub to your computer for the first time. You only do this once per repo. After that, you use `pull` to get updates. |
| **Branch** | A separate version of the code where you can make changes without affecting anyone else. Like making a copy of a Google Doc to edit, then merging your edits back into the original when you're done. |
| **Commit** | Saving a snapshot of your changes with a short description of what you did. This is a local save; it doesn't go to GitHub until you push. |
| **Push** | Uploading your commits from your computer to GitHub. This is what makes your work visible to everyone else. |
| **Pull** | Downloading the latest changes from GitHub to your computer. Do this before starting anything new so you have your partner's most recent work. |
| **Pull Request (PR)** | A request on GitHub to merge your branch into the main codebase. It shows exactly what you changed, and someone else reviews it before it gets merged. This is how code gets into the official version. |
| **Merge** | Combining your branch's changes into the main branch. This happens on GitHub after your PR is approved. |
| **Main branch** | The "official" version of the code that everyone shares. It should always work and never be broken. You don't edit it directly. |

---

## Initial Setup

You only need to do this once. If you've already done a step (for example, you already have Git installed), skip to the next one.

### Step 1: Make sure Git is installed

**What this does:** Git is the software that tracks code changes. It needs to be on your computer before you can do anything else.

**Mac:** Open the Terminal app (search "Terminal" in Spotlight) and type:
```bash
git --version
```
If you see a version number (like `git version 2.39.0`), you already have Git and can skip to Step 2. If your Mac prompts you to install developer tools, follow those prompts, then run the command again to confirm.

**Windows:** Open Command Prompt and type `git --version`. If you see a version number, skip to Step 2. If not, download Git from [git-scm.com](https://git-scm.com/) and install it. When the installer asks about terminal preferences, choose "Git Bash." After installing, close and reopen your terminal, then run `git --version` to confirm.

✅ **You're done with this step when** `git --version` shows a version number.

### Step 2: Tell Git who you are

**What this does:** Every time you save (commit) code, Git stamps it with your name and email so the team knows who made each change.

```bash
git config --global user.name "Your Full Name"
git config --global user.email "your-github-email@example.com"
```

**Important:** Use the same email address that's on your GitHub account. If they don't match, your commits won't show up as "yours" on GitHub.

✅ **You're done with this step when** `git config --global user.name` and `git config --global user.email` print your info back.

### Step 3: Accept the GitHub organization invite

**What this does:** Cayden has added you to the CivicAIClub organization on GitHub and to the **Developers** team, which has write access to every project repo.

Check your email for an invitation from GitHub to join **CivicAIClub**. Click the link and accept. If you can't find the email, go to [github.com/CivicAIClub](https://github.com/CivicAIClub) while logged into GitHub and you should see a banner to accept.

If you haven't received an invite at all, message Cayden with your GitHub username.

✅ **You're done with this step when** you can open your case's repository (link in the table above) and see its code.

### Step 4: Sign in to GitHub from your computer

**What this does:** Pushing code needs GitHub to know it's you. Passwords don't work for this; pick **one** of these:

- **Easiest:** install [GitHub Desktop](https://desktop.github.com/), sign in, and Git on your computer is authenticated. You can still use the terminal afterwards.
- **Terminal:** install the [GitHub CLI](https://cli.github.com/) and run `gh auth login` (choose GitHub.com → HTTPS → login with a web browser).
- **Manual:** GitHub → Settings → Developer settings → Personal access tokens → Fine-grained tokens → Generate. Give it access to the CivicAIClub repos with **Contents: read and write** and **Pull requests: read and write**. When Git asks for a password, paste the token.

✅ **You're done with this step when** a push in Step 4 of the workflow below doesn't ask for a password (or accepts your token).

### Step 5: Clone your repo

**What this does:** Downloads your project from GitHub onto your computer. Once per repo.

In your terminal, go to wherever you want the folder to live (Desktop is fine), then clone **your case's** repo. Pick the line for your case:

```bash
cd ~/Desktop
git clone https://github.com/CivicAIClub/case-a-clc-workflow.git    # Case A: Luke, Jack
git clone https://github.com/CivicAIClub/case-b-music-studio.git    # Case B: Serena, JT
git clone https://github.com/CivicAIClub/case-c-dei-timeline.git    # Case C: Zahir, Keke
git clone https://github.com/CivicAIClub/case-d-roster-export.git   # Case D: James, Magnus, Jay
```

This creates a folder with the repo's name (for example `case-b-music-studio`) containing all the project files.

✅ **You're done with this step when** the folder exists on your computer and contains a `README.md` and a `.cursor/rules/` folder (it's hidden; `ls -a` shows it).

### Step 6: Open it in Cursor and set the project up

**What this does:** Cursor is the code editor we're using. Opening the repo folder in Cursor loads its committed rules automatically and gives you a built-in terminal.

Open Cursor → File → Open Folder → select the repo folder (for example `case-b-music-studio`). You should see the project files in the left sidebar. From here on, use Cursor's built-in terminal (View → Terminal, or `` Ctrl+` ``) for Git commands.

Then **read your repo's `README.md`** and follow its "Setup from a fresh clone" section. Every project is different (Python virtualenv, `npm ci`, or just Apps Script), and the README is the source of truth. If the README doesn't get you to a running app, that's a bug in the README; tell Cayden.

✅ **You're done with this step when** the project runs locally the way its README says it should.

---

## How We Work: The Branch Workflow

This is the most important section. This is how every piece of code gets written and shared.

### The big picture

Nobody edits `main` directly. You create a **branch** (your own separate workspace), do your work there, then open a **Pull Request** on GitHub asking to merge your changes into `main`. Someone reviews it, and once approved, it gets merged.

This protects everyone. If your code has a bug, it doesn't break your partner's work. If you need to throw away an experiment, you just delete the branch. `main` stays clean.

### Step 1: Pull the latest main

**When:** every time you sit down to start a new piece of work.

```bash
git checkout main
git pull origin main
```

The first command switches you to `main`. The second downloads any new changes from GitHub (`origin` means "the copy on GitHub"). "Already up to date" is fine.

### Step 2: Create a new branch

```bash
git checkout -b feature/short-description
```

Branch names have a **type prefix** and a short description. All lowercase, hyphens between words, no spaces:

| Prefix | Use it for | Example |
|---|---|---|
| `feature/` | Something new | `feature/lesson-recap-editor` |
| `fix/` | Fixing a bug | `fix/date-parsing-no-due-date` |
| `chore/` | Housekeeping: docs, config, dependencies | `chore/update-readme-setup` |

**Bad branch names (don't do these):**
```bash
git checkout -b my-branch              # No type prefix
git checkout -b Feature/Canvas Setup   # No uppercase, no spaces
git checkout -b fix                    # Too vague, no description
git checkout -b case-b/new-thing       # The old case-X/ prefix is retired; the repo already says which case it is
```

✅ **You're on your branch when** the terminal shows the branch name, or `git branch` shows a `*` next to it.

### Step 3: Write your code

Do your work. The whole repo is your team's, so edit whatever the task needs. Two courtesies: check with Cayden before changing anything under `.github/` (CI, CODEOWNERS, PR template) or `.cursor/rules/`, and keep the README accurate when you change setup.

### Step 4: Stage and commit your changes

Commits are save points. Each one captures a snapshot with a message describing what changed. They stay on your computer until you push.

```bash
git add .
git commit -m "Add Status column to the By Day table"
```

`git add .` stages everything you've changed (or `git add somefile.py` for just one file). `git commit -m "..."` saves the snapshot with your message.

**Good commit messages:** `"Add student profile database schema"`, `"Fix date parsing for assignments without due dates"`, `"Create tour stop QR landing page"`.
**Bad commit messages:** `"stuff"`, `"fixed it"`, `"asdfasdf"`, `"WIP"`.

**How often?** Every time you finish a small working piece. Small, frequent commits are much easier to work with than one giant commit at the end.

### Step 5: Push your branch to GitHub

```bash
git push origin feature/short-description
```

**First-time push:** Git might say "The current branch has no upstream branch." Run the command it suggests:
```bash
git push --set-upstream origin feature/short-description
```
After that, plain `git push` works on that branch.

✅ **You're done with this step when** your branch appears under the "branches" dropdown on your repo's GitHub page.

### Step 6: Open a Pull Request (PR)

1. Go to your repo on GitHub (links in the table at the top).
2. You'll see a yellow banner saying your branch had recent pushes, with a green **"Compare & pull request"** button. Click it. (If not, open the "branches" dropdown, find your branch, and click "New pull request".)
3. **Title:** a clear description of what this PR adds or changes.
4. **Description:** the PR template is pre-filled with three headings: *What changed*, *How I tested it*, *Screenshots (if UI changed)*. Fill them in. If something is still in progress or known-broken, say so.
5. Click **"Create pull request"**.

Your project partner and Cayden are requested as reviewers automatically (that's what `CODEOWNERS` does). On Cases B and C, a CI check also installs and builds your branch; a red ❌ means the build is broken and needs fixing before merge.

### Step 7: Get a review, then merge

Someone else looks at your changes to make sure they make sense and don't break anything. This is required: the repo is configured so you **cannot merge without at least one approval**, and (where CI exists) without a green build.

If the reviewer requests changes, make them on your local branch, commit, and push again. The PR updates automatically. Reviewing your partner's PRs is part of the job too; leave comments, ask questions, and approve when it looks right.

Once approved, click the green **"Merge pull request"** button. GitHub will offer to delete the branch afterwards; go ahead, it's merged.

**After merging, update your local computer:**
```bash
git checkout main
git pull origin main
```

You're ready to start a new branch for your next task. Go back to Step 1.

---

## The Three Rules

These are non-negotiable:

**1. Never push directly to `main`.** Always use a branch and a Pull Request. Every repo in the organization is protected: GitHub will block a direct push to `main`, block force-pushes, and block deleting `main`. But understand the reason: `main` is the shared, working version your client's tool runs from.

**2. One repo per project; club-wide things go in `docs`.** Your work goes in your case's repository. Don't clone or edit another team's repo unless they ask for help. Anything that applies to everyone (guides, conventions) goes in the [docs](https://github.com/CivicAIClub/docs) repo through a PR.

**3. Never commit secrets.** API keys, passwords, tokens, `.env` files, Apps Script shared secrets: none of that goes in Git. Once committed, it's in the history permanently, even if you delete the file later. Each repo's `.gitignore` already blocks `.env` and `.env.local`, and each repo has a `.env.example` with placeholders showing which variables exist. Real values go in your local `.env` / `.env.local` only. If you're not sure whether something counts as a secret, ask before committing.

---

## Common Situations and Fixes

### "I don't know what branch I'm on"
```bash
git branch
```
The branch with a `*` is your current branch. If it says `* main`, create or switch to a feature branch before making changes.

### "I made changes but I'm not sure what's different"
```bash
git status
```
Lists every file you've changed, added, or deleted since your last commit. Red = unstaged, green = staged.

### "I want to see exactly what I changed in a file"
```bash
git diff
```
Lines starting with `+` are additions; `-` are deletions.

### "I messed up and want to undo everything since my last commit"
```bash
git checkout -- .
```
Resets all files to your last commit. **Your uncommitted changes are gone permanently.** Only use it if you're sure.

### "I accidentally started working on main instead of a branch"
If you haven't committed yet, move your work to a new branch without losing anything:
```bash
git stash
git checkout -b feature/your-feature
git stash pop
```

### "My push got rejected"
Usually your partner pushed to the same branch and you're behind:
```bash
git pull origin your-branch-name
```
If Git can combine the changes automatically, push again. If it reports a **merge conflict**, both of you edited the same lines. Git marks the file like this:
```
<<<<<<< HEAD
your version of the code
=======
their version of the code
>>>>>>> origin/branch-name
```
Open the file, decide which version to keep (or combine them), delete the `<<<<<<<`, `=======`, and `>>>>>>>` markers, save, then:
```bash
git add .
git commit -m "Resolve merge conflict in filename.py"
git push origin your-branch-name
```
If you're stuck on a merge conflict, ask for help. It's better to ask than to accidentally delete someone's work.

### "GitHub says I can't push to main / my push was rejected by a rule"
That's the protection working. Create a branch (Step 2 above), commit there, push the branch, and open a PR.

### "I want to see what branches exist"
```bash
git branch          # on your computer
git branch -r       # on GitHub
```

---

## Your Project's README

Each repo's `README.md` is the source of truth for the client, the problem, the architecture, and **exact setup steps from a fresh clone**. Read it before you start coding.

Keep it updated. When you change how the project is installed, configured, or run, update the README (and `.env.example` if you added a variable) in the same PR. Cayden needs to be able to check on any project at any time, and other teams may learn from your work. If someone can't run your project from the README alone, the README needs more detail.

---

## Where the Cursor Rules Live

Each repo has two committed rule files in `.cursor/rules/`:

- `civic-ai-workflow.mdc`: the club workflow (this guide, condensed) so the AI never suggests pushing to `main` or committing secrets.
- `case-<x>-….mdc`: your project's context: client, architecture, stack, constraints, and what "done" means.

They load automatically when the repo is open in Cursor. You don't need to paste anything into Cursor settings. If you find the rules are wrong or out of date, fix them in a `chore/` PR like any other file.

---

## Quick Reference Card

```
# === START OF A WORK SESSION ===
git checkout main                  # switch to the main branch
git pull origin main               # download the latest changes from GitHub

git checkout -b feature/name       # new branch (feature/, fix/, or chore/)


# === WHILE YOU'RE WORKING ===
git status                         # see what files you've changed
git add .                          # stage all changes for commit
git commit -m "what you did"       # save a snapshot with a description
                                   # (repeat add + commit as often as you want)


# === WHEN YOU'RE READY TO SHARE ===
git push origin feature/name       # upload your branch to GitHub
                                   # then open a Pull Request on your repo's page


# === AFTER YOUR PR IS MERGED ===
git checkout main                  # switch back to main
git pull origin main               # download the merged version
                                   # now start a new branch for your next task
```

---

## Questions?

If something doesn't make sense or you're stuck, ask Cayden or your project partner before doing anything drastic. Git mistakes are almost always fixable, but they're easier to fix early than late.
