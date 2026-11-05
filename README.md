# Basic File Operations in Linux

## Overview

Linux provides several command-line utilities for managing files, directories, permissions, and users.

This lab explores some fundamental Linux commands used to perform file operations, modify file permissions, execute scripts, and switch between user accounts.

Understanding these operations is essential for Linux system administration and cybersecurity.

## Lab Objective

Learn how to use basic file operations in the Linux operating system.

## Lab Purpose

Understand how Linux handles files, file permissions, ownership, and execution privileges.

## Lab Environment

- **Operating System:** Kali Linux
- **Environment:** Virtual Machine
- **Shell:** Linux Terminal
- **Privileges:** Root and standard user

## Lab Walkthrough

### Task 1: List Files and Directories Using `ls`

The `ls` command is used to list files and directories within a directory.

Run:

```bash
ls
```

To explore additional options, use:

```bash
ls --help
```

To display all files, including hidden files, alongside detailed information, run:

```bash
ls -al
```

The output provides several details about each file and directory:

| Information | Description |
|---|---|
| Permissions | File type and access permissions. |
| Links | Number of hard links. |
| Owner | User who owns the file. |
| Group | Group associated with the file. |
| Size | File size in bytes. |
| Date/Time | Last modification date and time. |
| Name | File or directory name. |

Hidden files in Linux generally have names beginning with a period (`.`).

### Task 2: Create an Empty File Using `touch`

The `touch` command can create an empty file if it does not already exist.

Create a file named `example.txt` in the root user's home directory:

```bash
touch /root/example.txt
```

If you are not operating as root, use:

```bash
sudo touch /root/example.txt
```

The command creates an empty file named `example.txt`.

### Task 3: Edit a File Using `nano`

The `nano` command opens a terminal-based text editor.

Open the file:

```bash
nano /root/example.txt
```

Enter the following text:

```text
THIS IS A FILE FOR PRACTICING
```

To save and exit:

1. Press `Ctrl + O` to save.
2. Press `Enter` to confirm the filename.
3. Press `Ctrl + X` to exit Nano.

### Task 4: Display File Contents Using `cat`

The `cat` command, short for concatenate, can display the contents of a file directly in the terminal.

Display the contents of the file created earlier:

```bash
cat /root/example.txt
```

The terminal should display:

```text
THIS IS A FILE FOR PRACTICING
```

The `cat` command is also useful for combining files and creating or redirecting file contents.

### Task 5: Create and Execute a Script Using File Permissions

Unlike Windows, Linux does not rely exclusively on file extensions to determine whether a file can be executed.

Linux uses file permissions to determine whether a user can read, write, or execute a file.

#### 1. Create a Shell Script

Create a file named `file` in the root user's home directory:

```bash
echo '#!/bin/bash
echo "hello world"' > ~/file
```

Verify its contents:

```bash
cat ~/file
```

Expected content:

```bash
#!/bin/bash
echo "hello world"
```

The first line is called a shebang. It specifies the interpreter used to execute the script.

#### 2. Assign Executable Permissions

Use the `chmod` command to modify the file's permissions.

```bash
chmod a+x ~/file
```

The `a+x` option adds execute permission for all users:

- User (owner)
- Group
- Others

Verify the permissions:

```bash
ls -l ~/file
```

The permission output should show execute permissions for all three categories.

#### 3. Execute Using a Relative Path

Navigate to the root user's home directory:

```bash
cd /root
```

Execute the script using a relative path:

```bash
./file
```

Expected output:

```text
hello world
```

The `./` prefix tells Linux to execute the file from the current directory.

#### 4. Execute Using an Absolute Path

Execute the same script using its full path:

```bash
/root/file
```

Expected output:

```text
hello world
```

This demonstrates the difference between relative and absolute file paths.

### Task 6: Switch Users Using `su`

Linux allows users to switch between accounts without logging out of the current session.

To switch from a standard user to the root account, execute:

```bash
sudo su -
```

Enter the current user's sudo password when prompted.

The `-` option starts a login shell and loads the target user's login environment.

To switch from root to another user:

```bash
su - username
```

Replace `username` with the account you want to switch to.

When root switches to an unprivileged local user, a password is normally not required.

To confirm the currently active user, run:

```bash
whoami
```

## Important Commands Covered

| Command | Function |
|---|---|
| `ls` | Lists files and directories. |
| `ls -al` | Displays hidden files and detailed file information. |
| `touch` | Creates an empty file. |
| `nano` | Opens a terminal-based text editor. |
| `cat` | Displays or combines file contents. |
| `chmod` | Changes file permissions. |
| `./file` | Executes a file from the current directory. |
| `sudo su -` | Switches to a root login shell. |
| `su - username` | Switches to another user's login shell. |
| `whoami` | Displays the current username. |

## Understanding Linux File Permissions

Linux uses three primary permission categories:

- **r (Read):** Allows a user to read a file.
- **w (Write):** Allows a user to modify a file.
- **x (Execute):** Allows a user to execute a file.

These permissions apply to three categories:

- **u:** User/Owner.
- **g:** Group.
- **o:** Others.

For example:

```bash
chmod u+x file
```

Adds execute permission for the file owner.

```bash
chmod g+x file
```

Adds execute permission for the group.

```bash
chmod o+x file
```

Adds execute permission for others.

```bash
chmod a+x file
```

Adds execute permission for everyone.

## Practical Applications in Cybersecurity

Understanding Linux file operations and permissions is important in cybersecurity because they directly affect system access and security.

These skills are useful for:

- Managing files and directories on Linux systems.
- Understanding file ownership and access permissions.
- Identifying executable files.
- Managing shell scripts.
- Understanding privilege escalation risks associated with excessive permissions.
- Switching between standard and privileged accounts.
- Performing basic Linux system administration.

## Screenshots / Evidence

The following screenshots are recommended to document the practical work.

Save captured screenshots in a folder named `screenshots/` in the repository.

1. **`01-ls-directory-listing.png`** — Terminal showing the output of `ls` and `ls -al`.
2. **`02-touch-file-creation.png`** — Terminal showing the creation of `example.txt`.
3. **`03-nano-file-editing.png`** — Nano editor displaying the practice text.
4. **`04-cat-file-content.png`** — Terminal displaying the contents of `example.txt`.
5. **`05-script-creation.png`** — Terminal showing the shell script contents.
6. **`06-chmod-executable-permissions.png`** — Terminal showing the executable permissions after running `chmod a+x`.
7. **`07-script-execution.png`** — Terminal showing successful execution using relative and absolute paths.
8. **`08-user-switching.png`** — Terminal showing user switching and verification using `whoami`.

*Note: Add the actual screenshots after capturing them. Do not use placeholders as evidence of completed execution.*

## Conclusion

This lab introduces essential Linux file operations and user-management commands.

Understanding how Linux handles files, permissions, executable scripts, and user privileges provides a foundation for more advanced system administration and cybersecurity activities.
