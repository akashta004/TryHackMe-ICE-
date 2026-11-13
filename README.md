# 🧊 TryHackMe — Ice

![TryHackMe](https://img.shields.io/badge/TryHackMe-212C42?style=for-the-badge&logo=tryhackme&logoColor=red)
![Windows](https://img.shields.io/badge/Target-Windows-0078D6?style=for-the-badge&logo=windows&logoColor=white)
![Difficulty](https://img.shields.io/badge/Difficulty-Medium-orange?style=for-the-badge)

> Write-up for the [Ice](https://tryhackme.com/room/ice) room on TryHackMe — a Windows machine focused on service enumeration and exploitation.

---

## 📌 Table of Contents
- [Room Info](#-room-info)
- [Objectives](#-objectives)
- [Tools Used](#-tools-used)
- [Walkthrough](#-walkthrough)
  - [1. Reconnaissance](#1-reconnaissance)
  - [2. Enumeration](#2-enumeration)
  - [3. Exploitation](#3-exploitation)
  - [4. Privilege Escalation](#4-privilege-escalation)
  - [5. Flags](#5-flags)
- [Key Learnings](#-key-learnings)
- [Disclaimer](#-disclaimer)
- [Author](#-author)

---

## 📖 Room Info

| | |
|---|---|
| **Room name** | Ice |
| **Platform** | TryHackMe |
| **Target OS** | Windows |
| **Attacker machine** | Kali Linux |
| **Status** | ✅ Completed |

---

## 🎯 Objectives

- Enumerate services running on a Windows target
- Identify and exploit a vulnerable service
- Escalate privileges to gain full system access
- Capture the user and root (system) flags

---

## 🧰 Tools Used

| Category | Tools |
|----------|-------|
| Scanning | Nmap |
| Enumeration | smbclient, enum4linux, CrackMapExec |
| Exploitation | Metasploit |
| Privilege Escalation | winPEAS |

---

## 🔍 Walkthrough

### 1. Reconnaissance

Initial port scan of the target:

```bash
nmap -sV -sC -p- -oN nmap-initial.txt <target-ip>
```

**Findings:**
- *(List open ports and services here, e.g. 135, 139, 445, 8000)*

![Nmap Scan](screenshots/01-nmap.png)

---

### 2. Enumeration

*(Describe the service you dug into — SMB shares, a web service on a custom port, etc.)*

```bash
smbclient -L //<target-ip>/ -N
```

**Findings:**
- *(What you discovered — e.g. accessible share, interesting file, service version)*

![Enumeration](screenshots/02-enum.png)

---

### 3. Exploitation

*(Name the vulnerability/service you exploited and why it's vulnerable.)*

```bash
msfconsole -q
use exploit/<path/to/module>
set RHOSTS <target-ip>
set LHOST <your-ip>
run
```

**Result:**
- *(Shell obtained, user context, etc.)*

![Exploitation](screenshots/03-exploit.png)

---

### 4. Privilege Escalation

*(Describe the misconfiguration or vulnerability used to escalate — e.g. weak service permissions, scheduled task, token privilege.)*

```bash
# Example: upload and run winPEAS
.\winPEASx64.exe
```

**Result:**
- *(How you obtained SYSTEM/admin access)*

![PrivEsc](screenshots/04-privesc.png)

---

### 5. Flags

| Flag | Value |
|------|-------|
| User flag | `THM{xxxxxxxxxxxxxxxx}` |
| Root flag | `THM{xxxxxxxxxxxxxxxx}` |

---

## 📚 Key Learnings

- *(e.g. How to enumerate SMB shares on Windows targets)*
- *(e.g. Importance of checking for outdated/vulnerable third-party software)*
- *(e.g. How misconfigured service permissions lead to privilege escalation)*

---



## 👤 Author

**Your Name**
- TryHackMe: [your-profile](https://tryhackme.com/p/your-profile)
- GitHub: [@your-username](https://github.com/your-username)

⭐ Star this repo if you found it helpful!
