# OverTheWire: Bandit Log

## Level 0

### Objective
Read the `readme` file.

### Commands
```bash
ls
cat readme
```

### Linux Concept
- `ls` lists the files in the current directory.
- `cat` displays the contents of a file.

#### Notes
To connect to a remote machine using SSH:

```bash
ssh username@hostname -p port_number
```

Example:

```bash
ssh bandit0@bandit.labs.overthewire.org -p 2220
```

### Password
```text
<password>
```

---

## Level 1

### Objective
Read a file named `-`.

### Commands
```bash
cat ./-
```

### Linux Concept
`-` is treated as standard input by many commands. Prefixing it with `./` tells the shell it's a filename in the current directory.

### Password
```text
PK8fYLZg2hnHSz83plBL1iEPKdD3QToB
```

---

## Level 2

### Objective
Read a file whose name contains spaces.

### Commands
```bash
cat -- "--spaces in this filename--"
```

or

```bash
cat ./--spaces\ in\ this\ filename--
```

### Linux Concept
- Escape spaces using `\`.
- If a filename begins with `-` or `--`, use `--` or `./` so it isn't treated as an option.

### Password
```text
7ZZ2LFrykP2zEyvBl4m3clcL7tGYJPME
```

---

## Level 3

### Objective
Find and read the hidden file inside the `inhere` directory.

### Commands
```bash
cd inhere
ls -a
cat <hidden_filename>
```

### Linux Concept
- `ls -a` displays hidden files.
- Hidden files begin with `.` (dot).

### Password
```text
xzTXq1rDJQVVAzdv5cHq1TQytTWufAMq
```

---

## Level 4

### Objective
Find the only human-readable file in the `inhere` directory.

### Commands
```bash
file ./*
cat ./-fileXX
```

## Linux Concept
- `file` identifies a file's type.
- Use `./` for filenames beginning with `-`.

### Password
```text
6C7h9GD8M6ai5nr7wo1RonrzFjj9yIrG

---

## Level 5

### Objective
Find the File with Password amoung many directories.

### Commands
```bash 
find . -type f -readable -size 1033c ! -executable
```

## Linux Concept
- `find` used to search for a specific file.
- uses Option and names to do so

### Password
``` text
pXa26xhMWaC2SvDotA4r9EgZkulOeSBW

---

## Level 6

### Objective
Find the File with Password with diferent group/user/size

### Commands
```bash 
find / -type f -user bandit7 -group bandit6 -size 33c 2>/dev/null
```

## Linux Concept
- `find` used to search for a specific file.
- uses Option and names to do so

### Password
``` text
Bmnnvf82KzQlfxgAI2d1zYbr1u9pr3E3

--- 

## Level 7

### Objective
Find the password next to the word `millionth` in `data.txt`.

### Commands
```bash
grep "millionth" data.txt
```

### Linux Concept
`grep` searches for lines containing a specific pattern or text inside files.

### Password
```text
VR1ljMayciFxbnUokuQmJFw6QC9VKtub
```

---

## Level 8

### Objective
Find the only line in `data.txt` that occurs exactly once.

### Commands
```bash
sort data.txt | uniq -u
```

### Linux Concept
- `sort` groups identical lines together.
- `uniq` only compares adjacent lines.
- `uniq -u` prints only lines that occur exactly once.
- `|` (pipe) passes the output of one command as the input to another.

### Password
```text
EjmOSvuAu7sGAHqHVcBDPirRe9T03kxl
```

---

# Command Reference

## cat
Reads a file.

```bash
cat file.txt
```
---

## grep
Searches for text.

```bash
grep "word" file.txt
```

---

## find
Searches for files.

```bash
find . -type f
```

---

## strings
Extracts readable text from binary files.

```bash
strings file.bin
```

---

## Level 9

### Objective
Find the password in `data.txt`, which contains many human-readable strings. The password is preceded by several `=` characters.

### Commands
```bash
strings data.txt | grep "==="
```

### Linux Concept
- `strings` extracts human-readable text from binary files.
- `grep` searches for lines containing a specific pattern.
- `|` (pipe) sends the output of `strings` directly to `grep`.

### Password
```text
B0s2khmbT9u0geKuOoVGW3JZKhndE3BG
```

---

## Level 10

### Objective
Decode the Base64-encoded password stored in `data.txt`.

### Commands
```bash
base64 -d data.txt
```

### Linux Concept
- Base64 is an **encoding**, not encryption.
- It converts binary data into printable text.
- `base64 -d` decodes Base64 back to its original form.

### Password
```text
pYfOY6HwUsDj5rL9UvyhU7MCmv8vN5Ro
```
---

## Level 11

### Objective
Decode the ROT13-encoded password stored in `data.txt`.

### Commands

```bash
cat data.txt | tr 'A-Za-z' 'N-ZA-Mn-za-m'
```

### Linux Concept

- `tr` translates characters from one set to another.
- ROT13 rotates every alphabetic character by 13 positions.
- Applying ROT13 twice returns the original text.

### Password

```text
GROozWPO8QyN0mGrjUkID0WCYkZiQxrN
```

---

## Level 12

### Objective

Recover the password from `data.txt`, which is a hexdump of a file that has been repeatedly compressed.

### Commands

```bash
mkdir /tmp/bandit12
cp ~/data.txt .

xxd -r data.txt > data

file data

mv data data.gz
gunzip data.gz

file data

mv data data.bz2
bunzip2 data.bz2

file data

mv data data.tar.gz
gunzip data.tar.gz

tar -xf data.tar

file data5.bin
tar -xf data5.bin

file data6.bin
mv data6.bin data6.bz2
bunzip2 data6.bz2

file data6
tar -xf data6

file data8.bin
mv data8.bin data8.gz
gunzip data8.gz

cat data8
```

### Linux Concept

- `xxd -r` reverses a hexdump back into its original binary file.
- `file` identifies the actual type of a file, regardless of its extension.
- `gunzip` decompresses **gzip** files.
- `bunzip2` decompresses **bzip2** files.
- `tar -xf` extracts the contents of a **tar archive**.
- Always inspect a file with `file` before deciding which tool to use.
- Never use `cat` on binary files; only use it once the file is identified as ASCII text.

### Password

```text
qQYQiHOBPR8zR61qxYqX45quvihF2uzk
```

---

## Level 13

### Objective

Use the provided private SSH key (`sshkey.private`) to log in as `bandit14` and retrieve the password for the next level.

### Commands

```bash
ssh -i sshkey.private bandit14@bandit.labs.overthewire.org -p 2220

cat /etc/bandit_pass/bandit14
```

### Linux Concept

- `ssh` establishes a secure remote shell connection.
- `-i` specifies the private SSH key (identity file) to use for authentication.
- `-p` specifies the SSH port.
- SSH key authentication replaces passwords by proving ownership of the matching private key.
- The private key must remain secret, while the corresponding public key is stored on the server.

### Password

```text
aaWecNkG4FhxJQxz07uiwzVP6bJiYS65
```

---

## Level 14

### Objective

Submit the current password to a service listening on `localhost` at port `30000` to receive the password for the next level.

### Commands

```bash
nmap -p 30000 -T4 -sV localhost

echo '<current_password>' | nc localhost 30000
```

### Linux Concept

- `nmap` scans hosts to discover open ports and identify running services.
- `-p 30000` scans only port `30000`.
- `-sV` attempts to detect the service running on the port.
- `localhost` refers to the current machine (`127.0.0.1`).
- `nc` (Netcat) creates TCP/UDP connections and can send or receive data.
- `echo` outputs text.
- The pipe (`|`) sends the output of one command as the input to another.
- `echo '<password>' | nc localhost 30000` sends the password directly to the service without entering interactive mode.

### Password

```text
pbLYuZtTg4MgaqfJx8jbA9gKKGqM68A7
```

---

## Level 15

### Objective

Submit the current password to the service listening on `localhost` at port `30001` using an SSL/TLS encrypted connection to receive the password for the next level.

### Commands

```bash
echo "pbLYuZtTg4MgaqfJx8jbA9gKKGqM68A7" | openssl s_client -connect localhost:30001 -quiet
```

### Linux Concept

- `openssl s_client` creates an SSL/TLS client connection to a remote service.
- `-connect host:port` specifies the destination host and port.
- `-quiet` suppresses most handshake information, displaying mainly the server's response.
- SSL/TLS encrypts data transmitted over a TCP connection.
- The pipe (`|`) sends the output of `echo` to the standard input of `openssl s_client`.

### Password

```text
kS0Hf0u5HiXFwKMKFqXvPdOTNGGa0X8V
```

---

## Level 16

### Objective

Scan the ports between `31000` and `32000` on `localhost` to find the service that accepts SSL/TLS connections. Submit the current password to that service to obtain the private SSH key for the next level.

### Commands

```bash
nmap -T4 -sV -p 31000-32000 localhost

 
```

### Linux Concept

- `nmap` is a network scanner used to discover hosts, open ports, and running services.
- `-p 31000-32000` scans the specified range of ports.
- `-T4` speeds up the scan using the Aggressive timing template, making it ideal for trusted networks and labs.
- `-sV` attempts to identify the service and version running on each open port.
- `openssl s_client` creates an SSL/TLS client connection to a server.
- `-connect host:port` specifies the destination server and port.
- The pipe (`|`) sends the current password to the SSL service through standard input (`stdin`).
- Unlike previous levels, the service returns an **SSH private key** instead of a password.

### Password

```text
N/A

Reward:
Private SSH key for bandit17
```

---

## Level 17

### Objective

Find the password for the next level by comparing the contents of `passwords.old` and `passwords.new`. The password is the only line that differs between the two files.

### Commands

```bash
ls

diff passwords.old passwords.new
```

### Linux Concept

- `diff` compares two files line by line.
- Lines beginning with `<` exist only in the first file.
- Lines beginning with `>` exist only in the second file.
- Since only one line differs, the line prefixed with `>` is the new password.
- `diff` is one of the most commonly used Linux utilities for comparing configuration files, source code, logs, and text files.

### Practical Intel

Common `diff` options:

```bash
diff file1 file2          # Basic comparison

diff -u file1 file2       # Unified output (most commonly used)

diff -y file1 file2       # Side-by-side comparison

diff -r dir1 dir2         # Compare directories recursively

diff -q file1 file2       # Only report whether files differ
```

Real-world uses:

- Compare configuration files before deployment.
- Review changes to Infrastructure as Code (Terraform, Ansible).
- Compare Kubernetes manifests.
- Check differences between application logs.
- Generate patches and review code changes.

### Password

```text
OQxXZjELndr90zuhOTDYBEomI0SZITXI
```

---

## Level 18

### Objective

Retrieve the password stored in the `readme` file. A `.bashrc` file automatically logs the user out upon login, preventing an interactive shell. Bypass the shell by executing a command directly during the SSH connection.

### Commands

```bash
ssh bandit18@bandit.labs.overthewire.org -p 2220 "cat readme"
```

### Linux Concept

- `ssh` can execute a command on a remote machine without opening an interactive shell.
- Anything enclosed in quotes after the SSH connection details is executed directly on the remote system.
- Since `.bashrc` runs only when starting an interactive shell, executing a command directly bypasses the logout script.
- This technique is commonly used for remote administration, automation, and scripting.

### Practical Intel

Common SSH command execution patterns:

```bash
ssh user@host "ls -lah"

ssh user@host "cat /etc/os-release"

ssh user@host "systemctl status nginx"

ssh user@host "journalctl -u nginx --no-pager"

ssh user@host "uptime"
```

Useful SSH options:

```bash
ssh -i ~/.ssh/id_ed25519 user@host    # Specify a private key

ssh -p 2222 user@host                 # Connect to a custom port

ssh -v user@host                      # Verbose mode (debugging)

ssh user@host "command"               # Execute a remote command
```

Real-world uses:

- Run maintenance tasks on servers.
- Retrieve logs without opening a shell.
- Automate deployments.
- Execute scripts remotely.
- Collect system information from cloud instances.

### Password

```text
KpsOfPkcP7i1FlIExk2QEjyt6dw8dxZI
```

---

## Level 19

### Objective

Use the setuid binary `bandit20-do` to execute a command as the `bandit20` user and read the password stored in `/etc/bandit_pass/bandit20`.

### Commands

```bash
ls -l

./bandit20-do cat /etc/bandit_pass/bandit20
```

### Linux Concept

- `setuid` (Set User ID) is a special Linux file permission that allows a program to run with the permissions of the file's owner instead of the user executing it.
- The `bandit20-do` binary is owned by `bandit20` and has the setuid bit enabled.
- When executed, it temporarily runs as the `bandit20` user, allowing access to files that `bandit19` cannot normally read.
- This is a common privilege escalation mechanism used by trusted system utilities.

### Practical Intel

Inspect file permissions:

```bash
ls -l
```

Example output:

```text
-rwsr-x--- 1 bandit20 bandit19 14884 Jun 24 14:58 bandit20-do
```

Notice the `s` in the owner's execute field:

```text
-rwsr-x---
   ^
```

This indicates the **setuid** bit is enabled.

Useful commands:

```bash
find / -perm -4000 2>/dev/null     # Find all setuid binaries

chmod u+s file                     # Enable the setuid bit (owner only)

chmod u-s file                     # Remove the setuid bit

stat file                          # View detailed file metadata
```

Real-world uses:

- `passwd` allows normal users to change passwords by temporarily running with root privileges.
- `sudo` uses privilege escalation to execute commands as another user.
- System administration tools often rely on setuid to perform privileged tasks securely.
- Security professionals audit setuid binaries because improperly configured ones can lead to privilege escalation vulnerabilities.

### Password

```text
4pIjcunZ0fK2vmp3IwfG8Vf7VhxD6pOA
```

---

## Level 20

### Objective

Use the `suconnect` program to connect to a listening TCP port on localhost. The service expects the current level's password and returns the password for the next level if the correct password is provided.

### Commands

```bash
# Terminal 1
echo "4pIjcunZ0fK2vmp3IwfG8Vf7VhxD6pOA" | nc -l -p 1234

# Terminal 2
./suconnect 1234
```

### Linux Concept

- `suconnect` is a custom program that connects to a TCP port on the local machine.
- `nc` (Netcat) is a versatile networking utility that can act as both a client and a server.
- `nc -l` starts Netcat in **listening mode**, waiting for an incoming connection.
- `-p 1234` specifies the port to listen on.
- `echo` sends the current level's password into Netcat through a pipe (`|`).
- `suconnect` connects to the listening port, reads the password, validates it, and returns the password for the next level.

### Practical Intel

Common Netcat commands:

```bash
nc host port                     # Connect to a TCP service

nc -l -p 1234                    # Listen on TCP port 1234

echo "Hello" | nc host port      # Send data to a service

nc -vz host 22                   # Check whether a TCP port is open

nc -lvnp 4444                    # Verbose listener (common in labs and troubleshooting)
```

Real-world uses:

- Verify whether a service is reachable.
- Test firewall and Security Group rules.
- Debug client-server communication.
- Troubleshoot Kubernetes services.
- Check if an application is listening on the expected port.
- Manually interact with TCP-based services.

### Password

```text
4pIjcunZ0fK2vmp3IwfG8Vf7VhxD6pOA
```

---
