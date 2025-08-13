
````markdown
# 🐧 Linux Permissions & User Management Cheat Sheet

## Written By: VINOD N. RATHOD. 

A quick reference for viewing and managing file permissions, ownership, and users in Linux.

---

##  Table of Contents
1. [View File Permissions](#1-view-file-permissions)
2. [Change Permissions – chmod](#2-change-permissions--chmod)
3. [Change Ownership – chown, chgrp](#3-change-ownership--chown-chgrp)
4. [View Ownership & IDs](#4-view-ownership--ids)
5. [Switch Users – su, sudo, whoami, id](#5-switch-users--su-sudo-whoami-id)
````
---

## **1: View File Permissions**

**ls -l** : Show permissions, owner, group, size  
```bash
ls -l /etc/passwd
````

---

## **2: Change Permissions – chmod**

**chmod 777 file** : Everyone can read, write, execute

```bash
chmod 777 script.sh
```

**chmod 700 file** : Only owner has full access

```bash
chmod 700 secret.txt
```

**chmod 755 file** : Owner full, others read + execute

```bash
chmod 755 myprogram
```

---

## **3: Change Ownership – chown, chgrp**

**sudo chown user file** : Change file owner

```bash
sudo chown alice report.txt
```

**sudo chown user\:group file** : Change owner & group

```bash
sudo chown alice:staff report.txt
```

**sudo chgrp group file** : Change group only

```bash
sudo chgrp staff report.txt
```

---

## **4: View Ownership & IDs**

**ls -l** : View owner and group

```bash
ls -l project.txt
```

**stat file** : Show full file metadata

```bash
stat project.txt
```

---

## **5: Switch Users – su, sudo, whoami, id**

**whoami** : Show current user

```bash
whoami
```

**id** : Show UID, GID, and group info

```bash
id
```

**su user** : Switch to another user

```bash
su bob
```

**sudo command** : Run command as root

```bash
sudo apt update
```

**sudo su** : Switch to root shell

```bash
sudo su
```

**exit** : Exit current shell

```bash
exit
```
---
# THANK YOU!
#  ~ **V1NNN22** ~

