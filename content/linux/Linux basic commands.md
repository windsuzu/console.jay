---
draft: false
date: 2024-12-06 21:22
tags:
  - linux
---

## Navigation

`cd` (Change Directory): Navigate through the file system.

| Command        | Description                       |
| -------------- | --------------------------------- |
| `cd Documents` | moves to the Documents folder     |
| `cd ..`        | goes up one directory level       |
| `cd ~`         | goes to the home directory        |
| `cd -`         | returns to the previous directory |
`pwd` (Print Working Directory): Displays the current directory path.

|Command|Description|
|---|---|
|`pwd`|prints the full path of your location|

`ls` (List Files): Displays files and directories.

|Command|Description|
|---|---|
|`ls`|lists files and directories in the current directory|
|`ls -l`|detailed listing with permissions, size, etc.|
|`ls -a`|includes hidden files in the listing|
|`ls -lh`|detailed listing with human-readable sizes|

---
## **File and Directory Creation**

`touch`: Creates empty files.

|Command|Description|
|---|---|
|`touch file.txt`|creates an empty file named `file.txt`|

`mkdir` (Make Directory): Creates new directories.

|Command|Description|
|---|---|
|`mkdir myfolder`|creates a folder named `myfolder`|
|`mkdir -p folder/subfolder`|creates nested directories in one step|

---

## **Wildcards for Multiple Files**

Wildcards simplify operations on multiple files.

|Wildcard|Example|Description|
|---|---|---|
|`*`|`ls *.txt`|matches all files ending in `.txt`|
|`?`|`ls file?.txt`|matches files like `file1.txt`|

---

## **Basic File Operations**

`cp` (Copy): Copies files or directories.

|Command|Description|
|---|---|
|`cp file.txt backup.txt`|copies `file.txt` to `backup.txt`|
|`cp -r folder1 folder2`|copies the folder and its contents|

`mv` (Move/Rename): Moves or renames files.

|Command|Description|
|---|---|
|`mv oldname.txt newname.txt`|renames `oldname.txt` to `newname.txt`|
|`mv file.txt /path/to/folder/`|moves the file to another location|

`rm` (Remove): Deletes files or directories.

|Command|Description|
|---|---|
|`rm file.txt`|deletes the file|
|`rm -r folder`|deletes the folder and its contents|

---

## **Helpful Shortcuts**

|Shortcut|Description|
|---|---|
|`Ctrl + L`|clears the terminal screen|
|`Ctrl + C`|stops the current command|
|`Ctrl + R`|searches command history interactively|
|`!!`|repeats the last command|
|`!<cmd>`|runs the most recent command starting with `<cmd>`|
