# 🔐 GitHub SSH Key Authentication Setup

SSH key authentication with GitHub.

---

## Step 1: Check for Existing SSH Keys

```bash
ls -al ~/.ssh
```

Look for files like `id_rsa`, `id_ed25519`, or their `.pub` counterparts.

---

## Step 2: Generate a New SSH Key

### Using Ed25519 (recommended)

```bash
ssh-keygen -t ed25519 -C "your_email@example.com"
```

### If Ed25519 is not supported

```bash
ssh-keygen -t rsa -b 4096 -C "your_email@example.com"
```

- Press **Enter** to accept the default file path.
- Optionally set a **passphrase** for extra security.

---

## Step 3: Add SSH Key to the SSH Agent

Start the SSH agent:

```bash
eval "$(ssh-agent -s)"
```

Add your SSH key:

```bash
ssh-add ~/.ssh/id_ed25519
```

(Use `id_rsa` if that's your key type.)

---

## Step 4: Add the SSH Key to Your GitHub Account

1. Copy your **public key** to the clipboard:

   ```bash
   cat ~/.ssh/id_ed25519.pub
   ```

2. Go to [GitHub → Settings → SSH and GPG keys](https://github.com/settings/keys)

3. Click **New SSH key**, give it a title, and paste the key.

---

## Step 5: Test the SSH Connection

```bash
ssh -T git@github.com
```

You should see:

```
Hi username! You've successfully authenticated, but GitHub does not provide shell access.
```

---

---
