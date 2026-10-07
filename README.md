
# Linux-Fundamentals-with-Kali/Parrot

Basic Linux commands and fundamental concepts using Kali Linux or Parrot OS.

## Lab Environment

- **Operating System**: Kali Linux or Parrot Linux
- **Interface**: Terminal
- **Shell**: Bash (Konsole)
- **Environment**: Personal authorized cybersecurity lab

---

## Linux - System Information

### Intro Terms and Concepts

**Binaries**  
Binaries in Linux are executable files containing machine code (compiled programs) that the CPU can run directly.  
They are typically found in directories like `/bin`, `/usr/bin`, `/sbin`, and `/usr/sbin`. Unlike scripts (which need an interpreter), binaries are ready-to-run native executables.

**Case Sensitivity**  
Linux treats uppercase and lowercase letters as distinct.  
- File and directory names are case-sensitive: `File.txt`, `file.txt`, and `FILE.TXT` are three different files.  
- Commands and binaries are also case-sensitive: `ls` works, but `LS` or `Ls` will not (unless a matching binary exists).  
- This applies to paths, environment variables, and most shell operations.  
- This behavior comes from the underlying file systems (ext4, XFS, Btrfs, etc.), which are case-sensitive by default.

**Directory**  
Directories in Linux are folders that organize files and other directories in a hierarchical tree structure.  
- Everything starts from the root directory `/`.  
- Common system directories include `/bin`, `/etc`, `/home`, `/usr`, `/var`, and `/tmp`.  
- Paths are written with forward slashes (e.g., `/home/user/documents`).  
- Directories are themselves special files that contain a list of names and pointers (inodes) to the files or subdirectories they hold.

**Home Directory**  
The home directory is the personal directory assigned to each user, where their files, settings, and personal data are stored by default.  
- Path is usually `/home/username` (for regular users).  
- The root user’s home is `/root`.  
- Represented by the shortcut `~` (tilde) in the shell.  
- Contains user-specific configuration files (often hidden, starting with a dot, like `.bashrc`).

**Distribution (Distro)**  
A Linux distribution is a complete operating system built around the Linux kernel, packaged with system tools, libraries, a package manager, and often a desktop environment.  

Popular examples include:  
- Ubuntu  
- Fedora  
- Debian  
- Arch Linux  
- Linux Mint  
- CentOS / Rocky Linux  

Each distro differs in package management, release cycle, default software, and target use case (desktop, server, etc.).

**root**  
`root` has two main meanings:

1. **Root User**  
   The superuser account (UID 0) with unrestricted privileges. It can perform any administrative task on the system.  
   - Home directory: `/root`  
   - Prompt usually ends with `#` instead of `$`

2. **Root Directory**  
   The top-level directory of the filesystem hierarchy, written as `/`.  
   All other directories and files branch from it.

**Script**  
A script is a plain-text file containing a sequence of commands that the system executes in order, usually through an interpreter.  
- Common types: Bash (`.sh`), Python (`.py`), Perl, etc.  
- Starts with a shebang line (e.g., `#!/bin/bash`) that tells the system which interpreter to use.  
- Unlike binaries, scripts are human-readable and do not need to be compiled.  
- Made executable with `chmod +x scriptname`.

**Shell**  
The shell is the command-line interface (CLI) that lets users interact with the operating system by typing commands.  
- It interprets the commands you enter and passes them to the kernel for execution.  
- The most common shell is **Bash** (Bourne Again Shell).  
- Other popular shells include Zsh, Fish, and Dash.  
- The shell is also a scripting language — scripts are usually written for a specific shell.

**Terminal**  
The terminal is the text-based interface (or the program that provides it) where you type commands to interact with the system.  
- It runs a shell (like Bash) inside it.  
- Can be a physical console or a terminal emulator (e.g., GNOME Terminal, Konsole, xterm, or the default terminal in most desktop environments).  
- Everything you type appears as text; there is no graphical interface inside the terminal itself.

---

### The Linux Filesystem

The Linux filesystem is a hierarchical tree structure that organizes all files and directories on the system.

**Core Concepts**  
- Everything starts at the root directory `/`.  
- Everything is treated as a file (regular files, directories, devices, sockets, etc.).  
- The filesystem is case-sensitive.  
- Paths use forward slashes (`/`).

**Absolute vs Relative Paths**  
- **Absolute path**: Starts from root → `/home/user/documents/file.txt`  
- **Relative path**: Starts from the current directory → `documents/file.txt`

**Important Directories (Filesystem Hierarchy Standard)**

