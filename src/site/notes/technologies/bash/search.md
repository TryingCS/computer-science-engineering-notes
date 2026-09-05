---
{"dg-publish":true,"permalink":"/technologies/bash/search/","dg-note-properties":{}}
---


#bash 
# Search (`grep`, `find`, `locate`)

## Lesson Checklist
- [ ] Search text inside a file with `grep`
- [ ] Use `grep` flags (`-i`, `-n`, `-r`, `-v`)
- [ ] Search for files by name with `find`
- [ ] Use `find` flags (`-type`, `-size`, `-iname`)
- [ ] Understand metric sizes in `find` (`k`, `M`, `G`)
- [ ] Use `locate` for fast system-wide search
- [ ] Update the locate database with `sudo updatedb`

---

# 1. Prepare practice folder

Open terminal and go to your practice folder:

```bash
cd ~/bash_practice
```

Create a clean workspace for this lesson:

```bash
mkdir search_lab
cd search_lab
```

---

# 2. Create test files

Let us make some files to search through.

```bash
echo "apple" > fruit.txt
echo "banana" >> fruit.txt
echo "Apple pie" >> fruit.txt
echo "cherry" >> fruit.txt

echo "dog" > animal.txt
echo "cat" >> animal.txt
```

Check them:

```bash
cat fruit.txt
cat animal.txt
```

---

# 3. `grep` — search inside files

`grep` looks for **text** inside files.

Basic usage:

```bash
grep "apple" fruit.txt
```

Expected output:

```text
apple
```

Notice it did not find "Apple pie". `grep` is case-sensitive by default.

---

# 4. Useful `grep` flags

| Flag | Meaning |
|---|---|
| `-i` | ignore case (upper/lower) |
| `-n` | show line numbers |
| `-v` | invert match (show lines that DO NOT match) |
| `-r` | recursive (search inside all files in a folder) |

### Ignore case (`-i`)

```bash
grep -i "apple" fruit.txt
```

Output:

```text
apple
Apple pie
```

### Show line numbers (`-n`)

```bash
grep -n "banana" fruit.txt
```

Output:

```text
2:banana
```

### Invert match (`-v`)

Show everything EXCEPT "cherry":

```bash
grep -v "cherry" fruit.txt
```

### Recursive search (`-r`)

Search for "cat" in all files in the current folder:

```bash
grep -r "cat" .
```

Output:

```text
./animal.txt:cat
```

---

# 5. `find` — search for files and folders

`grep` searches **inside** files.
`find` searches for the files **themselves**.

Basic usage:

```bash
find . -name "fruit.txt"
```

Meaning:
- `.` = start in current folder
- `-name` = match exact name

Output:

```text
./fruit.txt
```

---

# 6. Useful `find` flags

### Ignore case (`-iname`)

```bash
find . -iname "FRUIT.TXT"
```

### Find by type (`-type`)

| Type | Meaning |
|---|---|
| `f` | file |
| `d` | directory (folder) |

Find only folders:

```bash
find . -type d
```

Find only files:

```bash
find . -type f
```

---

# 7. Find by size (Metric System)

`find` uses metric units for size.

| Letter | Metric Unit |
|---|---|
| `c` | bytes |
| `k` | Kilobytes (KB) |
| `M` | Megabytes (MB) |
| `G` | Gigabytes (GB) |

Find files larger than 1 Kilobyte:

```bash
find . -type f -size +1k
```

Find files smaller than 1 Megabyte:

```bash
find . -type f -size -1M
```

*(Note: Our test files are tiny, so `+1k` might return nothing. `+0c` means larger than 0 bytes).*

---

# 8. Wildcards in `find`

Use `*` to match any characters.

Find all `.txt` files:

```bash
find . -name "*.txt"
```

**Important:** Always put quotes around the name when using `*`.

---

# 9. `locate` — fast system-wide search

`find` scans the hard drive in real-time. It can be slow.
`locate` searches a pre-built database. It is instant.

Try it:

```bash
locate bash
```

It will instantly list every file on your system with "bash" in the path.

---

# 10. Update the `locate` database

If you just created a file, `locate` will not see it yet. The database updates automatically once a day, but you can force it.

```bash
sudo updatedb
```

Enter your password when prompted.

Now `locate` will see your new files.

---

# 11. Combine `find` and `grep`

This is a very common real-world pattern.

First, use `find` to get a list of files.
Then, use `grep` to search inside them.

Example: Find all `.txt` files, then search for "apple" inside them.

```bash
find . -name "*.txt" -exec grep -i "apple" {} +
```

Breakdown:
- `-exec` = run a command on the results
- `grep -i "apple"` = the command to run
- `{}` = placeholder for the file name `find` discovered
- `+` = end of the command

---

# 12. Mini practice

Run these commands one by one:

```bash
cd ~/bash_practice/search_lab

# grep practice
grep -i "apple" fruit.txt
grep -n "dog" animal.txt
grep -v "cat" animal.txt

# find practice
find . -name "*.txt"
find . -type f
find . -type d

# locate practice
locate updatedb
```

---

# Next lesson

Lesson 4 will be