# Linux Handbook

My personal Linux reference built through hands-on practice.

---

# Terminal Basics

## Current Directory

Show where you currently are.

```bash
pwd
```

Example:

```text
/home/kj5000/PROJECTS
```

---

## List Files

```bash
ls
```

Useful options:

```bash
ls -a      # Show hidden files
ls -l      # Detailed view
ls -la     # Detailed + hidden files
```

---

## Change Directory

```bash
cd folder_name
```

Useful shortcuts:

```bash
cd ..
cd ~
cd /
cd -
```

| Command | Meaning |
|---------|----------|
| `cd ..` | Parent directory |
| `cd ~` | Home directory |
| `cd /` | Root directory |
| `cd -` | Previous directory |

---

# Creating Files

## Create a File

```bash
cat > notes.txt
```

Type your text.

Press:

```
Ctrl + D
```

to save.

---

## Append to an Existing File

```bash
cat >> notes.txt
```

Adds text without deleting previous contents.

---

## Read a File

```bash
cat file.txt
```

---

## Rename a File

```bash
mv old_name.txt new_name.txt
```

Example:

```bash
mv Notes.txt Bandit_log.md
```

---

## Move a File

```bash
mv file.txt ~/PROJECTS/Linux_Practice/
```

---

# Hidden Files

Files beginning with `.` are hidden.

Show them:

```bash
ls -a
```

Examples:

```text
.bashrc
.profile
.gitignore
```

---

# Special File Names

## Filename "-"

Linux thinks filenames beginning with `-` are options.

Wrong:

```bash
cat -
```

Correct:

```bash
cat ./-
```

---

## Filename Beginning with "--"

Wrong:

```bash
cat --file
```

Correct:

```bash
cat ./--file
```

---

## Filenames with Spaces

Using quotes:

```bash
cat "spaces in filename"
```

Using escape characters:

```bash
cat spaces\ in\ filename
```

---

# SSH

## Connect to Remote Machine

```bash
ssh username@host -p port
```

Example:

```bash
ssh bandit5@bandit.labs.overthewire.org -p 2220
```

---

## Exit SSH

```bash
exit
```

or

```
Ctrl + D
```

---

# Markdown Basics

## Headings

```md
# Heading
## Sub Heading
### Section
```

---

## Inline Code

```md
`command`
```

Produces:

`command`

---

## Code Block

````md
```bash
ls -la
```

