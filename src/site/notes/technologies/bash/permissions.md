---
{"dg-publish":true,"permalink":"/technologies/bash/permissions/","dg-note-properties":{}}
---

#bash 
---
# Lesson checklist

- [ ] View file with `cat`
- [ ] View long file with `less`
- [ ] Exit `less` with `q`
- [ ] Use `head`
- [ ] Use `tail`
- [ ] Use `tail -f`
- [ ] Use `>` and `>>`
- [ ] Read `ls -l` permissions
- [ ] Use `chmod +x`
- [ ] Run script with `./script.sh`
- [ ] Understand `sudo` is powerful
---
# 1. Create a test file

```bash
touch test.txt
```

Add text using `echo`:

```bash
echo "hello bash" > test.txt
```

Meaning:

```text
Put the text "hello bash" into test.txt
```

Check:

```bash
cat test.txt
```

Expected output:

```bash
hello bash
```

---

# 2. `cat` — show file content

```bash
cat test.txt
```

Good for small files.

Bad for huge files because it prints everything at once.

---

# 3. Create a longer file

Run:

```bash
for i in {1..50}; do echo "line $i" >> long.txt; done
```

This creates 50 lines.

Check:

```bash
cat long.txt
```

It prints many lines.

---

# 4. `less` — view file page by page

```bash
less long.txt
```

Inside `less`:

| Key | Action |
|---|---|
| `↑` | scroll up |
| `↓` | scroll down |
| `Space` | next page |
| `b` | previous page |
| `q` | quit |

Important:

```text
Press q to exit less.
```

---

# 5. `head` — show first lines

Show first 10 lines:

```bash
head long.txt
```

Show first 3 lines:

```bash
head -n 3 long.txt
```

Expected:

```bash
line 1
line 2
line 3
```

---

# 6. `tail` — show last lines

Show last 10 lines:

```bash
tail long.txt
```

Show last 3 lines:

```bash
tail -n 3 long.txt
```

Expected:

```bash
line 48
line 49
line 50
```

---

# 7. `tail -f` — follow live file updates

Useful for logs.

Create log file:

```bash
echo "start" > app.log
```

Follow it:

```bash
tail -f app.log
```

Open another terminal if needed.

In another terminal:

```bash
cd bash_practice
echo "new event" >> app.log
```

The first terminal will show:

```bash
new event
```

Stop following with:

```bash
Ctrl + C
```

---

# 8. Redirection quickly

You already used:

```bash
>
```

and:

```bash
>>
```

Meaning:

| Symbol | Meaning |
|---|---|
| `>` | write output to file, overwrite |
| `>>` | write output to file, append |

Example:

```bash
echo "one" > out.txt
echo "two" >> out.txt
cat out.txt
```

Expected:

```bash
one
two
```

---

# 9. Permissions — why they matter

Every file has permissions.

They control:

```text
read
write
execute
```

For:

```text
owner
group
others
```

---

# 10. See permissions

```bash
ls -l
```

Example output:

```bash
-rw-r--r-- 1 yourname yourname 6 Jan 1 12:00 test.txt
```

The important part:

```bash
-rw-r--r--
```

Break it down:

```bash
- rw- r-- r--
```

| Position | Meaning |
|---|---|
| First `-` | normal file |
| `rw-` | owner permissions |
| `r--` | group permissions |
| `r--` | others permissions |

---

# 11. Permission letters

| Letter | Meaning |
|---|---|
| `r` | read |
| `w` | write |
| `x` | execute |
| `-` | no permission |

For folders:

| Letter | Meaning for folder |
|---|---|
| `r` | list folder contents |
| `w` | create/delete inside folder |
| `x` | enter folder |

---

# 12. Make a script file

Create:

```bash
touch hello.sh
```

Add content:

```bash
echo "echo Hello from Bash" > hello.sh
```

View:

```bash
cat hello.sh
```

Expected:

```bash
echo Hello from Bash
```

Try running:

```bash
./hello.sh
```

You may get:

```bash
Permission denied
```

Because it is not executable yet.

---

# 13. Make script executable

```bash
chmod +x hello.sh
```

Check:

```bash
ls -l hello.sh
```

You should see something like:

```bash
-rwxr-xr-x
```

Now run:

```bash
./hello.sh
```

Expected:

```bash
Hello from Bash
```

---

# 14. What does `chmod +x` mean?

```bash
chmod
```

Means:

```text
change mode / change permissions
```

```bash
+x
```

Means:

```text
add execute permission
```

So:

```bash
chmod +x hello.sh
```

Means:

```text
make hello.sh executable
```

---

# 15. Numeric permissions

Common one:

```bash
chmod 600 secret.txt
```

Meaning:

```text
owner can read/write
group has no access
others have no access
```

Create:

```bash
echo "private" > secret.txt
chmod 600 secret.txt
ls -l secret.txt
```

Expected:

```bash
-rw-------
```

---

# 16. Common permission numbers

| Number | Meaning |
|---|---|
| `777` | everyone can read/write/execute — usually unsafe |
| `755` | owner full, others read/execute |
| `700` | only owner full access |
| `644` | owner read/write, others read |
| `600` | only owner read/write |

Rule:

```text
Do not use 777 unless you really know why.
```

---

# 17. Change permissions with numbers

```bash
chmod 644 test.txt
ls -l test.txt
```

Expected similar:

```bash
-rw-r--r--
```

Then:

```bash
chmod 600 test.txt
ls -l test.txt
```

Expected:

```bash
-rw-------
```

---

# 18. Understand `sudo`

`sudo` means:

```text
run command as administrator
```

Example:

```bash
sudo apt update
```

Use `sudo` only when needed.

Dangerous example:

```bash
sudo rm -r /
```

Never run that.

It tries to destroy the system.

---

# 19. `chown` — change owner

Basic idea:

```bash
chown user:group file
```

Example:

```bash
sudo chown yourname:yourname secret.txt
```

Replace `yourname` with your actual username.

Check your username:

```bash
whoami
```

---

