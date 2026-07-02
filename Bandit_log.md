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

## Level 5

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



