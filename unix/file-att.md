# File Attributes in UNIX - Study Notes

## File and Directory Attributes Listing

### ls -l Command
- **Purpose**: Shows detailed file attributes
- **Usage**: `ls -l` or `ll`
- **Output Format**: 
```
-rw-r--r-- 1 user group 1024 May 25 10:30 filename
```

### Attribute Components
1. **File type and permissions** (-rw-r--r--)
2. **Link count** (1)
3. **Owner name** (user)
4. **Group name** (group)
5. **File size** (1024 bytes)
6. **Last modification time** (May 25 10:30)
7. **File name** (filename)

---

## File Ownership

### Types of Ownership
1. **User/Owner** - Person who created the file
2. **Group** - Collection of users who share access
3. **Others** - All other users on the system

### Viewing Ownership
- `ls -l filename` - shows owner and group
- `id` - shows your user ID and group memberships

---

## File Permissions

### Permission Types
1. **Read (r)** - Can view file contents
2. **Write (w)** - Can modify file contents
3. **Execute (x)** - Can run the file as a program

### Permission Categories
1. **User/Owner permissions** - First 3 characters
2. **Group permissions** - Next 3 characters  
3. **Other permissions** - Last 3 characters

### Reading Permission Format
```
-rw-r--r--
- = file type
rw- = user permissions (read, write, no execute)
r-- = group permissions (read only)
r-- = other permissions (read only)
```

---

## Changing File Permissions

### Relative Permission Method (chmod with symbols)

#### Adding Permissions
```bash
chmod u+x filename      # Add execute for user
chmod g+w filename      # Add write for group
chmod o+r filename      # Add read for others
chmod a+x filename      # Add execute for all (user, group, others)
```

#### Removing Permissions
```bash
chmod u-w filename      # Remove write from user
chmod g-x filename      # Remove execute from group
chmod o-r filename      # Remove read from others
```

#### Setting Specific Permissions
```bash
chmod u=rw filename     # Set user to read-write only
chmod g=r filename      # Set group to read only
chmod o= filename       # Remove all permissions from others
```

### Absolute Permission Method (chmod with numbers)

#### Permission Values
- **Read (r)** = 4
- **Write (w)** = 2
- **Execute (x)** = 1

#### Common Permission Combinations
- **7** = rwx (4+2+1) = read, write, execute
- **6** = rw- (4+2) = read, write
- **5** = r-x (4+1) = read, execute
- **4** = r-- (4) = read only
- **0** = --- = no permissions

#### Examples
```bash
chmod 755 filename      # rwxr-xr-x (user: all, group: read+execute, others: read+execute)
chmod 644 filename      # rw-r--r-- (user: read+write, group: read, others: read)
chmod 600 filename      # rw------- (user: read+write, others: no access)
chmod 777 filename      # rwxrwxrwx (all permissions for everyone)
```

---

## Changing File Ownership

### Changing User Ownership
```bash
chown newuser filename          # Change owner to newuser
chown newuser:newgroup filename # Change both owner and group
```

### Examples
```bash
chown john report.txt           # Change owner to john
sudo chown root important.txt   # Change owner to root (needs sudo)
```

---

## Changing Group Ownership

### chgrp Command
```bash
chgrp newgroup filename         # Change group ownership
chgrp students *.txt            # Change group for all .txt files
```

### Using chown for Group
```bash
chown :newgroup filename        # Change only group (note the colon)
```

---

## File System and Inodes

### What is an Inode?
- **Inode** = Index node
- **Purpose**: Stores file metadata (information about file)
- **Contents**: File size, permissions, ownership, timestamps, disk location
- **Not stored**: File name (stored in directory)

### Viewing Inode Information
```bash
ls -i filename          # Show inode number
stat filename           # Show detailed inode information
```

---

## Hard Link

### Definition
- **Hard link** creates another name for the same file
- Both names point to the same inode
- Deleting one name doesn't delete the file until all links are removed

### Creating Hard Links
```bash
ln original.txt hardlink.txt    # Create hard link
```

