Here is a **simple, exam-friendly explanation** of the topics you asked for, divided into two parts:

---

## 🐚 **Shell Scripting Basics**

### 1. ✅ **Simple Shell Script**

* A file containing UNIX commands to automate tasks.

```bash
#!/bin/bash
echo "Hello, World!"
```

### 2. 👤 **Interactive Shell Script**

* Takes input from the user.

```bash
#!/bin/bash
echo "Enter your name:"
read name
echo "Hello, $name!"
```

### 3. 🧾 **Using Command Line Arguments**

```bash
#!/bin/bash
echo "First arg: $1"
echo "Second arg: $2"
```

### 4. 🔗 **Logical Operators**

* `&&` → run second command only if first succeeds
* `||` → run second command if first fails

```bash
mkdir test && echo "Created"
rm file.txt || echo "File not found"
```

### 5. 🔍 **Condition Checking**

#### `if` Statement:

```bash
if [ $age -ge 18 ]; then
  echo "Adult"
else
  echo "Minor"
fi
```

#### `case` Statement:

```bash
case $1 in
  start) echo "Starting...";;
  stop) echo "Stopping...";;
  *) echo "Unknown option";;
esac
```

---

### 6. ➕ **Expression Evaluation**

#### Using `test` or `[ ]`:

```bash
if [ $a -eq $b ]; then
  echo "Equal"
fi
```

#### Using `expr` for computation:

```bash
sum=$(expr 3 + 2)
echo $sum
```

#### `expr` for strings:

```bash
expr length "hello"
expr index "hello" "e"
```

---

### 7. 🔁 **Loops**

#### `while` Loop:

```bash
count=1
while [ $count -le 5 ]; do
  echo $count
  count=$(expr $count + 1)
done
```

#### `for` Loop:

```bash
for i in 1 2 3; do
  echo $i
done
```

---

### 8. 📍 **Positional Parameters**

| Symbol | Meaning             |
| ------ | ------------------- |
| `$0`   | Script name         |
| `$1`   | First argument      |
| `$2`   | Second argument     |
| `$@`   | All arguments       |
| `$#`   | Number of arguments |

---

## 🖥️ **System Administration (UNIX)**

### ✅ **Essential Duties**

* Manage users and groups
* Control system boot and shutdown
* Backup & restore data
* Install software and patches
* Monitor system performance

---

### 🔁 **Starting and Shutdown**

| Command           | Use                  |
| ----------------- | -------------------- |
| `reboot`          | Restart system       |
| `shutdown -h now` | Shutdown immediately |
| `init 0`          | Shutdown             |
| `init 6`          | Reboot               |

---

### 👤 **User Account Management (Basic)**

| Field          | Description                                   |
| -------------- | --------------------------------------------- |
| Username       | Unique login name                             |
| Password       | Encrypted in `/etc/shadow`                    |
| Home Directory | User's default directory (e.g., `/home/user`) |
| Group ID       | Primary group ID in `/etc/group`              |
| Disk Quota     | Limit on how much disk space user can use     |
| Terminal       | The terminal used for login (e.g., `tty1`)    |

---

Let me know if you want a **cheat sheet PDF**, **practice questions**, or **shell script examples**!
