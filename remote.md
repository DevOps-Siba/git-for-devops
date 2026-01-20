# How to Clone a GitHub Repository Using SSH and PAT

This document explains two standard ways to clone a GitHub repository:

1. Using **SSH keys** (recommended best practice)
2. Using **Personal Access Token (PAT)** over HTTPS

---

## Method 1: Clone Repo Using SSH (Best Practice)

### Step 1: Generate an SSH key (if not already created)

```bash
ssh-keygen -t ed25519 -C "your_email@example.com"
```

Press **Enter** for all prompts.

---

### Step 2: Copy your public key

```bash
cat ~/.ssh/id_ed25519.pub
```

Copy the full output.

---

### Step 3: Add SSH key to GitHub

1. Go to **GitHub → Settings**
2. Click **SSH and GPG keys**
3. Click **New SSH key**
4. Title: `my-laptop-key`
5. Key: paste the copied key
6. Click **Add SSH key**

---

### Step 4: Test SSH connection

```bash
ssh -T git@github.com
```

Expected output:

```
Hi DevOps-Siba! You've successfully authenticated...
```

---

### Step 5: Clone repo using SSH

From GitHub repo → **Code → SSH**, copy the SSH URL:

```
git@github.com:DevOps-Siba/git-for-devops.git
```

Then run:

```bash
git clone git@github.com:DevOps-Siba/git-for-devops.git
```

---

### Bonus: Convert an already cloned repo from HTTPS to SSH

```bash
git remote set-url origin git@github.com:DevOps-Siba/git-for-devops.git
```

---

## Method 2: Clone Repo Using PAT (HTTPS)

### Step 1: Generate a PAT on GitHub

1. GitHub → Settings
2. Developer settings → Personal access tokens → Tokens (classic)
3. Generate new token

   * Note: `git-access`
   * Expiration: 30 days or No expiration
   * Scopes: ✅ `repo`
4. Copy the generated token

---

### Step 2: Get the HTTPS clone URL

From GitHub repo → **Code → HTTPS**, copy the URL:

```
https://github.com/DevOps-Siba/git-for-devops.git
```

---

### Step 3: Clone repo using HTTPS

```bash
git clone https://github.com/DevOps-Siba/git-for-devops.git
```

When prompted:

```
Username: DevOps-Siba
Password: <paste your PAT>
```

---

### Optional: One-line method (PAT embedded in URL)

⚠️ Not recommended for security, only for labs:

```bash
git clone https://DevOps-Siba:<YOUR_PAT>@github.com/DevOps-Siba/git-for-devops.git
```

Example:

```bash
git clone https://DevOps-Siba:ghp_xxxxxx@github.com/DevOps-Siba/git-for-devops.git
```

---

### Store PAT so it won't ask again

```bash
git config --global credential.helper store
```

---

## Verification Commands

```bash
git remote -v
ssh -T git@github.com
```

---

## Summary

| Method      | When to Use                              |
| ----------- | ---------------------------------------- |
| SSH         | Best practice, no password/token prompts |
| PAT (HTTPS) | Quick setup, training, fallback          |

---

## Recommended for You

Since you are preparing for real DevOps workflows, **SSH** is strongly recommended for daily use.

---

*End of document*
