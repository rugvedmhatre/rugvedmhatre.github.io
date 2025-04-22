---
title: "Book Notes: Linux Programming Interface - Linux Fundamentals"
date: 2025-04-21T18:30:00+05:30
toc: true
toc_label: "Notes"
category: book-notes
excerpt: Notes on Linux Fundamentals from "Linux Programming Interface" by Michael Kerrisk
seo_title: Linux Fundamentals from Linux Programming Interface Book
seo_description: Notes on Linux Fundamentals from "Linux Programming Interface" by Michael Kerrisk
---

_These are my notes on Linux Fundamentals from the "Linux Programming Interface" book by Michael Kerrisk_

# The Kernel

The kernel is the core software component that manages and allocates a computer’s resources, such as the CPU, memory, and hardware devices.

While it’s technically possible to run programs without a kernel, having one greatly simplifies program development and execution. The kernel provides a structured software layer that efficiently manages limited system resources, offering greater power, flexibility, and abstraction for developers.

> On Linux systems, the kernel executable is usually found at `/boot/vmlinuz`. The name cleverly mirrors the word “vmlinux”, with the `z` at the end indicating that it’s a compressed version of the kernel.

## Tasks performed by the Kernel

### Process Scheduling

- Linux is a preemptive multitasking operating system.
- Multitasking allows multiple processes to reside in memory simultaneously, with each receiving CPU time.
- Preemptive scheduling means the kernel decides which process runs and for how long, ensuring fair and efficient CPU allocation.

### Memory Management

- Linux uses virtual memory management, which provides two key benefits:
  - Process Isolation: Each process is given a separate address space, protecting it from unauthorized access or interference by other processes or the kernel.
  - Efficient Memory Use: Only parts of a process need to be kept in RAM at any time, allowing more processes to coexist in memory. This improves CPU utilization by increasing the chance that at least one runnable process is always available.

### File System Management

- The kernel manages the file system, enabling users and programs to create, read, update, and delete files.
- It abstracts physical storage devices, providing a unified and hierarchical file system view.

### Process Creation and Termination

- The kernel can load and start a new program in memory, turning it into an independent process.
- It provides necessary resources (CPU time, memory, file access).
- Once the process finishes, the kernel reclaims its resources for future use.

### Device Access and Management

- Devices like keyboards, mice, disks, and monitors enable interaction between the system and the outside world.
- The kernel offers a standardized interface to access these devices.
- It also handles concurrent access, ensuring multiple processes can share devices without conflict.

### Networking

- The kernel is responsible for transmitting and receiving data over networks on behalf of user processes.
- It handles packet routing, socket communication, and ensures data reaches its destination efficiently.

### System Call Interface (API)

- Programs interact with the kernel via system calls, which act as secure entry points into kernel space.
- Examples: read(), write(), fork(), exec(), open().
- The system call interface abstracts hardware details and enforces privilege boundaries.

### Multiuser Support & Virtual Environments
- Linux supports multiple users, each with:
  - A home directory
  - Isolated processes and memory
  - Independent access to files and devices
- The kernel ensures resource isolation and arbitration, allowing users and programs to operate as if each had their own private machine.

## Kernel Mode and User Mode

Modern CPUs operate in at least two modes: user mode and kernel mode (also called supervisor mode). The CPU switches between these modes using special hardware instructions.
- User mode restricts access to user space memory. Any attempt to access kernel space causes a hardware exception.
- Kernel mode has full access to both user and kernel memory.

Certain critical operations—like halting the system, managing memory, or performing device I/O—can only be done in kernel mode. This separation protects the system by preventing user programs from interfering with kernel data or operations.

## Process View vs Kernel View

### Process View

From a process’s perspective:
- It runs in isolation, unaware of the system’s global state.
- It doesn’t know when it will be scheduled, which other processes are running, or when events like signals or IPC will occur.
- It lacks visibility into:
  - Memory location (RAM vs. swap)
  - Disk location of files (accesses files by name only)
  - Other processes (no direct access)
  - Devices (cannot directly communicate with hardware)
- It cannot create or terminate itself without help from the kernel.

### Kernel View

From the kernel’s perspective:
- It has full control over the system and all processes.
- It:
  - Schedules processes (who runs, when, and for how long)
  - Maintains data about process state, memory mapping, and file locations
  - Manages interprocess communication (IPC)
  - Handles process creation and termination
  - Manages all I/O operations through device drivers
- The kernel acts as the coordinator, ensuring processes can run safely and efficiently without interfering with each other.

# The Shell

A shell is a program that reads user commands and runs the appropriate programs in response. It’s often called a command interpreter.

When a user logs in, the system starts a login shell—a process that runs the shell program for that session.

Unlike some operating systems where the command interpreter is built into the kernel, on UNIX/Linux, the shell runs as a regular user-level process.

> The Bourne Again Shell (bash) is the GNU version of the original Bourne shell (sh). Written by Brian Fox and Chet Ramey, it adds interactive features from the C and Korn shells. On most Linux systems, sh is actually a symlink to bash, running in compatibility mode.

Shells aren’t just for typing commands interactively—they also execute shell scripts, which are text files containing commands. Shells support typical programming constructs like variables, loops, conditionals, I/O, and functions, making them powerful scripting tools.

# Users and Groups in Linux

## Users
- Username: Unique name used to log in to the system.
- User ID (UID): Numeric identifier for the user (used internally by the system).
- Group ID (GID): The user’s primary group—used for permission checks.
- Home Directory: The default working directory after login (e.g., `/home/rugved`).
- Login Shell: The program started after login (commonly `/bin/bash`).
- Password: Usually stored in a secure shadow file, not directly in `/etc/passwd`.

