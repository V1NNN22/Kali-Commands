
````markdown
# 🐧 Linux Commands Cheat Sheet
~
## Written By: VINOD N. RATHOD. 
~
A quick reference for common Linux commands with examples. Perfect for beginners or as a refresher.

---

##  Table of Contents
1. [Linux Folder Basics](#1-linux-folder-basics)
2. [Navigating the File System](#2-navigating-the-file-system)
3. [File and Folder Operations](#3-file-and-folder-operations)
4. [View and Edit Files](#4-view-and-edit-files)
   - [Editing Files](#editing-files)

````
---

## **1. Linux Folder Basics**

**/** : Root level folder (like C: drive in Windows) 

```bash
cd /
````

**/home** : User folder (all user data lives here)

```bash
cd /home/username
```

**/root** : Only the root (admin) user uses this folder

```bash
sudo cd /root
```

**/bin** : Holds basic tools you use every day (ls, cp, rm, etc.)

```bash
ls /bin
```

**/usr** : Software you install later goes here

```bash
ls /usr
```

**/var** : Holds logs, emails, web files, anything that changes often

```bash
ls /var/log
```

**/tmp** : Temporary files (deleted on restart)

```bash
cd /tmp
```

**/etc** : System settings for everything

```bash
ls /etc
```

---

## **2. Navigating the File System**

**pwd** : Show where you are (Print Working Directory)

```bash
pwd
```

**ls** : List contents of folder

```bash
ls /home
```

**clear** : Clears the terminal

```bash
clear
```

**tree** : Shows files & folders in tree structure

```bash
tree /var
```

**ls -l** : Long listing (sizes, dates, permissions)

```bash
ls -l /etc
```

**ls -a** : Show hidden files (starting with .)

```bash
ls -a
```

**cd \~** : Go to your home directory

```bash
cd ~
```

**cd -** : Go back to previous directory

```bash
cd -
```

---

## **3. File and Folder Operations**

**touch file.txt** : Create a new empty file

```bash
touch notes.txt
```

**mkdir dir/** : Create a new directory

```bash
mkdir projects
```

**cp file1 file2** : Copy a file

```bash
cp notes.txt backup.txt
```

**cp -r dir1 dir2** : Copy a folder and its contents recursively

```bash
cp -r projects projects_backup
```

**mv src dest** : Move or rename a file/folder

```bash
mv oldname.txt newname.txt
```

**rm file.txt** : Delete a file

```bash
rm old.txt
```

**rmdir folder/** : Delete an empty folder

```bash
rmdir tempfolder
```

**rm -r folder/** : Delete a folder and everything inside

```bash
rm -r old_project
```

---

## **4. View and Edit Files**

**cat file.txt** : Print entire file

```bash
cat notes.txt
```

**less file.txt** : View large files page-by-page

```bash
less bigfile.txt
```

**more file.txt** : Similar to less

```bash
more bigfile.txt
```

**head file.txt** : Show first 10 lines

```bash
head notes.txt
```

**tail file.txt** : Show last 10 lines

```bash
tail notes.txt
```

**tail -f /path/log.log** : Live follow a log file

```bash
tail -f /var/log/syslog
```

---

### **Editing Files**

**nano file** : Simple terminal editor (save `ctrl+o`, exit `ctrl+x`)

```bash
nano notes.txt
```

**vim file** : Advanced terminal editor (`Esc` → `:wq` to save & quit)

```bash
vim notes.txt
```

**i** : Insert mode (start editing in vim)

```bash
# Press 'i' in vim to start typing
```

**Esc** : Exit insert mode in vim

```bash
# Press Esc to stop editing
```

**:wq** : Save and quit in vim

```bash
:wq
```

**:q!** : Quit without saving in vim

```bash
:q!
```

---
# THANK YOU!
#  ~ **V1NNN22** ~
