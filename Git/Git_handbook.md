# Git Handbook

Personal Git + GitHub workflow used from the Linux terminal.

---

# One-Time Setup

Check Git version

```bash
git --version
```

Configure identity

```bash
git config --global user.name "Your Name"
git config --global user.email "you@example.com"
```

View configuration

```bash
git config --list
```

---

# Create a Repository

Create project

```bash
mkdir Project
cd Project
```

Initialize Git

```bash
git init
```

---

# Check Repository Status

```bash
git status
```

Use this command constantly.

---

# Add Files

Add one file

```bash
git add filename
```

Add everything

```bash
git add .
```

---

# Commit Changes

```bash
git commit -m "Meaningful commit message"
```

Example:

```bash
git commit -m "Completed Bandit Levels 0-10"
```

---

# View Commit History

Compact view

```bash
git log --oneline
```

Detailed view

```bash
git log
```

---

# GitHub via SSH

Generate SSH key

```bash
ssh-keygen -t ed25519 -C "your_email@example.com"
```

Show public key

```bash
cat ~/.ssh/id_ed25519.pub
```

Test GitHub authentication

```bash
ssh -T git@github.com
```

Expected output:

```text
Hi username! You've successfully authenticated...
```

---

# Add Remote Repository

View remotes

```bash
git remote -v
```

Add remote

```bash
git remote add origin git@github.com:USERNAME/REPOSITORY.git
```

Change remote

```bash
git remote set-url origin git@github.com:USERNAME/REPOSITORY.git
```

---

# Push Changes

First push

```bash
git push -u origin main
```

Later pushes

```bash
git push
```

---

# Pull Changes

```bash
git pull
```

If histories are unrelated

```bash
git pull origin main --rebase --allow-unrelated-histories
```

---

# Common Workflow

Check status

```bash
git status
```

Stage changes

```bash
git add .
```

Commit

```bash
git commit -m "Describe changes"
```

Push

```bash
git push
```

---

# Lessons Learned

- `git status` is your best friend.
- Commit small, meaningful changes.
- Use SSH instead of HTTPS for GitHub authentication.
- Read Git's error messages—they usually tell you exactly what to do.