## Groups
- Purpose: Used to control access to files and system resources.
- Multiple Group Membership: Users can belong to more than one group, allowing flexible permission management.
- Defined In: `/etc/group`, with:
  - Group Name: Unique group identifier (e.g., developers)
  - Group ID (GID): Numeric ID of the group
  - User List: List of usernames who are members of the group

## Superuser (root)
- UID 0: The special user with unrestricted access to the entire system.
- Bypasses Permissions: Can read, write, and execute any file, and control any process.
- System Admin Role: Used for administrative tasks like installing software, managing users, and modifying system settings.

# File Organization in Linux

## Hierarchical Structure
- Linux uses a single unified directory tree starting from the root directory `/`.
- Unlike Windows, which uses separate directory trees for each disk (e.g., `C:\`, `D:\`), Linux mounts all storage under the same hierarchy.

## File Types
Every file has a type, such as:
- Regular file: Standard data files
- Directory: Contains a list of file names and links
- Symbolic link: Pointer to another file
- Device file: Interface to hardware
- Socket/Pipe: For interprocess communication

## Directories and Links
- A directory maps file names to file references (called links).
- A file can have multiple links, allowing it to appear in more than one directory.
- Each directory contains two special entries:
  - `.` \\(\rightarrow\\) refers to itself
  - `..` \\(\rightarrow\\) refers to its parent directory
- The root directory (`/`) is its own parent, so `/..` = `/`.

## Symbolic Links (Soft Links)

A symbolic link is a special file that points to another file by name (called its target). Unlike a hard link, which directly references file data, a symbolic link stores a path to another file.
- The kernel automatically follows symbolic links when resolving pathnames.
- Links can be nested (pointing to other symbolic links), but the kernel limits how many it will follow to avoid infinite loops.
- If the target file doesn’t exist, the symbolic link becomes a dangling link.
- “Hard link” = direct reference to file data. “Soft link” or symbolic link = pointer to a file name.

## File Names in Linux
- Most Linux file systems allow filenames up to 255 characters.
- Filenames can include any character except:
  - `/` (used as a directory separator)
  - `\0` (null character, reserved as a string terminator)
- Recommended Characters
  - Use only letters, digits, and these symbols: `.`, `_`, `-`
  - This is called the portable filename character set (defined by SUSv3).
  - It’s safer because these characters don’t require escaping in most contexts (e.g., shell, regex).
- Avoid:
  - Special characters (e.g., `*`, `&`, `?`) — they may be misinterpreted by the shell or scripts.
  - Filenames starting with `-` — they may be mistaken as command-line options.

## Pathnames in Linux

A pathname is a string that describes the location of a file or directory in the file system. It consists of:
- An optional starting slash `/` (indicates an absolute path)
- A sequence of filenames, separated by `/`

Components:
- All parts except the last must be directories (or symbolic links to directories).
- The final component can be any type of file.

Terminology:
- The portion before the last `/` is the directory part.
- The final filename is the base or file part.

Notes:
- Pathnames are read left to right, each level referring to a subdirectory of the one before.
- `..` refers to the parent directory at any point in the path.
- A pathname specifies the location of a file within the directory hierarchy and can be either absolute or relative:
  - Absolute pathname: Begins with a `/` and defines the file’s location starting from the root directory.
  - Relative pathname: Does not begin with a `/` and defines the file’s location relative to the current working directory of the process.

## Current Working Directory

Each process has a current working directory, which represents its current location in the directory hierarchy. When a process uses a relative pathname, it is interpreted based on this directory.
- A process inherits its working directory from its parent.
- A login shell starts in the user’s home directory, as defined in `/etc/passwd`.
- The current directory can be changed using the cd command.

## File Ownership and Permissions

Each file is associated with a user ID (owner) and a group ID. These determine who can access or modify the file.

Users are classified into three categories for permission purposes:
- Owner: the user who owns the file
- Group: users in the same group as the file
- Others: all remaining users

Each category has three permission types, resulting in nine permission bits:
- Read (`r`): view file contents or list directory contents
- Write (`w`): modify file contents or change directory entries (add/remove files)
- Execute (`x`): run the file (if executable) or access directory contents

Permissions on directories differ slightly:
- Read: list files in the directory
- Write: add, remove, or rename files in the directory
- Execute: access files within the directory (provided the files themselves permit it)

# File I/O Model

UNIX systems follow the principle of I/O universality, meaning the same system calls—such as `open()`, `read()`, `write()`, and `close()`—are used for all types of files, including regular files, devices, and pipes. The kernel handles translating these calls into the appropriate operations, allowing applications to work with any file type in a consistent way.

The kernel treats files as sequential streams of bytes. For random access (e.g., seeking to a specific location in a file), programs use the `lseek()` system call.

UNIX does not use a special end-of-file character. The end of a file is indicated when a `read()` call returns zero bytes. Newline characters (`\n`, ASCII 10) are commonly used by applications to separate lines in text files.

## File Descriptors

When a file is opened using `open()`, the kernel returns a file descriptor—a small, non-negative integer that uniquely identifies the open file within the process.

By default, every process starts with three file descriptors:
- 0: Standard Input (`stdin`)
- 1: Standard Output (`stdout`)
- 2: Standard Error (`stderr`)

These are typically connected to the terminal in an interactive shell or program.

## stdio Library

The stdio library in C provides higher-level I/O functions built on top of the system calls. Common functions include:
- `fopen()`, `fclose()` – for opening and closing files
- `scanf()`, `printf()` – for formatted input and output
- `fgets()`, `fputs()` – for line-based I/O

These functions use internal buffers and offer a more convenient interface for file I/O in C programs.

# References

1. Kerrisk, Michael. The Linux Programming Interface: A Linux and UNIX System Programming Handbook. United States, No Starch Press, 2010.
