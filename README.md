# Git Assignment – DevOps Micro Internship

This assignment is part of the **DevOps Micro Internship (#DMIByPravinMishra)** led by [Pravin Mishra](https://www.linkedin.com/in/pravin-mishra-aws-trainer/).

🎓 Enrollment, cohort dates, and the full curriculum are on [University](https://university.pravinmishra.com?utm_source=dmi&utm_medium=readme&utm_campaign=week4-codetrack).
💬 Questions along the way? Join the [DMI Discord](https://discord.pravinmishra.com/?utm_source=dmi&utm_medium=readme&utm_campaign=week4-codetrack).

This repo is the **starter UI** for the assignment below — `index.html` and `style.css` here are the files you'll copy into your own `CodeTrack` project in Task 3.

---

## Week 4 – Git & GitHub Assignment: CodeTrack

### Scenario (Real Job Ticket)

You joined the **"CodeTrack"** project. Your manager wants:

- A clean initial commit with starter UI files
- A second commit after you follow product instructions in `index.html`
- A basic deployment to an EC2 web server (Nginx)

### Learning Objectives

You will learn to:

- Inspect repo state with `git status`
- Stage changes properly (`git add .` vs `git add <file>`)
- Create meaningful commits (two commits minimum)
- Verify history using `git log --oneline`
- Deploy a static website to EC2 using Nginx (industry simulation)

### Prerequisites

- Assignment 1 completed: `CodeTrack` exists and is a Git repo (`.git` folder present)
- Git installed: `git --version`
- Basic file editing (VS Code / Notepad / Nano)
- AWS EC2 access for deployment task (Task 7)

### Notes / Assumptions

- Your repo is named `CodeTrack` and already initialized with Git.
- Default branch might be `master` or `main` depending on Git version/settings (both are okay).
- For EC2, you may use Ubuntu or Amazon Linux. Steps provided for both.

---

## Tasks

### Task 1 — Verify Git Setup + Enter the Repo

**Goal:** Confirm Git works and you are inside the right folder.

Check Git:

```bash
git --version
```

Go to your CodeTrack folder:

macOS/Linux/Git Bash:

```bash
cd ~/projects/CodeTrack
pwd
```

Windows PowerShell (example path):

```powershell
cd C:\Users\<YourUser>\projects\CodeTrack
cd
```

Confirm it's a Git repo:

```bash
git status
```

✅ **Expected:** You see a status message and no "not a git repository" error.

> **Industry Note:** Half of Git mistakes happen because people run commands in the wrong folder. Pros always verify with `pwd` + `git status`.

**Screenshots required**
- Screenshot 1: `pwd`
- Screenshot 2: `git status`

---

### Task 2 — Create `index.html` and `style.css`

**Goal:** Create two files and confirm they exist.

macOS/Linux/Git Bash:

```bash
touch index.html style.css
ls
```

Windows PowerShell (no `touch`):

```powershell
echo. > index.html
echo. > style.css
dir
```

✅ **Expected:** You see both files in the directory listing.

> **Industry Note:** This simulates the first step of a frontend ticket: scaffold basic files before you start development.

**Screenshots required**
- Screenshot 3: Command + output showing both files exist (`ls` or `dir`)

---

### Task 3 — Add Starter Content (Two Options)

**Goal:** Put real HTML/CSS content in the files.

1. Open GitHub repo: [`dmi-codetrack-starter-assignment`](https://github.com/pravinmishraaws/dmi-codetrack-starter-assignment)
2. Copy content from their `index.html` and `style.css`
3. Paste into your local files

> **Industry Note:** Teams often give a starter template repo. Your job is to pull/apply it and then start making controlled commits.

**Screenshots required**
- Screenshot 4: Your editor showing `index.html` + `style.css` contents (one screenshot is fine if both visible, otherwise two)

---

### Task 4 — Track and Stage Files Correctly

**Goal:** See untracked files, then stage them.

Check status:

```bash
git status
```

✅ **Expected:** `index.html` and `style.css` appear as untracked.

Stage files (choose one approach):

**Approach 1** (recommended for beginners now):

```bash
git add index.html
git add style.css
```

**Approach 2** (bulk stage):

```bash
git add .
```

Verify staged:

```bash
git status
```

✅ **Expected:** Under `Changes to be committed` you see `new file: index.html` and `new file: style.css`

> **Industry Note:** Staging is how you control exactly what goes into a commit. Professionals avoid "accidental commits" by staging intentionally.

**Screenshots required**
- Screenshot 5: `git status` showing files as untracked
- Screenshot 6: `git status` showing files as staged / changes to be committed

---

### Task 5 — Create the First Commit (Clean Initial Commit)

**Goal:** Make your first commit with a meaningful message.

```bash
git commit -m "Initial UI scaffold: add index.html and style.css"
```

Verify history:

```bash
git log --oneline
```

✅ **Expected:** 1 commit appears.

> **Industry Note:** Commit messages should read like a work log. "Initial UI scaffold…" tells reviewers what happened.

**Screenshots required**
- Screenshot 7: Output of the `git commit ...`
- Screenshot 8: Output of `git log --oneline`

---

### Task 6 — Modify `index.html` and Make a Second Commit (Controlled Change)

**Goal:** Simulate a real "small change" ticket and commit it separately.

1. Open `index.html` in your browser and look at the page.
2. Follow the instructions inside `index.html` (from the comment block): **change the Student Name & Group Name** placeholders.
3. Save the file and refresh your browser.
4. Confirm Git sees the modification:

```bash
git status
```

5. Stage only the file you changed:

```bash
git add index.html
git status
```

6. Commit with a meaningful message:

```bash
git commit -m "Update homepage content: heading, tagline, CTA button"
```

7. Verify history:

```bash
git log --oneline
```

> **Industry Note:** Multiple commits are good practice: one commit for scaffolding, one for the feature change. This makes PR review and rollback easier.

**Screenshots required**
- Screenshot 9: Browser showing updated page (visible changes)
- Screenshot 10: `git status` showing `index.html` modified
- Screenshot 11: `git commit ...` output
- Screenshot 12: `git log --oneline` showing two commits

---

### Task 7 — Deploy to EC2 with Nginx (Static Website)

**Goal:** Deploy your CodeTrack site to a live server.

**Required EC2 Setup (must be true)**
- EC2 instance running (Ubuntu or Amazon Linux)
- Security Group allows:
  - SSH (22) from your IP
  - HTTP (80) from anywhere (`0.0.0.0/0`) for testing

**Step A — SSH into EC2**

```bash
ssh -i your-key.pem ubuntu@<EC2_PUBLIC_IP>
```

(For Amazon Linux, user is often `ec2-user`)

Follow the remaining steps as below — you already mastered these in the Linux section.

- **Step B** — Install & Start Nginx
- **Step C** — Copy your files to EC2 (from your local machine)
- **Step D** — Move files into the Nginx web root (on EC2)
- **Step E** — Validate from your browser at `http://<EC2_PUBLIC_IP>`

✅ **Expected:** You should see your CodeTrack page.

> **Industry Note:** This simulates a classic DevOps flow: build locally → commit changes → deploy to server. Even with CI/CD later, this helps you understand what pipelines automate.

**Screenshots required**
- Screenshot 13: `systemctl status nginx` output (shows running)
- Screenshot 14: `curl -I http://localhost` output
- Screenshot 15: Browser showing your site loaded from `http://<EC2_PUBLIC_IP>` (URL visible)

---

## LinkedIn Post (MANDATORY)

Write a short LinkedIn post about what you achieved in this assignment. Include:

- Your application URL
- 3–5 lines: what you deployed + what you learned
- 1 screenshot proof (app page showing your Full Name)

Submit:
- LinkedIn Post URL: `___________________________`
- Screenshot of the LinkedIn post

---

## Acknowledgment

This assignment is part of the **DevOps Micro Internship (#DMIByPravinMishra)** by **Pravin Mishra**.

[University](https://university.pravinmishra.com?utm_source=dmi&utm_medium=readme&utm_campaign=week4-codetrack) · [DMI Student Hub](https://dmi.pravinmishra.com?utm_source=dmi&utm_medium=readme&utm_campaign=week4-codetrack) · [Pravin Mishra](https://pravinmishra.com?utm_source=dmi&utm_medium=readme&utm_campaign=week4-codetrack) · [Discord](https://discord.pravinmishra.com/?utm_source=dmi&utm_medium=readme&utm_campaign=week4-codetrack)
