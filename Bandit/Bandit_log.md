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

echo "kS0Hf0u5HiXFwKMKFqXvPdOTNGGa0X8V" | openssl s_client -connect localhost:<PORT> -quiet
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