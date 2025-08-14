

````markdown
#  Linux Process & System Info Cheat Sheet

~
## Written By: VINOD N. RATHOD. 
~

Quick reference for managing processes, background jobs, and checking system information.

---

##  Table of Contents
A. [View Running Processes](#a-view-running-processes)  
B. [Kill / Manage Processes](#b-kill--manage-processes)  
C. [Background Jobs](#c-background-jobs)  
D. [System Info](#d-system-info)
````
---

## **A. View Running Processes**

**ps** : Show current user's processes  
```bash
ps
````

**ps aux** : Show all system processes

```bash
ps aux
```

**ps aux | grep name** : Search for a specific process

```bash
ps aux | grep firefox
```

**top** : Live view of processes, CPU, RAM

```bash
top
```

**htop** : Better live view (if installed)

```bash
htop
```

**Install htop:**

```bash
sudo apt update
sudo apt install htop
```

---

## **B. Kill / Manage Processes**

**kill PID** : Kill process by PID

```bash
kill 1234
```

**killall name** : Kill all processes with exact name

```bash
killall firefox
```

**pkill name** : Kill process by partial name match

```bash
pkill fire
```

---

## **C. Background Jobs**

**command &** : Run command in background

```bash
ping google.com &
```

**jobs** : List background jobs

```bash
jobs
```

**fg** : Bring job to foreground

```bash
fg
```

**bg** : Resume job in background

```bash
bg
```

---

## **D. System Info**

**uname -a** : OS and kernel info

```bash
uname -a
```

**uptime** : Show system running time

```bash
uptime
```

**df -h** : Disk usage (human-readable)

```bash
df -h
```

**free -m** : RAM usage (in MB)

```bash
free -m
```

**lscpu** : CPU details

```bash
lscpu
```

**lsblk** : List block devices and partitions

```bash
lsblk
```

---
# THANK YOU!
#  ~ **V1NNN22** ~
