# Nmap Basics 

# 1. Introduction to Enumeration

In cybersecurity:Knowledge is power


Before attacking a target, we must first gather information.

This process is called: Enumeration

# Why Enumeration Matters

Enumeration helps identify:

* Open ports
* Running services
* Operating systems
* Firewalls
* Vulnerabilities

Without enumeration, exploitation becomes very difficult.


# 2. What is Port Scanning?

When a service runs on a computer, it opens a: Port

Ports allow devices and services to communicate.

Port scanning helps identify:

* Open ports
* Closed ports
* Filtered ports


# Total Number of Ports

Every device has:

65535

Available ports.


# Well-Known Ports

Well-known ports range from: 0 - 1023


# 3. Common Ports

| Port | Service |
| ---- | ------- |
| 21   | FTP     |
| 22   | SSH     |
| 23   | Telnet  |
| 25   | SMTP    |
| 53   | DNS     |
| 80   | HTTP    |
| 110  | POP3    |
| 139  | NETBIOS |
| 443  | HTTPS   |
| 445  | SMB     |


# 4. Introduction to Nmap

Nmap stands for: Network Mapper

Nmap is the industry-standard tool for:

* Port scanning
* Service detection
* OS detection
* Vulnerability scanning
* Enumeration

# Basic Nmap Syntax

```bash id="zj52f2"
nmap <target>
```

Example:

```bash id="9xhz31"
nmap 192.168.1.10
```

# 5. Important Nmap Switches

| Switch     | Purpose                   |
| ---------- | ------------------------- |
| `-sS`      | SYN Scan                  |
| `-sT`      | TCP Connect Scan          |
| `-sU`      | UDP Scan                  |
| `-sN`      | NULL Scan                 |
| `-sF`      | FIN Scan                  |
| `-sX`      | Xmas Scan                 |
| `-O`       | OS Detection              |
| `-sV`      | Service Version Detection |
| `-v`       | Verbose                   |
| `-vv`      | More Verbose              |
| `-A`       | Aggressive Scan           |
| `-Pn`      | Skip Host Discovery       |
| `-sn`      | Ping Sweep                |
| `-p-`      | Scan All Ports            |
| `-oN`      | Normal Output             |
| `-oG`      | Grepable Output           |
| `-oA`      | Save All Formats          |
| `-T5`      | Fast Timing               |
| `--script` | Run NSE Script            |

---

# Examples

## Scan Port 80

```bash id="xj16xl"
nmap -p 80 192.168.1.10
```


## Scan Ports 1000-1500

```bash id="bxx9cl"
nmap -p 1000-1500 192.168.1.10
```

## Scan All Ports

```bash id="f6e14p"
nmap -p- 192.168.1.10
```


## Service Version Detection

```bash id="s3uvq1"
nmap -sV 192.168.1.10
```


## OS Detection

```bash id="jqgspv"
nmap -O 192.168.1.10
```

# 6. TCP Three-Way Handshake

TCP communication works using:

1. SYN
2. SYN/ACK
3. ACK

This is called:

```text id="7vr3jc"
TCP Three-Way Handshake
```


# 7. TCP Connect Scan (`-sT`)

TCP Connect Scan performs the complete handshake.

### Open Port Response

Server replies with:

```text id="vgh4ns"
SYN/ACK
```


### Closed Port Response

Server replies with:

```text id="0q8z8x"
RST
```

RST means:

```text id="m79x9w"
Reset
```


# RFC Used

TCP behavior is defined in:

* RFC 9293


# TCP Connect Scan Command

```bash id="g8o5hn"
nmap -sT 192.168.1.10
```


# 8. SYN Scan (`-sS`)

Also called:

* Half-Open Scan
* Stealth Scan

# How SYN Scan Works

1. Send SYN
2. Receive SYN/ACK
3. Send RST instead of ACK

This avoids completing the connection.


# Advantages

* Faster
* Stealthier
* Less logging
* Can bypass older IDS systems


# Disadvantages

