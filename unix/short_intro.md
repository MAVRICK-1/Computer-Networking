Here's a **very short and exam-oriented** summary of the key UNIX concepts:

---

### 💻 **UNIX Operating System**

A **multiuser**, **multitasking**, and **portable** operating system, widely used in servers and programming environments.

---

### 🧱 **UNIX Architecture**

1. **Kernel** – Core of UNIX

   * Manages hardware, memory, processes, files, and system calls

2. **Shell** – Command-line interface

   * Accepts user input and passes it to the kernel

3. **Utilities** – Standard programs/tools (e.g., `ls`, `cp`)

---

### 📁 **Files and Processes**

* **Everything in UNIX is a file** (including devices).
* **Process** – A running program.
* Commands like `ps`, `kill`, and `top` manage processes.

---

### 🧩 **System Calls**

* Interface between **user programs and kernel**
* Examples: `read()`, `write()`, `fork()`, `exec()`, `open()`

---

### ⭐ **Features of UNIX**

* Multiuser & multitasking
* Portability
* Security & permission control
* Pipelining and redirection
* Rich set of utilities

---

### 📜 **POSIX and SUS**

* **POSIX**: Portable Operating System Interface

  * IEEE standard for UNIX compatibility
* **SUS**: Single UNIX Specification

  * Defines what it means to be a "UNIX" system

---

### 🛠️ **Internal vs External Commands**

| Internal Commands        | External Commands           |
| ------------------------ | --------------------------- |
| Built into shell         | Stored as separate binaries |
| Fast execution           | Slower (loads from disk)    |
| e.g. `cd`, `echo`, `pwd` | e.g. `ls`, `cp`, `grep`     |

---

Let me know if you want this in a printable format or flashcards.


Here's a **very short and exam-oriented summary** of the given UNIX commands:

---

### 📅 **`cal`** – Calendar

Displays the calendar of the current or given month/year.

```sh
cal           # current month
cal 2025      # full calendar of 2025
```

---

### 🕒 **`date`** – Display system date and time

```sh
date          # shows current date and time
```

---

### 💬 **`echo`** – Message display

Prints text or variable values.

```sh
echo "Hello"  
echo $HOME  
```

---

### 🧮 **`bc`** – Calculator (basic calculator)

Command-line calculator, supports floating point:

```sh
echo "5+3" | bc  
```

---

### 🔒 **`passwd`** – Change user password

```sh
passwd        # prompts to change your password
```

---

### 👥 **`who`** – Shows logged-in users

```sh
who           # lists users currently logged in
```

---

### 🖥️ **`uname`** – System information

```sh
uname         # system name
uname -a      # all system info (kernel, architecture, etc.)
```

---

### 🧷 **`tty`** – Terminal filename connected to input

```sh
tty           # returns the terminal device (e.g., /dev/pts/0)
```

---

Let me know if you'd like a 1-page PDF of all these UNIX quick-revision notes!

