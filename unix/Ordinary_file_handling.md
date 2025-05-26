# Ordinary File Handling in UNIX - Study Notes

## Displaying and Creating Files (cat)

### Purpose
- **cat** stands for "concatenate"
- Used to display file contents on screen
- Can also create new files

### Usage
```bash
cat filename           # Display file contents
cat file1 file2        # Display multiple files
cat > newfile          # Create new file (type content, press Ctrl+D to save)
cat >> existingfile    # Add content to existing file
```

### Examples
- `cat letter.txt` - shows contents of letter.txt
- `cat > notes.txt` - creates new file called notes.txt

---

## Copying a File (cp)

### Purpose
- **cp** copies files from one location to another
- Original file remains unchanged

### Usage
```bash
cp source destination     # Copy single file
cp file1 file2 file3 dir/ # Copy multiple files to directory
cp -r dir1 dir2          # Copy directory recursively
```

### Examples
- `cp report.txt backup.txt` - copies report.txt to backup.txt
- `cp *.txt documents/` - copies all .txt files to documents folder

---

## Deleting a File (rm)

### Purpose
- **rm** removes (deletes) files permanently
- Be careful - deleted files cannot be easily recovered

### Usage
```bash
rm filename           # Delete single file
rm file1 file2        # Delete multiple files
rm -r directory       # Delete directory and its contents
rm -i filename        # Interactive deletion (asks confirmation)
```

### Examples
- `rm oldfile.txt` - deletes oldfile.txt
- `rm -i important.doc` - asks before deleting important.doc

---

## Renaming/Moving a File (mv)

### Purpose
- **mv** moves files to different locations
- Also used to rename files
- Original file is moved, not copied

### Usage
```bash
mv oldname newname      # Rename file
mv file directory/      # Move file to directory
mv file1 file2 dir/     # Move multiple files
```

### Examples
- `mv report.txt final_report.txt` - renames file
- `mv document.txt archive/` - moves file to archive folder

---

## Paging Output (more)

### Purpose
- **more** displays file content one screen at a time
- Useful for viewing large files without overwhelming the screen

### Usage
```bash
more filename           # View file page by page
command | more          # Page output of any command
```

### Controls
- **Space** - next page
- **Enter** - next line
- **q** - quit

### Example
- `more bigfile.txt` - view large file page by page

---

## Printing a File (lp)

### Purpose
- **lp** sends files to printer
- Stands for "line printer"

### Usage
```bash
lp filename             # Print file
lp -n 3 filename        # Print 3 copies
lp -d printer filename  # Print to specific printer
```

### Example
- `lp report.txt` - prints report.txt

---

## Knowing File Type (file)

### Purpose
- **file** command identifies what type of file it is
- Tells you if it's text, image, executable, etc.

### Usage
```bash
file filename           # Check single file type
file *                  # Check all files in current directory
```

### Examples
- `file document.txt` - Output: "ASCII text"
- `file photo.jpg` - Output: "JPEG image data"

---

## Line, Word and Character Counting (wc)

### Purpose
- **wc** counts lines, words, and characters in files
- Stands for "word count"

### Usage
```bash
wc filename             # Shows lines, words, characters
wc -l filename          # Count only lines
wc -w filename          # Count only words
wc -c filename          # Count only characters
```

### Examples
- `wc essay.txt` - Output: "25 150 800 essay.txt" (25 lines, 150 words, 800 characters)
- `wc -l data.txt` - shows only number of lines

---

## Comparing Files (cmp)

### Purpose
- **cmp** compares two files byte by byte
- Shows first difference found

### Usage
```bash
cmp file1 file2         # Compare two files
cmp -s file1 file2      # Silent comparison (no output if same)
```

### Examples
- `cmp original.txt copy.txt` - compares two files
- If files are same: no output
- If different: shows first difference location

---

## Finding Common Between Two Files (comm)

### Purpose
- **comm** finds common and unique lines between two sorted files
- Shows three columns: unique to file1, unique to file2, common to both

### Usage
```bash
comm file1 file2        # Compare sorted files
comm -12 file1 file2    # Show only common lines
comm -3 file1 file2     # Hide common lines
```

### Example
- `comm list1.txt list2.txt` - compares two sorted lists

---

## Displaying File Differences (diff)

### Purpose
- **diff** shows detailed differences between files
- More detailed than cmp command

### Usage
```bash
diff file1 file2        # Show differences
diff -u file1 file2     # Unified format (easier to read)
```

### Examples
- `diff old_version.txt new_version.txt` - shows what changed
- Output uses symbols: < (from first file), > (from second file)

---

## Creating Archive File (tar)

### Purpose
- **tar** creates archive files (combines multiple files into one)
- Stands for "tape archive"

### Usage
```bash
tar -cf archive.tar files    # Create archive
tar -tf archive.tar          # List contents
tar -xf archive.tar          # Extract archive
```

### Examples
- `tar -cf backup.tar *.txt` - creates archive of all .txt files
- `tar -xf backup.tar` - extracts all files from archive

---

## Compress File (gzip)

### Purpose
- **gzip** compresses files to save space
- Compressed files have .gz extension

### Usage
```bash
gzip filename           # Compress file (original file is replaced)
gzip -k filename        # Keep original file
```

### Examples
- `gzip bigfile.txt` - creates bigfile.txt.gz and removes original
- File becomes smaller in size

---

## Uncompress File (gunzip)

### Purpose
- **gunzip** uncompresses .gz files
- Opposite of gzip

### Usage
```bash
gunzip filename.gz      # Uncompress file
gunzip -k filename.gz   # Keep compressed file
```

### Examples
- `gunzip document.txt.gz` - creates document.txt and removes .gz file

---

## Archive File (zip)

### Purpose
- **zip** creates compressed archive files
- Different from tar (tar doesn't compress by default)

### Usage
```bash
zip archive.zip files   # Create zip archive
zip -r archive.zip dir/ # Include directories
```

### Examples
- `zip backup.zip *.doc` - creates compressed archive of all .doc files

---

## Extract Compress File (unzip)

### Purpose
- **unzip** extracts files from zip archives

### Usage
```bash
unzip archive.zip       # Extract all files
unzip -l archive.zip    # List contents without extracting
```

### Examples
- `unzip project.zip` - extracts all files from project.zip

---

## Effects of cp, rm, and mv Commands on Directories

### cp (Copy) Command on Directories
- **Without -r flag**: Cannot copy directories
- **With -r flag**: Copies directory and all its contents recursively
- **Example**: `cp -r folder1 folder2` - copies entire folder1 to folder2

### rm (Remove) Command on Directories
- **Without -r flag**: Cannot delete non-empty directories
- **With -r flag**: Deletes directory and all contents recursively
- **rmdir command**: Removes only empty directories
- **Example**: `rm -r oldfolder` - deletes folder and everything inside

### mv (Move) Command on Directories
- **Works normally**: Can move/rename directories without special flags
- **Moves entire directory**: All contents move with the directory
- **Example**: `mv documents archive/` - moves entire documents folder

## Key Points for Exams
- **cat** - display/create files
- **cp** - copy (needs -r for directories)
- **rm** - delete (needs -r for directories)
- **mv** - move/rename (works on directories normally)
- **more** - view files page by page
- **wc** - count lines, words, characters
- **tar** - create archives
- **gzip/gunzip** - compress/uncompress
- **zip/unzip** - create/extract compressed archives
- Always be careful with rm command - deletion is permanent!
