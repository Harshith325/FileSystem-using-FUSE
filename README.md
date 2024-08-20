
# Filesystem Using FUSE

## Overview

This project involves creating a custom file system using FUSE (Filesystem in Userspace), designed to support essential file operations and directory management within a tree-structured hierarchy. The project aims to provide a solid foundation for understanding file system design and implementation, with potential applications in various domains such as security, embedded systems, and collaborative environments.

## Problem Statement

The objective is to design and implement a simple file system that supports the following functionalities:
- File creation, reading, writing, and deletion
- Tree-structured directory management
- Efficient handling of file attributes and operations


## Tools/APIs Used

The following tools and APIs are utilized in this project:

1. **Standard C Library**  
   - `#include<stdio.h>`, `#include<errno.h>`, `#include<stdlib.h>`, `#include<string.h>`, `#include<unistd.h>`, `#include<time.h>`, `#include<stddef.h>`, `#include<assert.h>`
   - Provides general-purpose functions for programming in C.

2. **File Control**  
   - `#include<fcntl.h>`
   - Header file for performing file control operations.

3. **FUSE Library**  
   - `#include<fuse.h>`
   - Offers functions like `getattr` and `readdir` for creating a FUSE-based file system.

4. **POSIX API**  
   - `#include<unistd.h>`
   - Header file for POSIX (Portable Operating System Interface) API functions.

5. **Macros**  
   - `#define block_size 1024`
   - Defines a macro for the block size.

6. **Structures**  
   - `struct Superblock`, `struct Inode`, `struct Node`
   - Data structures representing the superblock, inode, and node within the filesystem.

7. **fuse_main Function**  
   - Acts as the entry point for the FUSE-based file system, initializing the superblock, creating the root node, and launching the FUSE file system.

## Installation and Setup

To set up the file system, follow these steps:

1. **Compilation:**
   ```bash
   cc -g -Wall -O2 -o fileSys fileStruct.c `pkg-config fuse --cflags --libs`
   ```
   - `-Wall`: Enables all compiler warnings.
   - `pkg-config`: Locates the necessary compiler and linker flags for the FUSE library.

2. **Create a Mount Point:**
   ```bash
   mkdir ~/mount_point
   ```

3. **Mount the Filesystem:**
   ```bash
   ./fileSys -f ~/mount_point
   ```

4. **Unmount the Filesystem:**
   ```bash
   sudo umount -f ~/mount_point
   ```

## Filesystem Functions

The following functions are implemented to manage the filesystem:

- **getattr:**  
  Access file or directory attributes.  
  Example: `ls -l /path/to/mounted/directory/file`

- **readdir:**  
  List directory contents.  
  Example: `ls /path/to/mounted/directory`

- **read:**  
  Read the contents of a file.  
  Example: `cat /path/to/mounted/directory/file`

- **mkdir:**  
  Create a new directory.  
  Example: `mkdir /path/to/mounted/directory/new_directory`

- **mknod:**  
  Create a new file (not implemented to demonstrate a difference).  
  Example: `touch new_file`

- **write:**  
  Write content to a file.  
  Example: `echo "content" > /path/to/mounted/directory/file`

