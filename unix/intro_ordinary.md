Here’s a **very short and exam-oriented summary** of file management commands in UNIX:

---

### 📄 **Displaying and Creating Files**

* **`cat`** – Concatenate and display file contents.

  ```sh
  cat file.txt    # Display contents of a file
  cat > newfile   # Create a new file by entering text
  ```

---

### 📋 **Copying a File**

* **`cp`** – Copy files or directories.

  ```sh
  cp source.txt destination.txt   # Copy file
  cp -r source_dir/ destination_dir/  # Copy directory recursively
  ```

---

### 🗑️ **Deleting a File**

* **`rm`** – Remove a file or directory.

  ```sh
  rm file.txt    # Remove a file
  rm -r dir_name # Remove a directory recursively
  ```

---

### 🔄 **Renaming/Moving a File**

* **`mv`** – Rename or move files/directories.

  ```sh
  mv oldname.txt newname.txt    # Rename a file
  mv file.txt /newfolder/      # Move file to a new directory
  ```

---

### 📜 **Paging Output**

* **`more`** – View file contents page by page.

  ```sh
  more largefile.txt  # Display file with pagination
  ```

---

### 🖨️ **Printing a File**

* **`lp`** – Print a file to the default printer.

  ```sh
  lp file.txt   # Print file.txt
  ```

---

### 🗂️ **Knowing File Type**

* **`file`** – Determine the file type.

  ```sh
  file file.txt  # e.g., text, binary, executable, etc.
  ```

---

### 🔢 **Line, Word, and Character Counting**

* **`wc`** – Count lines, words, and characters in a file.

  ```sh
  wc file.txt      # Output: lines, words, characters
  wc -l file.txt   # Count only lines
  wc -w file.txt   # Count only words
  ```

---

### 🔍 **Comparing Files**

* **`cmp`** – Compare two files byte by byte.

  ```sh
  cmp file1.txt file2.txt  # Shows first difference
  ```

---

### 🧩 **Finding Common Between Two Files**

* **`comm`** – Display common lines between two sorted files.

  ```sh
  comm file1.txt file2.txt
  ```

---

### ⚖️ **Displaying File Differences**

* **`diff`** – Show line-by-line differences between two files.

  ```sh
  diff file1.txt file2.txt  # Displays differences
  ```

---

### 📦 **Creating Archive File**

* **`tar`** – Archive files into a single file (tarball).

  ```sh
  tar -cvf archive.tar file1.txt file2.txt   # Create tar archive
  ```

---

### 📚 **Compress File**

* **`gzip`** – Compress a file.

  ```sh
  gzip file.txt    # Compress file to file.txt.gz
  ```

---

### 📥 **Uncompress File**

* **`gunzip`** – Decompress a `.gz` file.

  ```sh
  gunzip file.txt.gz  # Decompress file
  ```

---

### 📦 **Archive File (zip)**

* **`zip`** – Create a zip archive.

  ```sh
  zip archive.zip file1.txt file2.txt
  ```

---

### 📤 **Extract Compressed File (unzip)**

* **`unzip`** – Extract files from a `.zip` archive.

  ```sh
  unzip archive.zip   # Extract zip archive
  ```

---

### 🔄 **Effect of `cp`, `rm`, and `mv` on Directories**

* **`cp`** – Copies the entire directory with the `-r` flag.

  ```sh
  cp -r dir1/ dir2/  # Copy directory recursively
  ```
* **`rm`** – Removes a directory with the `-r` flag (recursively).

  ```sh
  rm -r dir_name    # Remove directory and contents
  ```
* **`mv`** – Moves a directory or renames it.

  ```sh
  mv old_dir/ new_dir/    # Move or rename directory
  ```

---

Let me know if you'd like any more detailed examples or clarification!
