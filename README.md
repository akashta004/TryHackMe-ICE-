# 🛡️ TryHackMe | ICE 


> An isolated virtual lab for practicing ethical hacking, network scanning and vulnerability assessment.

---

## 📌 Table of Contents
- [Project Overview](#-project-overview)
- [Objectives](#-objectives)
- [Lab Architecture](#-lab-architecture)
- [Requirements](#-requirements)
- [Setup Guide](#-setup-guide)
- [Tools Used](#-tools-used)
- [Walkthrough](#-walkthrough)
- [Key Learnings](#-key-learnings)
- [Disclaimer](#-disclaimer)
- [Author](#-author)

---

## 📖 Project Overview

This project documents the cybersecurity lab I built using **Kali Linux** (attacker machine) and **VirtualBox** (virtualization platform). The lab runs on an isolated network so I can safely practice penetration testing techniques on intentionally vulnerable machines.

---

## 🎯 Objectives

- Build a safe, isolated environment for ethical hacking practice
- Learn the penetration testing workflow: recon → scanning → exploitation → reporting
- Get hands-on with industry-standard tools
- Document my work as a cybersecurity portfolio

---

## 🏗️ Lab Architecture

| Machine | Role | OS | RAM | IP Address |
|---------|------|----|-----|------------|
| Kali Linux | Attacker | Kali Linux | 4 GB | 192.168.56.101 |
| Target VM | Victim | (e.g. Metasploitable 2) | 1 GB | 192.168.56.102 |

**Network type:** Host-Only / NAT Network (isolated from the home network)

```
+----------------+        Host-Only Network        +------------------+
|  Kali Linux    | <-----------------------------> |   Target VM      |
|  (Attacker)    |        192.168.56.0/24          |   (Vulnerable)   |
+----------------+                                 +------------------+
```

> 🔧 Replace the machines and IPs above with your own.

---

## 💻 Requirements

- Host PC with at least 8 GB RAM (16 GB recommended)
- 50+ GB free disk space
- Virtualization (VT-x / AMD-V) enabled in BIOS
- [VirtualBox](https://www.virtualbox.org/) and Extension Pack
- [Kali Linux image](https://www.kali.org/get-kali/)

---

## ⚙️ Setup Guide

1. Install VirtualBox on the host machine.
2. Download and import the Kali Linux VirtualBox image.
3. Create a Host-Only or NAT Network in `File → Tools → Network Manager`.
4. Import the target VM and attach it to the same network.
5. Start both VMs and check connectivity:

```bash
ip a
ping -c 4 <target-ip>
nmap -sn 192.168.56.0/24
```

6. Take a **snapshot** of each VM in a clean state.

📷 *Screenshot of final setup:*

![Lab Setup](screenshots/lab-setup.png)

---

## 🧰 Tools Used

| Category | Tools |
|----------|-------|
| Reconnaissance | Nmap, Netdiscover |
| Vulnerability Scanning | Nikto, OpenVAS |
| Exploitation | Metasploit, SQLmap |
| Web Testing | Burp Suite, Gobuster |
| Password Attacks | John the Ripper, Hydra |
| Traffic Analysis | Wireshark |

---

## 🔍 Walkthrough

### Step 1: Network Discovery
Found live hosts on the lab network.

```bash
nmap -sn 192.168.56.0/24
```
![Step 1](screenshots/step1.png)

### Step 2: Port & Service Scan
Identified open ports and service versions on the target.

```bash
nmap -sV -sC -p- 192.168.56.102
```
![Step 2](screenshots/step2.png)

### Step 3: Vulnerability Identification
*(Describe what you found, e.g. outdated FTP service.)*

### Step 4: Exploitation
*(Describe the exploit and tool used, with a screenshot.)*

### Step 5: Findings & Mitigation
*(What was vulnerable, and how it can be fixed or hardened.)*

---

## 📚 Key Learnings

- How to build and isolate a safe virtual lab
- How scanning reveals attack surface
- Why patching and hardening matter
- How to document findings clearly

---

## ⚠️ Disclaimer

This project is for **educational purposes only**. All testing was done in my own isolated lab on machines I own. Never test systems without explicit permission. Unauthorized access is illegal.

---

## 👤 Author

**Your Name**
- GitHub: [@your-username](https://github.com/your-username)
- LinkedIn: [your-profile](https://linkedin.com/in/your-profile)

⭐ Star this repo if you found it helpful!
