---
{"dg-publish":true,"permalink":"/technologies/bash/linux-navigation/","dg-note-properties":{}}
---


#bash 
---

## 1. Open Terminal

On Linux:

Press:

```text
Ctrl + Alt + T
```

Or search for:

```text
Terminal
```

You will see something like:

```bash
username@laptop:~$
```

This means:

```text
You are in your home folder.
$ means you can type commands.
```

---

# 2. Where am I?

Command:

```bash
pwd
```

Means:

```text
Print Working Directory
```

Example output:

```bash
/home/yourname
```

This is your current location.

---

# 3. What is inside this folder?

Command:

```bash
ls
```

Means:

```text
list files and folders
```

Example:

```bash
Desktop  Documents  Downloads  Music  Pictures
```

Better version:

```bash
ls -la
```

Meaning:

| Part | Meaning |
|---|---|
| `ls` | list |
| `-l` | long format |
| `-a` | show hidden files |

Hidden files usually start with:

```bash
.
```

Example:

```bash
.bashrc
.config
.cache
```

---

# 4. Move into a folder

Command:

```bash
cd
```

Means:

```text
change directory
```

Example:

```bash
cd Documents
```

Then check:

```bash
pwd
```

You should now be inside:

```bash
/home/yourname/Documents
```

---

# 5. Go back one level

Command:

```bash
cd ..
```

Meaning:

```text
go to parent folder
```

Example:

If you are here:

```bash
/home/yourname/Documents
```

Then:

```bash
cd ..
```

You go to:

```bash
/home/yourname
```

---

# 6. Go home

Command:

```bash
cd
```

No folder name.

It always takes you home.

Example:

```bash
cd
```

Then:

```bash
pwd
```

Output:

```bash
/home/yourname
```

---

# 7. Go to root folder

Root is the top folder of Linux.

Command:

```bash
cd /
```

Then:

```bash
pwd
```

Output:

```bash
/
```

List files:

```bash
ls
```

You may see folders like:

```bash
bin  boot  dev  etc  home  usr  var
```

Go back home:

```bash
cd
```

---

# 8. Important folders

| Path | Meaning |
|---|---|
| `/` | root folder |
| `~` | your home folder |
| `.` | current folder |
| `..` | parent folder |
| `/home/yourname` | your personal files |
| `/etc` | system configuration |
| `/var/log` | logs |
| `/tmp` | temporary files |

---

# 9. Create a practice folder

Go home:

```bash
cd
```

Create folder:

```bash
mkdir bash_practice
```

Go inside:

```bash
cd bash_practice
```

Check:

```bash
pwd
```

Expected:

```bash
/home/yourname/bash_practice
```

List:

```bash
ls
```

It should be empty.

---

# 10. Create files

Command:

```bash
touch
```

Create empty file:

```bash
touch note.txt
```

List:

```bash
ls
```

You should see:

```bash
note.txt
```

Create more files:

```bash
touch a.txt b.txt c.txt
```

List:

```bash
ls
```

---

# 11. Remove files

Careful. Deleted files usually do not go to trash.

Remove one file:

```bash
rm c.txt
```

List:

```bash
ls
```

`c.txt` should be gone.

---

# 12. Remove folder

Create folder:

```bash
mkdir temp
```

Remove empty folder:

```bash
rmdir temp
```

If folder has files inside, use:

```bash
rm -r folder_name
```

Example:

```bash
mkdir temp
touch temp/file.txt
rm -r temp
```

Meaning:

| Part | Meaning |
|---|---|
| `rm` | remove |
| `-r` | recursive, remove folder and contents |

Be careful with:

```bash
rm -r
```

---

# 13. Copy files

Create file:

```bash
touch hello.txt
```

Copy it:

```bash
cp hello.txt backup.txt
```

List:

```bash
ls
```

You should see:

```bash
backup.txt  hello.txt
```

---

# 14. Move or rename files

Rename:

```bash
mv backup.txt old_backup.txt
```

List:

```bash
ls
```

Move file into folder:

```bash
mkdir folder1
mv old_backup.txt folder1/
```

List:

```bash
ls
```

Look inside folder:

```bash
ls folder1
```

---

# 15. Absolute path vs relative path

## Absolute path

Starts from root:

```bash
/home/yourname/bash_practice
```

Example:

```bash
cd /home/yourname/bash_practice
```

## Relative path

Starts from current folder.

If you are inside:

```bash
/home/yourname
```

Then:

```bash
cd bash_practice
```

That is relative.

---

# 16. Use Tab completion

Very important.

Type:

```bash
cd bas
```

Then press:

```text
Tab
```

It should complete:

```bash
cd bash_practice
```

This saves time and reduces mistakes.

---

# 17. Useful shortcuts

| Shortcut | Effect |
|---|---|
| `Tab` | autocomplete |
| `Ctrl + C` | cancel current command |
| `Ctrl + L` | clear terminal |
| `Ctrl + A` | move cursor to line start |
| `Ctrl + E` | move cursor to line end |
| `Ctrl + U` | delete current line before cursor |
| `↑` | previous command |
| `↓` | next command |

---

# 18. Clear screen

Command:

```bash
clear
```

Or:

```bash
Ctrl + L
```

---

# 19. Mini practice

Run these one by one:

```bash
cd
pwd
ls
mkdir bash_practice
cd bash_practice
pwd
touch file1.txt
touch file2.txt
ls
cp file1.txt file1_backup.txt
ls
mkdir folder1
mv file2.txt folder1/
ls folder1
cd ..
pwd
cd bash_practice
pwd
ls
```

---

# 20. You should now know

```bash
pwd
ls
ls -la
cd
cd folder
cd ..
cd /
mkdir
touch
rm
rmdir
rm -r
cp
mv
clear
```

---
