---
draft: false
date: 2024-12-07 14:21
tags:
  - linux
---

### **View User Information**

|Command|Description|
|---|---|
|`whoami`|displays the current logged-in user|
|`id`|shows user ID (UID), group ID (GID), and group memberships|
|`who`|lists all users currently logged into the system|
|`users`|lists logged-in users in a single line|

---

### **Create New Users and Understand Primary Groups**

|Command|Description|
|---|---|
|`sudo adduser username`|creates a new user with a home directory and default settings|
|`sudo useradd username`|creates a new user (minimal configuration)|
|`id username`|displays the UID, GID, and groups of a specific user|

> **Note:** A user's primary group is automatically created with the same name as the user by default.

---

### **Explore and Modify User Groups**

|Command|Description|
|---|---|
|`groups username`|lists all groups a user belongs to|
|`sudo usermod -aG groupname username`|adds a user to an additional group without removing existing groups|
|`sudo deluser username groupname`|removes a user from a specific group|

---

### **Create New Groups and Add Users to Them**

|Command|Description|
|---|---|
|`sudo groupadd groupname`|creates a new group|
|`sudo usermod -G groupname username`|assigns a user to a group, replacing all existing group memberships|
|`sudo gpasswd -a username groupname`|adds a user to a group using group administrator tools|

---

### **Grant Sudo Privileges to Users**

|Command|Description|
|---|---|
|`sudo usermod -aG sudo username`|adds a user to the `sudo` group (Debian/Ubuntu systems)|
|`sudo visudo`|opens the sudoers file for editing|
|`%groupname ALL=(ALL:ALL) ALL`|grants sudo privileges to all users in a group|

---

### **View and Understand File Permissions**

|Command|Description|
|---|---|
|`ls -l`|displays detailed file information, including permissions|
|`ls -ld directory/`|shows permissions for a directory|

> File permission format: `-rw-r--r--`

- **First character**: Type (`-` for file, `d` for directory)
- **Next three characters**: Owner permissions (read, write, execute)
- **Middle three characters**: Group permissions
- **Last three characters**: Other users' permissions

---

### **Change File Ownership**

`chown`: Changes the ownership of files or directories.

|Command|Description|
|---|---|
|`sudo chown user file.txt`|changes the owner of `file.txt` to `user`|
|`sudo chown user:group file.txt`|changes both the owner and group of `file.txt`|
|`sudo chown -R user directory/`|recursively changes ownership for a directory|

---

### **Modify File Permissions**

`chmod`: Changes file permissions.

|Command|Description|
|---|---|
|`chmod 644 file.txt`|sets permissions to read/write for owner, read-only for group and others|
|`chmod u+x file.sh`|adds execute permission for the owner|
|`chmod -R 755 folder/`|recursively sets permissions for a directory|

**Common Numeric Permissions:**

- `777`: Full permissions for everyone
- `755`: Full permissions for owner, read/execute for group and others
- `644`: Read/write for owner, read-only for group and others