* Requires sudo/root
* May crash unstable services

# SYN Scan Command

```bash id="7krm7g"
sudo nmap -sS 192.168.1.10
```


# 9. UDP Scan (`-sU`)

UDP is: Connectionless


No handshake exists in UDP.


# UDP Scan Command

```bash id="v9d1h7"
nmap -sU 192.168.1.10
```

# UDP Scan Results

| Response              | Meaning       |
| --------------------- | ------------- |
| No Response           | open|filtered |
| ICMP Port Unreachable | Closed        |


# Faster UDP Scan

```bash id="w3twit"
nmap -sU --top-ports 20 192.168.1.10
```

---

# 10. NULL, FIN & Xmas Scans

These scans are mainly used for: Firewall Evasion


# NULL Scan (`-sN`)

Sends packets with: No flags


# FIN Scan (`-sF`)

Uses: FIN flag

# Xmas Scan (`-sX`)

Uses flags:

* PSH
* URG
* FIN

# Important Note

Microsoft Windows often responds with: RST for every port

Making these scans unreliable against Windows systems.



# Xmas Scan Command

```bash id="v5ax5v"
nmap -sX 192.168.1.10
```

# 11. Ping Sweeps

Ping sweeps identify live hosts on a network.

---

# Ping Sweep Command

```bash id="5p7p0h"
nmap -sn 192.168.1.0/24
```

---

# CIDR Example

For network:

```text id="zjlwm6"
172.16.x.x
```

Command:

```bash id="nmb5vq"
nmap -sn 172.16.0.0/16
```

---

# 12. NSE (Nmap Scripting Engine)

NSE allows Nmap to run scripts for:

* Enumeration
* Vulnerability scanning
* Exploitation

---

# NSE Language

NSE scripts are written in:

```text id="8rfx4j"
Lua
```

---

# NSE Categories

| Category  | Purpose                 |
| --------- | ----------------------- |
| safe      | Safe scans              |
| vuln      | Vulnerability scanning  |
| exploit   | Exploit vulnerabilities |
| brute     | Brute force attacks     |
| auth      | Authentication testing  |
| discovery | Service discovery       |
| intrusive | Aggressive scripts      |

# Run Vulnerability Scripts

```bash id="r7r8dx"
nmap --script=vuln 192.168.1.10
```


# Run Specific Script

```bash id="vgcmrm"
nmap --script=http-enum 192.168.1.10
```


# Multiple Scripts

```bash id="xvmb8r"
nmap --script=smb-enum-users,smb-enum-shares 192.168.1.10
```


# Script Arguments

```bash id="ew3w7f"
nmap --script http-put --script-args http-put.url='/dav/shell.php'
```

# NSE Help

```bash id="c6g6gz"
nmap --script-help ftp-anon
```


# 13. Searching NSE Scripts

NSE scripts location:

```bash id="0x8m0r"
/usr/share/nmap/scripts
```


# Search for FTP Scripts

```bash id="xjlwm0"
ls -l /usr/share/nmap/scripts/*ftp*
```


# Search Using Grep

```bash id="3skujl"
grep "ftp" /usr/share/nmap/scripts/script.db
```

# SMB OS Discovery Script

```text id="vw4hcx"
smb-os-discovery.nse
```

# Update Nmap Script Database

```bash id="c6xq4z"
nmap --script-updatedb
```

# 14. Firewall Evasion

Many firewalls block:

```text id="j2i1xa"
ICMP
```

# Skip Ping Detection

```bash id="ocpyd2"
nmap -Pn 192.168.1.10
```


# Fragment Packets

```bash id="w0k09h"
nmap -f 192.168.1.10
```


# Add Scan Delay

```bash id="uzndg2"
nmap --scan-delay 5ms 192.168.1.10
```


# Random Packet Data

```bash id="p7kwhx"
nmap --data-length 50 192.168.1.10
```


# Generate Invalid Checksums

```bash id="0b0qta"
nmap --badsum 192.168.1.10
```

---

