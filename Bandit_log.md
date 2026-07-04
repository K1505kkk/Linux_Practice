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