| Directory    | Purpose                                      |
|--------------|----------------------------------------------|
| `/`          | Root of the entire filesystem                |
| `/bin`       | Essential user binaries (commands)           |
| `/sbin`      | Essential system binaries (admin tools)      |
| `/etc`       | System configuration files                   |
| `/home`      | User home directories                        |
| `/root`      | Home directory of the root user              |
| `/usr`       | User programs and data                       |
| `/usr/bin`   | Most user commands                           |
| `/var`       | Variable data (logs, caches, mail, etc.)     |
| `/tmp`       | Temporary files (usually cleared on reboot)  |
| `/dev`       | Device files                                 |
| `/proc`      | Virtual filesystem with process & system info|
| `/sys`       | Virtual filesystem for hardware/kernel info  |
| `/lib`       | Essential shared libraries                   |
| `/opt`       | Optional / third-party software              |
| `/mnt`       | Temporary mount points                       |
| `/media`     | Removable media (USB, CDs, etc.)             |

**Key Characteristics**  
- Single unified hierarchy — different partitions or drives are mounted into this tree (not separate drive letters like Windows).  
- Hidden files and directories start with a dot (`.bashrc`, `.config`).  
- Permissions and ownership control access to every file and directory.

---

### Commands in CLI

These are the most common commands used in the terminal.

| Command   | Description                                      |
|-----------|--------------------------------------------------|
| `ls`      | List files and directories                       |
| `cd`      | Change the current directory                     |
| `pwd`     | Print the current working directory              |
| `mkdir`   | Create a new directory                           |
| `rmdir`   | Remove an empty directory                        |
| `rm`      | Remove files or directories                      |
| `cp`      | Copy files or directories                         |
| `mv`      | Move or rename files and directories              |
| `touch`   | Create an empty file or update file timestamp    |
| `cat`     | Display the contents of a file                   |
| `less`    | View file contents page by page                  |
| `head`    | Show the first lines of a file                   |
| `tail`    | Show the last lines of a file                    |
| `echo`    | Display text or variables                        |
| `man`     | Display the manual page of a command             |
| `clear`   | Clear the terminal screen                        |
| `whoami`  | Show the current username                        |
| `uname`   | Display system information                       |
| `df`      | Show disk space usage                            |
| `du`      | Show directory space usage                       |
| `ps`      | List running processes                           |
| `kill`    | Terminate a process                              |
| `chmod`   | Change file or directory permissions             |
| `chown`   | Change file or directory ownership               |
| `sudo`    | Execute a command as the superuser               |
| `grep`    | Search for text patterns in files                |
| `find`    | Search for files and directories                  |
| `history` | Show command history                             |
| `which`   | Show the full path of a command                  |
| `file`    | Determine the type of a file                     |
| `wc`      | Count lines, words, and characters               |
| `tar`     | Create or extract archive files                  |
| `ssh`     | Connect to a remote system securely              |

---

### Command-Line Options (Flags / Switches)

Options modify how commands work.

#### 1. Basic Structure of a Command

```bash
command [options] [arguments]
```

- **command** → the program (e.g. `ls`, `rm`, `cp`)  
- **options** → modify the behavior of the command  
- **arguments** → the things the command acts on (files, directories, etc.)

#### 2. Types of Options

| Type              | Syntax                  | Example                      | Meaning                          |
|-------------------|-------------------------|------------------------------|----------------------------------|
| Short option      | `-x`                    | `ls -l`                      | Single letter                    |
| Multiple short    | `-xyz`                  | `ls -lah`                    | Combine several short options    |
| Long option       | `--word`                | `ls --all`                   | Full word (easier to read)       |
| Option with value | `-n 10` or `--lines=10` | `head -n 20 file.txt`        | Option needs a value             |

#### 3. How to Discover Options

Almost every command supports these two:

```bash
command --help          # Quick help
man command             # Full manual page
```

Example:
```bash
ls --help
man ls
```

#### 4. Common Options You’ll Use Often

**ls** (list files)
- `-l` → long format (permissions, size, date)
- `-a` → show hidden files
- `-h` → human-readable sizes
- `-R` → recursive (show subdirectories)  
Example: `ls -lah`

**rm** (remove)
- `-r` or `-R` → recursive (required for directories)
- `-f` → force (no confirmation)
- `-i` → interactive (ask before deleting)  
Example: `rm -rf folder/`

**cp** (copy)
- `-r` → recursive (copy directories)
- `-i` → ask before overwriting
- `-v` → verbose (show what’s being copied)  
Example: `cp -rv source/ destination/`

**mv** (move/rename)
- `-i` → ask before overwriting
- `-v` → verbose  
Example: `mv -i oldname.txt newname.txt`

**mkdir**
- `-p` → create parent directories if needed  
Example: `mkdir -p projects/2025/linux`

