Here’s a **very short and exam-oriented summary** of UNIX file system concepts:

---

### 📂 **UNIX File System**

* **File System**: A hierarchical structure for storing files and directories.

### 🗂️ **Types of Files**

1. **Regular files** – Data files (text, binaries).
2. **Directories** – Special files containing references to other files.
3. **Special files** – Devices or communication files (e.g., `/dev/sda`).

### 📝 **File Naming Convention**

* File names: Can be up to 255 characters.
* Case-sensitive: `file.txt` ≠ `File.txt`.

### 👪 **Parent-Child Relationship**

* Directories and files form a **tree-like structure**.
* Parent directory (`/home`) contains child directories (`/home/user`).

---

### 🏠 **HOME Variable**

* Stores the path to the user's home directory.

  ```sh
  echo $HOME   # Example: /home/user
  ```

### 🆔 **inode Number**

* Stores metadata about a file (owner, permissions, size, etc.).
* Each file has a unique inode number.

---

### 📍 **Absolute vs Relative Pathnames**

* **Absolute pathname**: Full path starting from root (`/`), e.g., `/home/user/file.txt`.
* **Relative pathname**: Path relative to current directory, e.g., `./file.txt` (current directory).

---

### 🔍 **Significance of Dot (`.`) and Dot-Dot (`..`)**

* **`.`** → current directory.
* **`..`** → parent directory.

---

### 🛠️ **File Management Commands**

* **`pwd`** – Displays the full path of the current directory.

  ```sh
  pwd  # Example: /home/user/Documents
  ```
* **`cd`** – Changes current directory.

  ```sh
  cd /home/user/Documents
  cd ..   # move up one directory
  ```
* **`mkdir`** – Creates a directory.

  ```sh
  mkdir new_folder
  ```
* **`rmdir`** – Removes an empty directory.

  ```sh
  rmdir empty_folder
  ```

### 📑 **Listing Directory Contents**

* **`ls`** – Lists files and directories.

  ```sh
  ls        # lists files in the current directory
  ls -l     # long format (detailed)
  ls -a     # includes hidden files (those starting with `.`)
  ```

---

### 🗂️ **Important Directories in UNIX**

* **`/bin`**: Essential system binaries (commands).
* **`/usr/bin`**: Non-essential binaries (user programs).
* **`/sbin`**: System binaries (used by admin).
* **`/usr/sbin`**: Non-essential system binaries.
* **`/etc`**: System configuration files.
* **`/dev`**: Device files (e.g., hard disks, terminals).
* **`/lib`**: System libraries.
* **`/usr/lib`**: Libraries for non-essential programs.
* **`/usr/include`**: Header files for compiling programs.
* **`/usr/share/man`**: Manual pages.
* **`/tmp`**: Temporary files.
* **`/var`**: Variable data files (logs, databases).
* **`/home`**: User home directories.

---

This covers the key UNIX file system concepts for your exam. Let me know if you'd like any further details!
