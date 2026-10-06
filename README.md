# Linux-Fundamentals-with-Kali/Parrot
Basic Linux commands and understanding using Kali-Linux

## Lab Environment

- Operating System: Kali Linux/Parrot Linux
- Interface: Terminal
- Shell: Bash - Konsole
- Environment: Personal authorized cybersecurity lab

## Lab 01 - System Information

### Intro Terms and Concepts

Binaries - Binaries in Linux are executable files containing machine code (compiled programs) that the CPU can run directly.
They are typically found in directories like /bin, /usr/bin, /sbin, and /usr/sbin. Unlike scripts (which need an interpreter), binaries are ready-to-run native executables.

Case sensitivity - Case Sensitivity in Linux means the system treats uppercase and lowercase letters as distinct.

File and directory names are case-sensitive: File.txt, file.txt, and FILE.TXT are three different files.
Commands and binaries are also case-sensitive: ls works, but LS or Ls will not (unless a matching binary exists).
This applies to paths, environment variables, and most shell operations.

This behavior comes from the underlying file systems (ext4, XFS, Btrfs, etc.), which are case-sensitive by default.

Directory - Directories in Linux are folders that organize files and other directories in a hierarchical tree structure.

Everything starts from the root directory /.
Common system directories include /bin, /etc, /home, /usr, /var, and /tmp.
Paths are written with forward slashes (e.g., /home/user/documents).
Directories are themselves special files that contain a list of names and pointers (inodes) to the files or subdirectories they hold.

Home - Home directory in Linux is the personal directory assigned to each user, where their files, settings, and personal data are stored by default.

Path is usually /home/username (for regular users).
The root user’s home is /root.
Represented by the shortcut ~ (tilde) in the shell.
Contains user-specific configuration files (often hidden, starting with a dot, like .bashrc).

Distribution - Linux distribution (or “distro”) is a complete operating system built around the Linux kernel, packaged with system tools, libraries, a package manager, and often a desktop environment.
Popular examples include:

Ubuntu
Fedora
Debian
Arch Linux
Linux Mint
CentOS / Rocky Linux

Each distro differs in package management, release cycle, default software, and target use case (desktop, server, etc.).

root - root in Linux has two main meanings:

Root user
The superuser account (UID 0) with unrestricted privileges. It can perform any administrative task on the system.
Home directory: /root
Prompt usually ends with # instead of $

Root directory
The top-level directory of the filesystem hierarchy, written as /.
All other directories and files branch from it.

Script in Linux is a plain-text file containing a sequence of commands that the system executes in order, usually through an interpreter.

Common types: Bash (.sh), Python (.py), Perl, etc.
Starts with a shebang line (e.g., #!/bin/bash) that tells the system which interpreter to use.
Unlike binaries, scripts are human-readable and do not need to be compiled.
Made executable with chmod +x scriptname.

Shell in Linux is the command-line interface (CLI) that lets users interact with the operating system by typing commands.

It interprets the commands you enter and passes them to the kernel for execution.
The most common shell is Bash (Bourne Again Shell).
Other popular shells include Zsh, Fish, and Dash.
The shell is also a scripting language — scripts are usually written for a specific shell.

Terminal in Linux is the text-based interface (or the program that provides it) where you type commands to interact with the system.

It runs a shell (like Bash) inside it.
Can be a physical console or a terminal emulator (e.g., GNOME Terminal, Konsole, xterm, or the default terminal in most desktop environments).
Everything you type appears as text; there is no graphical interface inside the terminal itself.

### The Linux Filesystem
Linux Filesystem is a hierarchical tree structure that organizes all files and directories on the system.
Core Concepts

Everything starts at the root directory /.
Everything is treated as a file (regular files, directories, devices, sockets, etc.).
The filesystem is case-sensitive.
Paths use forward slashes (/).

Absolute vs Relative Paths

Absolute path: Starts from root → /home/user/documents/file.txt
Relative path: Starts from the current directory → documents/file.txt

Important Directories (Filesystem Hierarchy Standard)
/Directory - Purpose
/ - Root of the entire filesystem
/bin - Essential user binaries (commands)
/sbin - Essential system binaries (admin tools)
/etc - System configuration files
/home - User home directories
/root - Home directory of the root user
/usr - User programs and data
/usr/bin - Most user commands
/var - Variable data (logs, caches, mail, etc.)
/tmp - Temporary files (usually cleared on reboot)
/dev - Device files
/proc - Virtual filesystem with process & system info
/sys - Virtual filesystem for hardware/kernel info
/lib - Essential shared libraries
/opt - Optional / third-party software
/mnt - Temporary mount points
/media - Removable media (USB, CDs, etc.)

Key Characteristics

Single unified hierarchy — different partitions or drives are mounted into this tree (not separate drive letters like Windows).
Hidden files and directories start with a dot (.bashrc, .config).
Permissions and ownership control access to every file and directory.

### Commands in CLI
These are the most common commands used in the terminal.
ls - List files and directories

cd - Change the current directory
pwd - Print the current working directory
mkdir - Create a new directory
rmdir - Remove an empty directory
rm - Remove files or directories
cp - Copy files or directories
mv - Move or rename files and directories
touch - Create an empty file or update file timestamp
cat - Display the contents of a file
less - View file contents page by page
head - Show the first lines of a file
tail - Show the last lines of a file
echo - Display text or variables
man - Display the manual page of a command
clear - Clear the terminal screen
whoami - Show the current username
uname - Display system information
df - Show disk space usage
du - Show directory space usage
ps - List running processes
kill - Terminate a process
chmod - Change file or directory permissions
chown - Change file or directory ownership
sudo - Execute a command as the superuser
grep - Search for text patterns in files
find - Search for files and directories
history - Show command history
which - Show the full path of a command
file - Determine the type of a file
wc - Count lines, words, and characters
tar - Create or extract archive files
ssh - Connect to a remote system securely


Command:

```bash
whoami
```
### Result

```text
kali
```

### Explanation

The `whoami` command displays the username of the currently logged-in user.
The result shows that the current user is `kali`.