### Characteristics
- Same inode number as original
- Same file size and permissions
- Cannot cross file systems
- Cannot link to directories (usually)

---

## Soft Link (Symbolic Link)

### Definition
- **Soft link** creates a pointer to another file
- Like a shortcut that points to the original file
- Has its own inode

### Creating Soft Links
```bash
ln -s original.txt softlink.txt     # Create soft link
ln -s /path/to/file linkname        # Link to file with full path
```

### Characteristics
- Different inode number
- Small file size (just stores path)
- Can cross file systems
- Can link to directories
- Breaks if original file is deleted

---

## Significance of File Attributes for Directory

### Directory Permissions
- **Read (r)** - Can list directory contents (`ls`)
- **Write (w)** - Can create/delete files in directory
- **Execute (x)** - Can enter directory (`cd`) and access files

### Important Notes
- Need execute permission to access files inside directory
- Need write permission to create/delete files
- Directory permissions affect file access

---

## Default Permissions and umask

### Default Permissions
- **Files**: 666 (rw-rw-rw-) - no execute by default
- **Directories**: 777 (rwxrwxrwx) - full permissions

### umask (User Mask)
- **Purpose**: Sets default permission restrictions
- **How it works**: Subtracts from default permissions

### Common umask Values
```bash
umask 022       # Default: files=644, directories=755
umask 077       # Restrictive: files=600, directories=700
umask           # Show current umask value
```

### Calculating Final Permissions
- **Files**: 666 - umask = final permission
- **Directories**: 777 - umask = final permission
- **Example**: umask 022 → files get 644, directories get 755

---

## Listing Modification and Access Time

### Time Types
1. **Access time (atime)** - Last time file was read
2. **Modify time (mtime)** - Last time file content was changed
3. **Change time (ctime)** - Last time file attributes were changed

### Viewing Times
```bash
ls -l filename          # Shows modification time
ls -la filename         # Shows access time
ls -lc filename         # Shows change time
stat filename           # Shows all three times
```

---

## Time Stamp Changing (touch)

### Purpose
- **touch** command changes file timestamps
- Can also create empty files

### Usage
```bash
touch filename          # Update timestamps to current time (creates file if doesn't exist)
touch -a filename       # Update only access time
touch -m filename       # Update only modification time
touch -t 202505251030 file  # Set specific time (YYYYMMDDhhmm)
```

### Examples
```bash
touch newfile.txt       # Creates empty file with current timestamp
touch -a document.txt   # Updates access time to now
```

---

## File Locating (find)

### Purpose
- **find** command searches for files and directories
- Very powerful with many options

### Basic Usage
```bash
find /path -name "filename"     # Find file by name
find . -name "*.txt"            # Find all .txt files in current directory
find /home -user john           # Find files owned by john
```

### Common find Options
```bash
find . -type f              # Find only files
find . -type d              # Find only directories
find . -size +1M            # Find files larger than 1MB
find . -mtime -7            # Find files modified in last 7 days
find . -perm 755            # Find files with specific permissions
```

### Advanced Examples
```bash
find /var/log -name "*.log" -mtime +30  # Find log files older than 30 days
find . -name "*.tmp" -delete            # Find and delete temporary files
find /home -user john -exec ls -l {} \; # Find john's files and list them
```

## Key Points for Exams

### Permission Numbers to Remember
- **755** - rwxr-xr-x (common for executables)
- **644** - rw-r--r-- (common for files)
- **600** - rw------- (private files)
- **777** - rwxrwxrwx (full permissions)

### Important Commands
- **chmod** - change permissions
- **chown** - change ownership
- **chgrp** - change group
- **umask** - set default permissions
- **find** - locate files
- **touch** - change timestamps
- **ln** - create links

### Key Differences
- **Hard link**: Same inode, cannot cross filesystems
- **Soft link**: Different inode, can cross filesystems, breaks if original deleted
- **Absolute permissions**: Use numbers (755, 644)
- **Relative permissions**: Use symbols (u+x, g-w)
