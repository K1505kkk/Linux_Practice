# SSH Handbook

SSH (Secure Shell) is a protocol used to securely connect to remote computers over a network. It encrypts all communication between the client and the server.

---

# Why SSH?

Instead of physically using another computer, SSH lets you open a terminal on a remote machine.

Example:

```bash
ssh bandit0@bandit.labs.overthewire.org -p 2220
```

This logs into the Bandit server as the user `bandit0`.

---

# Basic SSH Syntax

```bash
ssh username@hostname
```

Example:

```bash
ssh kj5000@example.com
```

If the server uses a custom port:

```bash
ssh -p 2220 username@hostname
```

---

# SSH Key Authentication

Instead of using passwords, SSH can authenticate using a pair of cryptographic keys.

There are two keys:

```
Private Key
id_ed25519
```

```
Public Key
id_ed25519.pub
```

## Private Key

- Must remain secret.
- Never upload or share it.
- Used to prove your identity.

Example:

```text
~/.ssh/id_ed25519
```

---

## Public Key

- Safe to share.
- Uploaded to GitHub or stored on remote servers.
- Used to verify your identity.

Example:

```text
~/.ssh/id_ed25519.pub
```

---

# Generating SSH Keys

```bash
ssh-keygen -t ed25519 -C "your-email@example.com"
```

Options:

- `-t` → Key type
- `ed25519` → Modern and recommended algorithm
- `-C` → Comment (usually your email)

---

# Using a Specific Key

Sometimes a server provides a private key.

Use:

```bash
ssh -i private_key username@hostname
```

Example (Bandit Level 13):

```bash
ssh -i sshkey.private bandit14@bandit.labs.overthewire.org -p 2220
```

`-i` means **Identity File**.

---

# SSH Directory

Linux stores SSH files here:

```text
~/.ssh/
```

Common files:

```
id_ed25519
id_ed25519.pub
known_hosts
authorized_keys
```

---

# known_hosts

When connecting to a server for the first time, SSH asks:

```
Are you sure you want to continue connecting?
```

Typing `yes` saves the server's fingerprint in:

```text
~/.ssh/known_hosts
```

This helps protect against man-in-the-middle attacks by remembering trusted servers.

---

# authorized_keys

On the server, the file:

```text
~/.ssh/authorized_keys
```

contains the public keys that are allowed to log in.

When you upload your GitHub public key or when Bandit provides key-based login, the server checks this file.

---

# SSH Authentication Flow

```
Your Computer
     │
     │ Private Key
     ▼
Signs a challenge
     │
     ▼
Remote Server
     │
Checks authorized_keys
     │
     ▼
Login Successful
```

The private key never leaves your computer.

---

# SSH and GitHub

GitHub uses SSH keys to authenticate Git operations.

Test your connection:

```bash
ssh -T git@github.com
```

Successful output:

```text
Hi <username>! You've successfully authenticated, but GitHub does not provide shell access.
```

---

# Commands Learned

Generate a new key:

```bash
ssh-keygen -t ed25519 -C "email@example.com"
```

Connect using a password:

```bash
ssh user@host -p 2220
```

Connect using a private key:

```bash
ssh -i private_key user@host -p 2220
```

Test GitHub authentication:

```bash
ssh -T git@github.com
```

Display your public key:

```bash
cat ~/.ssh/id_ed25519.pub
```

List SSH files:

```bash
ls ~/.ssh
```

---

# Concepts to Learn Later

- SSH Config (`~/.ssh/config`)
- SSH Agent (`ssh-agent`)
- `ssh-add`
- Port Forwarding
- SCP (Secure Copy)
- SFTP
- SSH Tunneling
- SSH Config Aliases
- Multiple SSH Keys