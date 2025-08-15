
````markdown
#  Linux Text Processing & Search Tools Cheat Sheet

~
## Written By: VINOD N. RATHOD. 
~

Quick reference for searching, processing, and extracting text and files in Linux.

---

##  Table of Contents
1. [grep — Pattern Hunter](#tool-1-grep--pattern-hunter)  
2. [find — File Locator](#tool-2-find--file-locator)  
3. [locate — Fast File Finder](#tool-3-locate--fast-file-finder)  
4. [cut — Field Extractor](#tool-4-cut--field-extractor)  
5. [awk — Mini Script Power](#tool-5-awk--mini-script-power)  
6. [xargs — Mass Execution](#tool-6-xargs--mass-execution)  
7. [sort & uniq — Clean Duplicates](#tool-7-sort--uniq--clean-duplicates)  
8. [strings — Readable Text in Binaries](#tool-8-strings--readable-text-in-binaries)  
9. [head / tail — File Start & End](#tool-9-head--tail--file-start--end)  
10. [wc — Count Lines/Words](#tool-10-wc--count-lineswords)
````
---

## **Tool 1: grep — Pattern Hunter**

**grep -i 'pass' creds.txt** : Search case-insensitive for "pass"  
```bash
grep -i 'admin' users.txt
````

**grep -rn 'flag' ./** : Recursive search with line numbers

```bash
grep -rn 'error' ./logs
```

**grep -A2 'token' file.txt** : Show 2 lines after match

```bash
grep -A2 'username' config.txt
```

---

## **Tool 2: find — File Locator**

**find / -name "flag.txt" 2>/dev/null** : Find file anywhere

```bash
find / -name "notes.txt" 2>/dev/null
```

**find . -type f -perm 777** : Find files with 777 permissions

```bash
find . -type f -perm 777
```

**find . -size +10k** : Find files larger than 10KB

```bash
find . -size +1M
```

---

## **Tool 3: locate — Fast File Finder**

**locate id\_rsa** : Find file using index

```bash
locate passwords.txt
```

**locate -i 'flag'** : Case-insensitive search

```bash
locate -i 'config'
```

**sudo updatedb** : Build file index (if needed)

```bash
sudo updatedb
```

---

## **Tool 4: cut — Field Extractor**

**cut -d ':' -f1 users.txt** : Extract usernames before ":"

```bash
cut -d ':' -f1 /etc/passwd
```

**cut -d ',' -f2 passwords.csv** : Extract 2nd field from CSV

```bash
cut -d ',' -f3 data.csv
```

---

## **Tool 5: awk — Mini Script Power**

**awk '{print \$1}' logs.txt** : Print first column

```bash
awk '{print $1}' access.log
```

**awk -F ':' '{print \$2}' file.txt** : Use ":" delimiter, print 2nd field

```bash
awk -F ':' '{print $3}' /etc/passwd
```

**awk '/admin/ {print \$1}' logs.txt** : Filter lines containing "admin"

```bash
awk '/error/ {print $2}' error.log
```

---

## **Tool 6: xargs — Mass Execution**

**cat filelist.txt | xargs chmod 644** : Apply chmod to all files in list

```bash
cat files.txt | xargs rm
```

**find . -name "\*.sh" | xargs -n1 chmod +x** : Make all `.sh` files executable

```bash
find . -name "*.py" | xargs -n1 chmod 644
```

---

## **Tool 7: sort & uniq — Clean Duplicates**

**sort urls.txt | uniq** : Remove duplicates

```bash
sort names.txt | uniq
```

**sort -u urls.txt** : Sort & remove duplicates

```bash
sort -u emails.txt
```

**uniq -c sorted.txt** : Count duplicates (needs sorted input)

```bash
uniq -c sorted_names.txt
```

---

## **Tool 8: strings — Readable Text in Binaries**

**strings suspicious.bin | grep -i pass** : Search readable "pass" in binary

```bash
strings dump.img | grep -i password
```

**strings -n 8 dump.dat** : Only strings 8+ chars long

```bash
strings -n 5 malware.bin
```

---

## **Tool 9: head / tail — File Start & End**

**head -n 5 logfile.txt** : First 5 lines

```bash
head -n 3 config.txt
```

**tail -n 10 logfile.txt** : Last 10 lines

```bash
tail -n 15 output.log
```

**tail -f /var/log/auth.log** : Live follow system log

```bash
tail -f /var/log/syslog
```

---

## **Tool 10: wc — Count Lines/Words**

**wc -l creds.txt** : Count lines

```bash
wc -l report.txt
```

**wc -w creds.txt** : Count words

```bash
wc -w article.txt
```

**wc -c creds.txt** : Count bytes

```bash
wc -c data.bin
```

---
# THANK YOU!
#  ~ **V1NNN22** ~
