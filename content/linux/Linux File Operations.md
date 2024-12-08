---
draft: false
date: 2024-12-08 23:28
tags:
  - linux
---

### **Creating Files and Directories**

| Command                   | Description                                     |
| ------------------------- | ----------------------------------------------- |
| `touch file.txt`          | Creates an empty file named `file.txt`.         |
| `mkdir new_directory`     | Creates a new directory named `new_directory`.  |
| `echo "text" > file.txt`  | Creates a file with the specified text content. |
| `echo "text" >> file.txt` | Appends the specified text to an existing file. |

---

### **Viewing and Editing Files**

|Command|Description|
|---|---|
|`cat file.txt`|Displays the entire content of a file.|
|`head file.txt`|Displays the first 10 lines of a file.|
|`head -n 5 file.txt`|Displays the first 5 lines of a file.|
|`tail file.txt`|Displays the last 10 lines of a file.|
|`nano file.txt`|Opens `file.txt` in the nano text editor.|

---
### **File Search Techniques**

| Command                        | Description                                                       |
| ------------------------------ | ----------------------------------------------------------------- |
| `find /path -name filename`    | Searches for a file with the specified name under the given path. |
| `find . -type d`               | Searches for all directories in the current path.                 |
| `find . -type f -name "*.txt"` | Finds all `.txt` files in the current directory.                  |
| `which command`                | Locates the executable path of a command.                         |

---

### **Deleting Files**

`rm`: Deletes files or directories.

|Command|Description|
|---|---|
|`rm file.txt`|deletes a file named `file.txt`|
|`rm -i file.txt`|prompts before deleting the file|
|`rm -r folder`|deletes a folder and its contents|
|`rm -rf folder`|forcibly deletes a folder and its contents without confirmation|

> **Caution:** Use the `-f` (force) option carefully, as it bypasses confirmation.

---

### **Copying Files**

`cp`: Copies files or directories.

|Command|Description|
|---|---|
|`cp file.txt backup.txt`|copies `file.txt` to `backup.txt`|
|`cp -r folder1 folder2`|recursively copies `folder1` and its contents to `folder2`|
|`cp -i file.txt backup.txt`|prompts before overwriting `backup.txt`|

---

### **Moving Files**

`mv`: Moves or renames files and directories.

|Command|Description|
|---|---|
|`mv file.txt folder/`|moves `file.txt` to the `folder`|
|`mv oldname.txt newname.txt`|renames `oldname.txt` to `newname.txt`|
|`mv -i file.txt folder/`|prompts before overwriting a file in the destination|
