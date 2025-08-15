

````markdown
#  Linux Networking Commands Cheat Sheet

~
## Written By: VINOD N. RATHOD. 
~

Quick reference for viewing network info, testing connectivity, tracing routes, and performing DNS lookups.

---

##  Table of Contents
A. [View IP Address & Interfaces](#a-view-ip-address--interfaces)  
B. [Test Connectivity](#b-test-connectivity)  
C. [Trace Network Path](#c-trace-network-path)  
D. [View Open Ports / Connections](#d-view-open-ports--connections)  
E. [DNS Lookup](#e-dns-lookup)  
F. [Web Requests from Terminal](#f-web-requests-from-terminal)
````
---

## **A. View IP Address & Interfaces**

**ip a** : Show IPs and all network interfaces  
```bash
ip a
````

*(If `ip` is not available)*

```bash
ifconfig
```

---

## **B. Test Connectivity**

**ping google.com** : Send packets to test if a host is reachable

```bash
ping google.com
```

*(Press `Ctrl + C` to stop)*

---

## **C. Trace Network Path**

**traceroute google.com** : Show hops to reach a domain

```bash
traceroute google.com
```

**Install traceroute if missing:**

```bash
sudo apt install traceroute
```

---

## **D. View Open Ports / Connections**

**netstat -tuln** : List listening TCP/UDP ports (older systems)

```bash
netstat -tuln
```

**ss -tuln** : Preferred for newer systems (same info as netstat)

```bash
ss -tuln
```

**Flags used in both:**

* `-t` : TCP
* `-u` : UDP
* `-l` : Listening only
* `-n` : Show IPs instead of domain names

---

## **E. DNS Lookup**

**dig google.com** : Show DNS resolution info *(needs dnsutils)*

```bash
dig google.com
```

**nslookup google.com** : Alternative DNS lookup

```bash
nslookup google.com
```

**Install dig if missing:**

```bash
sudo apt install dnsutils
```

---

## **F. Web Requests from Terminal**

**curl [http://example.com](http://example.com)** : Fetch web content (headers + body)

```bash
curl http://example.com
```

**wget [http://example.com](http://example.com)** : Download file or page

```bash
wget http://example.com
```

---
# THANK YOU!
#  ~ **V1NNN22** ~