**grep** (search text)
- `-i` → case-insensitive
- `-r` → recursive
- `-n` → show line numbers
- `-v` → invert match (show non-matching lines)  
Example: `grep -rn "error" /var/log/`

**tar** (archives)
- `-c` → create archive
- `-x` → extract
- `-v` → verbose
- `-f` → specify filename
- `-z` → use gzip compression  
Example: `tar -czvf backup.tar.gz folder/`

**chmod** (permissions)
- `+x` → add execute permission
- `-R` → recursive  
Example: `chmod +x script.sh` or `chmod -R 755 folder/`

#### 5. Useful Universal Options

| Option              | Meaning                     |
|---------------------|-----------------------------|
| `--help`            | Show help                   |
| `-v` / `--verbose`  | Show detailed output        |
| `-q` / `--quiet`    | Suppress output             |
| `-f`                | Force (no prompts)          |
| `-r` / `-R`         | Recursive                   |
| `-i`                | Interactive (ask first)     |

#### Practice Examples

```bash
ls -lah /home
rm -i *.tmp
cp -rv documents/ backup/
mkdir -p ~/projects/linux/notes
grep -i "failed" /var/log/syslog
tar -xzvf archive.tar.gz
```

The `whoami` command displays the username of the currently logged-in user.

# Working with Files and Directories in Linux

A practical guide to creating, editing, modifying, and managing files and directories in the Linux terminal (Kali / Parrot).

---

## 1. Working with Directories

| Action                      | Command       | Example                              | Notes |
|-----------------------------|---------------|--------------------------------------|-------|
| Create directory            | `mkdir`       | `mkdir notes`                        | Creates a single folder |
| Create nested directories   | `mkdir -p`    | `mkdir -p projects/linux/lab1`       | Creates parent folders if needed |
| Navigate into directory     | `cd`          | `cd projects/linux`                  | Change directory |
| Go up one level             | `cd ..`       | `cd ..`                              | Move to parent directory |
| Go to home directory        | `cd` or `cd ~`| `cd`                                 | Returns to your home directory |
| Show current path           | `pwd`         | `pwd`                                | Print working directory |
| List contents               | `ls`          | `ls -lah`                            | `-l` long, `-a` hidden, `-h` human-readable |
| Remove empty directory      | `rmdir`       | `rmdir notes`                        | Only works if directory is empty |
| Remove directory + contents | `rm -r`       | `rm -r projects`                     | Recursive delete (be careful!) |
| Force remove                | `rm -rf`      | `rm -rf old_folder`                  | No confirmation + recursive |

---

## 2. Creating Files

| Method                        | Command / Example                        | Description |
|-------------------------------|------------------------------------------|-----------|
| Create empty file             | `touch file.txt`                         | Creates a new empty file (or updates timestamp) |
| Create file with content      | `echo "Hello World" > file.txt`          | Creates file and writes text (overwrites if exists) |
| Append text to file           | `echo "More text" >> file.txt`           | Adds text to the end of the file |
| Create using cat              | `cat > file.txt`                         | Type content, then press `Ctrl + D` to save |
| Create using text editor      | `nano file.txt`                          | Opens nano editor (easiest for beginners) |

---

## 3. Editing Files

| Editor   | Command                  | How to Use                                      | Best For |
|----------|--------------------------|--------------------------------------------------|----------|
| nano     | `nano file.txt`          | Edit → `Ctrl + O` (save) → `Ctrl + X` (exit)    | Beginners |
| vim      | `vim file.txt`           | Press `i` to insert → `Esc` → `:wq` to save & quit | Advanced users |
| cat      | `cat >> file.txt`        | Type text → `Ctrl + D` to finish                | Quick appends |
| Redirect | `echo "text" > file.txt` | Overwrites the entire file                      | Simple changes |

**Recommended for beginners:** Use `nano`.

---

## 4. Viewing File Contents

| Command   | Example                     | Description |
|-----------|-----------------------------|-----------|
| `cat`     | `cat file.txt`              | Shows entire file |
| `less`    | `less file.txt`             | Scroll through file (`q` to quit) |
| `head`    | `head -n 20 file.txt`       | Shows first 20 lines |
| `tail`    | `tail -n 20 file.txt`       | Shows last 20 lines |
| `tail -f` | `tail -f /var/log/syslog`   | Live view (useful for logs) |

---

## 5. Copying, Moving, and Renaming

| Action                | Command | Example                          |
|-----------------------|---------|----------------------------------|
| Copy file             | `cp`    | `cp file.txt backup.txt`         |
| Copy directory        | `cp -r` | `cp -r notes/ notes_backup/`     |
| Move / Rename         | `mv`    | `mv oldname.txt newname.txt`     |
| Move file to folder   | `mv`    | `mv file.txt documents/`         |
| Rename directory      | `mv`    | `mv old_folder new_folder`       |

