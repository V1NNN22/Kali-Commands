# 🐧 Linux Essentials — Cheat Sheet

~
## Written By: VINOD N. RATHOD. 
~

---

## 📚 Table of Contents
- [📁 Linux File System Basics](#-linux-file-system-basics)
- [🛡️ Permissions & Users](#️-permissions--users)
- [⚙️ Processes & System Info](#️-processes--system-info)
- [🌐 Networking Basics in Linux](#-networking-basics-in-linux)
- [🚀 Power Tools (Search, Automation, Transfers, Security)](#-power-tools-search-automation-transfers-security)
- [🧩 Handy Snippets](#-handy-snippets)
- [✅ Practice Checklist](#-practice-checklist)

---

## 📁 Linux File System Basics

### 🗂️ The Directory Map (know these)
- `/` root of everything  
- `/home/USER` your files  
- `/etc` configs, `/var` variable data/logs, `/tmp` temporary  
- `/bin` & `/usr/bin` user commands, `/sbin` system commands  
- `/dev` devices, `/proc` running-kernel info (virtual), `/opt` optional apps

### 🧭 Navigate & List
```bash
pwd                          # where am I?
ls                           # list names
ls -la                       # long + hidden
ls -lh                       # human sizes
tree DIR                     # show folders as a tree (install: sudo apt/yum install tree)
cd DIR                       # go into DIR
cd ..                        # up one level
cd ~                         # home
```

### 📝 Create, Copy, Move, Delete
```bash
mkdir DIR                    # make folder
mkdir -p PATH/TO/DIR         # make nested folders
touch FILE                   # new empty file / update timestamp
cp FILE DEST                 # copy file
cp -r DIR DEST               # copy folder (recursive)
cp -a SRC DEST               # archive mode: keep perms/times/links
mv SRC DEST                  # move/rename
rm FILE                      # remove file
rm -i FILE                   # ask before delete
rm -r DIR                    # remove folder recursively
rm -rf DIR                   # ⚠️ force recursive delete (danger!)
rmdir EMPTYDIR               # remove empty folder
```

### 🔎 Inspect & Measure
```bash
file FILE                    # detect file type
stat FILE                    # full metadata (size, perms, times)
wc -l FILE                   # line count
du -sh *                     # sizes of items (disk usage, human)
df -h                        # free space by filesystem
```

### 🔗 Links (Shortcuts)
```bash
ln SRC HARDLINK              # hard link (same inode)
ln -s TARGET LINKNAME        # symbolic link (pointer)
```

### 🔍 Find Files Fast
```bash
find PATH -name "*.log"                  # by name (glob)
find PATH -type f -size +100M            # large files
find PATH -type f -mtime -1              # modified < 1 day
find PATH -type d -name ".git" -prune    # skip matches
find PATH -type f -name "*.tmp" -delete  # delete matches (careful)
find PATH -type f -exec grep -nH "text" {} \;  # search inside
```
> Tip: `locate NAME` is faster (uses a database). Update DB with `sudo updatedb` first on some distros.

### 📖 View File Contents
```bash
cat FILE                      # print all
nl FILE                       # print with line numbers
less FILE                     # pager (q to quit, /search, n next)
head -n 20 FILE               # first 20 lines
tail -n 50 FILE               # last 50 lines
tail -f LOGFILE               # follow live updates
```

---

## 🛡️ Permissions & Users

### 🔤 Read the `ls -l` Output
Example: `-rw-r--r-- 1 USER GROUP 12K Jan 1 12:00 notes.txt`  
- Positions: `d`=directory, `-`=file, `l`=symlink  
- Then `rwx` for **owner**, **group**, **others**.

### #️⃣ Octal Cheatsheet
- `r=4`, `w=2`, `x=1` → add them:
  - `7` = `rwx`, `6` = `rw-`, `5` = `r-x`, `4` = `r--`, `0` = `---`
- Common: `644` (files), `755` (dirs/executables)

### 🛠️ Change Permissions & Ownership
```bash
chmod 644 FILE                # octal
chmod u+x SCRIPT.sh           # symbolic (add exec to owner)
chmod -R 755 DIR              # recursive

chown USER FILE               # change owner
chown USER:GROUP FILE         # change owner & group
chgrp GROUP FILE              # change group
```

### 👥 Users & Groups
```bash
whoami                        # current user
id                            # uid/gid and groups
groups USER                   # groups for user

# Manage (needs sudo)
sudo useradd -m -s /bin/bash USER           # add user with home
sudo passwd USER                             # set password
sudo usermod -aG GROUP USER                  # add to group
sudo userdel -r USER                         # delete user & home
sudo groupadd GROUP                          # create group

# Privilege elevation
sudo -v                        # refresh sudo timestamp
sudo -l                        # what can I run?
su - USER                      # switch user (login shell)
```

### 🧷 Special Bits (Just Know)
- **Sticky** (`+t`) on shared dirs (e.g., `/tmp`): only owner can delete their files.  
  `sudo chmod +t /shared`
- **setuid/setgid**: run with owner/group privileges (advanced, use carefully).

### 🎯 Default Mask
```bash
umask           # show default (e.g., 0022)
umask 0022      # set: new files get (666-022)=644, dirs (777-022)=755
```

---

## ⚙️ Processes & System Info

### 🔭 See What’s Running
```bash
ps aux | less                     # all processes
pgrep -fl NAME                    # find PIDs by name
top                               # live view (q to quit)
htop                              # nicer top (install first)
watch -n1 'free -h'               # rerun every second
```

### 🧹 Control Processes
```bash
kill PID                          # polite stop (SIGTERM)
kill -9 PID                       # force kill (SIGKILL)
pkill NAME                        # kill by name
killall NAME                      # kill all named

nice -n 10 CMD                    # start with lower priority
renice 5 -p PID                   # change priority of running process
```

### 📊 Resource & Hardware
```bash
free -h                           # memory
df -h                             # disk space
du -sh DIR                        # folder size
uptime                            # load averages
uname -a                          # kernel & arch
cat /etc/os-release               # distro info
lscpu                             # CPU details
lsblk -f                          # disks/partitions
```

### 🧩 Services & Logs (systemd)
```bash
systemctl status SERVICE          # service status
sudo systemctl start|stop SERVICE # control
systemctl list-units --type=service --state=running  # running services

journalctl -u SERVICE --since "1 hour ago"  # recent logs
journalctl -xe                     # last errors with context
dmesg -T                           # kernel messages (with time)
```

### 🔓 Open Files & Ports
```bash
lsof -p PID                       # files opened by a process
sudo lsof -i -P -n                # all network sockets
ss -tulpen                        # listening ports & owners
```

---

## 🌐 Networking Basics in Linux

### 🛣️ Interfaces & Routes
```bash
ip a                              # addresses
ip r                              # routes
ip link set IFACE up|down         # bring interface up/down
sudo ip addr add 192.168.1.50/24 dev IFACE   # add IP
```

### 🧪 Connectivity Tests
```bash
ping -c 4 HOST                    # reachability + latency
traceroute HOST                   # path (install may be required)
mtr HOST                          # live trace (install may be required)
dig A example.com                 # DNS lookup (install: dnsutils/bind-utils)
nslookup example.com              # DNS (legacy/alt)
curl -I https://example.com       # HTTP headers (quick check)
wget URL                          # download file
```

### 🔭 Ports & Services
```bash
ss -tulpn                         # show listening ports
nc -vz HOST PORT                  # test TCP connect
nc -lvp 9000                      # simple listener on 9000
# send a file to listener:
nc HOST 9000 < FILE
```

> If using Wi-Fi NetworkManager:  
> `nmcli dev wifi list` → scan, `nmcli con up "SSID"` → connect (may need credentials).

---

## 🚀 Power Tools (Search, Automation, Transfers, Security)

### 🔍 Text Search & Filters
```bash
grep -RIn --color "PATTERN" PATH        # recursive, line numbers
grep -E "regex1|regex2" FILE            # extended regex

# Sed: find/replace (in-place with backup)
sed -i.bak 's/OLD/NEW/g' FILE

# Awk: pick columns / simple reports
awk -F: '{print $1, $3}' /etc/passwd     # user and uid
awk '{sum+=$1} END {print sum}' numbers.txt

# Quick cutters & sorters
cut -d, -f1-3 FILE                       # first 3 CSV fields
tr -d '\r' < FILE > CLEAN                # remove CR
sort FILE | uniq -c | sort -nr           # frequency count
```

### 🔗 Pipelines & `xargs`
```bash
# Send output into multiple places
somecmd | tee out.log

# Null-safe find → xargs
find PATH -type f -print0 | xargs -0 grep -n "TEXT"
```

### 📦 Archives & Compression
```bash
# tarball create/extract
tar -czvf archive.tgz DIR               # create (.tgz)
tar -xzvf archive.tgz                   # extract

zip -r archive.zip DIR                  # zip dir
unzip archive.zip                       # unzip
```

### 🔐 SSH & File Transfer
```bash
ssh USER@HOST                           # remote shell
scp FILE USER@HOST:/PATH/               # copy to remote
scp -r DIR USER@HOST:/PATH/             # copy folder
rsync -avh --progress SRC/ DEST/        # local sync
rsync -avh --progress SRC/ USER@HOST:/DEST/   # to remote
rsync -avh --delete SRC/ DEST/          # mirror (⚠️ deletes extras)
```

### ⏰ Schedule Jobs
```bash
crontab -e                               # edit user cron
# ┌ min (0-59)
# │ ┌ hour (0-23)
# │ │ ┌ day of month (1-31)
# │ │ │ ┌ month (1-12)
# │ │ │ │ ┌ day of week (0-7, Sun=0/7)
# * * * * *  CMD

# Example: run backup at 2:30 AM daily
30 2 * * * /home/USER/bin/backup.sh >> /var/log/backup.log 2>&1
```

### 🛰️ Security / Diagnostics (Ethical Use Only)
```bash
nmap -sV -Pn TARGET                    # discover services & versions
sudo tcpdump -i IFACE 'port 80' -c 50  # capture a few packets (Ctrl+C to stop)
```
> Use only on systems you own or are authorized to test. ✅

---

## 🧩 Handy Snippets

```bash
# 1) Find biggest things in current folder (top 20)
du -sh * | sort -hr | head -n 20

# 2) Which process is using PORT?
sudo lsof -iTCP:PORT -sTCP:LISTEN -n -P

# 3) Last 100 lines of a log with live follow
tail -n 100 -f /var/log/syslog

# 4) Safely replace a string across many files (with backups)
grep -RIl "OLD" . | xargs -I{} sed -i.bak 's/OLD/NEW/g' "{}"

# 5) List services that failed
systemctl --failed

# 6) Quickly serve current directory over HTTP (Python 3)
python3 -m http.server 8000
```

---

## ✅ Practice Checklist

- [ ] Navigate to your home and list all files (including hidden)  
  `cd ~ && ls -la`  
- [ ] Create `playground/notes`, make a file, and symlink it to `note`  
  ```bash
  mkdir -p playground/notes
  echo "hello" > playground/notes/one.txt
  ln -s playground/notes/one.txt note
  ```
- [ ] Set permissions: folder `755`, file `644`  
  `chmod 755 playground/notes && chmod 644 playground/notes/one.txt`  
- [ ] Find files modified today under `playground`  
  `find playground -type f -mtime -1 -print`  
- [ ] Watch memory usage live for 5 seconds  
  `watch -n1 -d 'free -h'` (press `Ctrl+C` when done)  
- [ ] Check listening ports  
  `ss -tulpen`  
- [ ] Compress `playground` into `playground.tgz` and extract it  
  `tar -czvf playground.tgz playground && tar -xzvf playground.tgz`  
- [ ] Copy a file to a remote host (replace placeholders)  
  `scp FILE USER@HOST:/PATH/`  
- [ ] Add a cron job to echo time every minute (then remove it)  
  `crontab -e` → `* * * * * date >> ~/minute.log`  

---
# THANK YOU!
#  ~ **V1NNN22** ~


