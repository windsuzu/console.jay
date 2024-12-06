---
draft: false
date: 2024-12-06 21:43
tags:
  - linux
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