---

## 6. Deleting Files

| Action                | Command  | Example                | Warning |
|-----------------------|----------|------------------------|---------|
| Delete file           | `rm`     | `rm file.txt`          | Permanent |
| Delete multiple files | `rm`     | `rm file1.txt file2.txt` | - |
| Interactive delete    | `rm -i`  | `rm -i *.txt`          | Asks for confirmation |
| Force delete          | `rm -f`  | `rm -f file.txt`       | No confirmation |

> **Warning:** There is no Trash/Recycle Bin in the terminal. `rm` permanently deletes files.

---

## 7. Quick Practice Workflow

```bash
# Create a project folder
mkdir -p ~/labs/linux/lab1
cd ~/labs/linux/lab1

# Create files
touch notes.txt
echo "This is my first note" > notes.txt
echo "Second line" >> notes.txt

# Edit the file
nano notes.txt

# View content
cat notes.txt

# Make a backup
cp notes.txt notes_backup.txt

# Rename a file
mv notes_backup.txt notes_old.txt

# Create another folder and move file into it
mkdir archive
mv notes_old.txt archive/
```
8. File Permissions
Every file and directory in Linux has permissions that control who can read, write, or execute them.
Permission Types
## 8. File Permissions

Every file and directory in Linux has permissions that control who can read, write, or execute them.

### Permission Types

| Symbol | Meaning  | Description                                       |
|--------|----------|---------------------------------------------------|
| `r`    | Read     | View file contents / list directory               |
| `w`    | Write    | Modify file / create or delete files in directory |
| `x`    | Execute  | Run a file as a program / enter a directory       |

### Permission Categories

| Category | Symbol | Meaning                              |
|----------|--------|--------------------------------------|
| Owner    | `u`    | The user who owns the file           |
| Group    | `g`    | Users who belong to the file’s group |
| Others   | `o`    | Everyone else                        |
| All      | `a`    | Owner + Group + Others               |

### Viewing Permissions

```bash
ls -l
```
**Example output:**
```text
-rw-r--r-- 1 kali kali 123 Oct 5 20:00 notes.txt
```

**Breakdown of `-rw-r--r--`:**
* **Type:** `-` = Regular file (`d` = Directory)
* **Owner (`u`):** `rw-` (Read & Write)
* **Group (`g`):** `r--` (Read-only)
* **Others (`o`):** `r--` (Read-only)

---

### Changing Permissions with `chmod`

#### Symbolic Method (Recommended for Beginners)

```bash
chmod u+x file.txt               # Add execute permission for owner
chmod g-w file.txt               # Remove write permission from group
chmod o+r file.txt               # Add read permission for others
chmod a+x script.sh              # Add execute for all users
chmod u=rwx,g=rx,o= file.txt     # Assign discrete permissions per scope
```

#### Numeric (Octal) Method

| Value | Permission | Description |
| :---: | :---: | :--- |
| **`4`** | `r` | Read |
| **`2`** | `w` | Write |
| **`1`** | `x` | Execute |
| **`0`** | `-` | No permissions |

Values are summed across each category:

| Total | Meaning | Breakdown |
| :---: | :--- | :--- |
| **`7`** | `rwx` | $4 + 2 + 1$ |
| **`6`** | `rw-` | $4 + 2$ |
| **`5`** | `r-x` | $4 + 1$ |
| **`4`** | `r--` | $4$ |
| **`0`** | `---` | $0$ |

**Examples:**
```bash
chmod 755 script.sh     # Owner: rwx (7) | Group: r-x (5) | Others: r-x (5)
chmod 644 file.txt      # Owner: rw- (6) | Group: r-- (4) | Others: r-- (4)
chmod 700 private.txt   # Owner: rwx (7) | Group: --- (0) | Others: --- (0)
```

---

### Changing Ownership with `chown`

```bash
sudo chown user:group file.txt
sudo chown kali:kali file.txt
sudo chown -R kali:kali folder/     # Recursively update folder contents
```

---

### Common Permission Configurations

| Permission | Octal | Typical Use Case |
| :---: | :---: | :--- |
| `rwxr-xr-x` | **755** | Shell scripts, shared binaries, executable programs |
| `rw-r--r--` | **644** | Standard user files, documents, web assets |
| `rwx------` | **700** | Private scripts, SSH key folders (`~/.ssh`), secure directories |
| `rwxrwxrwx` | **777** | Full global access (security risk; avoid in production) |
