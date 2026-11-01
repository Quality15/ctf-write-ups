<div align="center">

# 🛡️ CTF Write-ups & Security Notes

<p align="center">
  <strong>A curated collection of write-ups, vulnerability walkthroughs, and exploit analyses across major CTF competitions and security labs.</strong>
</p>

[![Writeups](https://img.shields.io/badge/Total_Writeups-35+-00e676?style=for-the-badge&logo=gitbook&logoColor=white)](#catalog)
[![TryHackMe](https://img.shields.io/badge/TryHackMe-Quality15-red?style=for-the-badge&logo=tryhackme&logoColor=white)](https://tryhackme.com/p/Quality15)
[![HackTheBox](https://img.shields.io/badge/HackTheBox-Quality15-9cf?style=for-the-badge&logo=hackthebox&logoColor=white)](https://app.hackthebox.com/users/1188168)
[![picoCTF](https://img.shields.io/badge/picoCTF-Quality15-blue?style=for-the-badge&logo=target&logoColor=white)](https://play.picoctf.org/users/Quality15)
[![CTFtime](https://img.shields.io/badge/CTFtime-Quality15-yellow?style=for-the-badge&logo=clockify&logoColor=black)](https://ctftime.org/user/193182)

<p align="center">
  <img src="https://img.shields.io/badge/Web_Exploitation-12-orange?style=flat-square&logo=firefox" alt="Web Exploitation">
  <img src="https://img.shields.io/badge/General_Skills-11-blue?style=flat-square&logo=gnubash" alt="General Skills">
  <img src="https://img.shields.io/badge/Forensics-4-green?style=flat-square&logo=wireshark" alt="Forensics">
  <img src="https://img.shields.io/badge/Cryptography-3-purple?style=flat-square&logo=letsencrypt" alt="Cryptography">
  <img src="https://img.shields.io/badge/Reverse_Engineering-2-lightgrey?style=flat-square&logo=assemblyscript" alt="Reverse Engineering">
  <img src="https://img.shields.io/badge/Binary_Exploitation-2-red?style=flat-square&logo=c" alt="Binary Exploitation">
  <img src="https://img.shields.io/badge/OSINT-1-teal?style=flat-square&logo=search" alt="OSINT">
</p>

[📌 About](#about) •
[👤 Profiles](#profiles) •
[📊 Statistics](#statistics) •
[🗂️ Write-up Catalog](#catalog) •
[🧰 Arsenal](#arsenal) •
[📁 Structure](#structure) •
[📝 Template](#template)

---

</div>

<a id="about"></a>
## 📌 About

This repository documents my practical journey through cybersecurity challenges, capture-the-flag (CTF) events, and vulnerable target machines. Each write-up focuses on:
- **Reconnaissance & Enumeration**: Identifying the attack surface systematically.
- **Root Cause Analysis**: Explaining *why* the vulnerability exists in code or architecture.
- **Proof of Concept & Exploitation**: Reproducible steps, commands, and custom exploit scripts.
- **Remediation & Lessons Learned**: Key takeaways and security hardening insights.

---

<a id="profiles"></a>
## 👤 Author & Profiles

| Platform | Handle / Profile | Focus Area |
| :--- | :--- | :--- |
| **TryHackMe** | [![TryHackMe](https://img.shields.io/badge/Quality15-222222?style=flat&logo=tryhackme&logoColor=red)](https://tryhackme.com/p/Quality15) | Machine Exploitation, Privilege Escalation, Web Labs |
| **HackTheBox** | [![HackTheBox](https://img.shields.io/badge/1188168-222222?style=flat&logo=hackthebox&logoColor=9cf)](https://app.hackthebox.com/users/1188168) | Box Rooting, Active Directory, Real-world Scenarios |
| **picoCTF** | [![picoCTF](https://img.shields.io/badge/Quality15-222222?style=flat&logo=target&logoColor=blue)](https://play.picoctf.org/users/Quality15) | Web, Pwn, Crypto, Forensics, Reverse Engineering |
| **CTFtime** | [![CTFtime](https://img.shields.io/badge/Quality15-222222?style=flat&logo=clockify&logoColor=yellow)](https://ctftime.org/user/193182) | Competitive CTF Events & Team Rankings |
| **GitHub** | [![GitHub](https://img.shields.io/badge/Quality15-222222?style=flat&logo=github&logoColor=white)](https://github.com/Quality15) | Source Code, Tooling & Notes |

---

<a id="statistics"></a>
## 📊 Statistics & Breakdown

### By Platform
```
picoCTF      ██████████████████████████████  29 Challenges
TryHackMe    ██████                          6 Machines / Rooms
Total                                        35 Detailed Write-ups
```

### By Category
| Category | Count | Primary Techniques & Vulnerabilities |
| :--- | :---: | :--- |
| 🌐 **Web Exploitation** | 12 | RCE, IDOR, Stored XSS, XXE, SSTI, Spring Boot Heapdump leak, PHP Backdoors, File Upload |
| 🛠️ **General Skills & Linux** | 11 | Git internals (`log`, `branch`, commit author spoofing), Linux CLI, Endianness, SMB enumeration |
| 🔍 **Forensics** | 4 | PCAP traffic analysis, QR code reconstruction, SHA-256 verification, Exif metadata |
| 🔐 **Cryptography** | 3 | RSA small exponent / factorization, Hash cracking (Rainbow tables / CrackStation), Multi-layer ciphers |
| ⚙️ **Reverse Engineering** | 2 | UPX binary unpacking, Java bytecode analysis & branching logic |
| 💥 **Binary Exploitation (Pwn)** | 2 | Heap buffer overflow, PIE address leak & ret2func |
| 🕵️ **OSINT & Recon** | 1 | Subdomain enumeration (`subfinder`), commit history analysis & author tracking |

---

<a id="catalog"></a>
## 🗂️ Write-up Catalog

### 🌐 TryHackMe Rooms

| Room | Category | Difficulty | Key Concepts & Techniques | Write-up |
| :--- | :--- | :---: | :--- | :---: |
| **Agent T** | Web Exploitation | 🟢 Easy | PHP 8.1.0-dev `User-Agentt` backdoor RCE to instant root shell | [Read](TryHackMe/Agent_T/Agent_T.md) |
| **Cyborg** | Web & Linux PrivEsc | 🟢 Easy | Dirsearch recon, Apache MD5 cracking, Borg backup repository extraction, sudo bash script privesc | [Read](TryHackMe/Cyborg/Cyborg.md) |
| **Dev Diaries** | OSINT / Recon | 🟢 Easy | Subdomain enumeration with `subfinder`, investigating developer GitHub commits & abandoned repositories | [Read](TryHackMe/Dev_Diaries/Dev%20Diaries.md) |
| **Neighbour** | Web Exploitation | 🟢 Easy | Insecure Direct Object References (IDOR) on authentication / profile parameters | [Read](TryHackMe/Neighbour/Neighbour.md) |
| **Publisher** | Web & PrivEsc | 🟡 Medium | SPIP 4.2.0 RCE (CVE-2023-27372), AppArmor restricted shell escape using unconfined bash binary | [Read](TryHackMe/Publisher/Publisher.md) |
| **The Sticker Shop** | Web Exploitation | 🟢 Easy | Stored XSS in customer feedback form, exfiltrating internal `flag.txt` from local service | [Read](TryHackMe/The_Sticker_Shop/The%20Sticker%20Shop.md) |

---

### 🚩 picoCTF 2026

| Challenge | Category | Difficulty | Key Concepts & Techniques | Write-up |
| :--- | :--- | :---: | :--- | :---: |
| **MY GIT** | General Skills | 🟢 Easy | Git over SSH, commit author spoofing (`root:root@picoctf`) | [Read](picoCTF/picoCTF2026/MY%20GIT.md) |
| **Piece by Piece** | General Skills | 🟢 Easy | Linux CLI split chunk concatenation (`cat part_* > combined.zip`) | [Read](picoCTF/picoCTF2026/Piece%20by%20Piece.md) |
| **Printer Shares** | General Skills | 🟢 Easy | Network printer share reconnaissance using `smbclient` | [Read](picoCTF/picoCTF2026/Printer%20Shares.md) |
| **bytemancy 1** | General Skills | 🟢 Easy | Python byte sequence matching & payload crafting (`\x65` * 1751) | [Read](picoCTF/picoCTF2026/bytemancy%201.md) |
| **ping-cmd** | General Skills | 🟢 Easy | OS Command Injection via ping IP parameter (`8.8.8.8; ls -la`) | [Read](picoCTF/picoCTF2026/ping-cmd.md) |

---

### 🚩 picoCTF 2025

| Challenge | Category | Difficulty | Key Concepts & Techniques | Write-up |
| :--- | :--- | :---: | :--- | :---: |
| **Cookie Monster Secret Recipe** | Web Exploitation | 🟢 Easy | HTTP cookie inspection and tampering | [Read](picoCTF/picoCTF2025/Cookie%20Monster%20Secret%20Recipe.md) |
| **EVEN RSA CAN BE BROKEN???** | Cryptography | 🟢 Easy | RSA cipher decryption with small public exponent / factorization | [Read](picoCTF/picoCTF2025/EVEN%20RSA%20CAN%20BE%20BROKEN%3F%3F%3F.md) |
| **Flag Hunters** | Reverse Engineering | 🟢 Easy | Java bytecode analysis and control-flow reconstruction | [Read](picoCTF/picoCTF2025/Flag%20Hunters.md) |
| **PIE TIME** | Binary Exploitation | 🟢 Easy | Position Independent Executable (PIE) address leak and buffer overflow | [Read](picoCTF/picoCTF2025/PIE%20TIME.md) |
| **Ph4nt0m 1ntrud3r** | Forensics | 🟢 Easy | PCAP packet analysis, stream reconstruction & Wireshark filtering | [Read](picoCTF/picoCTF2025/Ph4nt0m%201ntrud3r.md) |
| **RED** | Forensics | 🟢 Easy | Image metadata and Exif tag extraction | [Read](picoCTF/picoCTF2025/RED.md) |
| **Rust fixme 3** | General Skills | 🟢 Easy | Resolving compiler errors and syntax bugs in Rust source code | [Read](picoCTF/picoCTF2025/Rust%20fixme%203.md) |
| **SSTI1** | Web Exploitation | 🟢 Easy | Server-Side Template Injection (`{{ ... }}`) | [Read](picoCTF/picoCTF2025/SSTI1.md) |
| **hashcrack** | Cryptography | 🟢 Easy | Cracking salted/weak password hashes using CrackStation | [Read](picoCTF/picoCTF2025/hashcrack.md) |
| **head-dump** | Web Exploitation | 🟢 Easy | JVM Heapdump memory inspection to uncover exposed environment secrets | [Read](picoCTF/picoCTF2025/head-dump.md) |
| **n0s4n1ty 1** | Web Exploitation | 🟢 Easy | Unrestricted file upload leading to web shell execution | [Read](picoCTF/picoCTF2025/n0s4n1ty%201.md) |

---

### 🚩 picoCTF 2024

| Challenge | Category | Difficulty | Key Concepts & Techniques | Write-up |
| :--- | :--- | :---: | :--- | :---: |
| **Blame Game** | General Skills | 🟢 Easy | Git history analysis using `git log` and `git blame` | [Read](picoCTF/picoCTF2024/Blame_Game.md) |
| **Collaborative Development** | General Skills | 🟢 Easy | Git branch exploration (`git branch -a`) and multi-branch feature aggregation | [Read](picoCTF/picoCTF2024/Collaborative_Development.md) |
| **Commitment Issues** | General Skills | 🟢 Easy | Deleted file recovery via `git log -p` and commit diff inspection | [Read](picoCTF/picoCTF2024/Commitment_issues.md) |
| **IntroToBurp** | Web Exploitation | 🟢 Easy | Intercepting and modifying HTTP POST requests using Burp Suite | [Read](picoCTF/picoCTF2024/IntroToBurp.md) |
| **Scan Surprise** | Forensics | 🟢 Easy | QR Code decoding from challenge image file | [Read](picoCTF/picoCTF2024/Scan_Surprise.md) |
| **Time Machine** | General Skills | 🟢 Easy | Reviewing repository commit logs for author notes | [Read](picoCTF/picoCTF2024/Time_Machine.md) |
| **Verify** | Forensics | 🟢 Easy | SHA-256 hash checksum matching and decryption scripting | [Read](picoCTF/picoCTF2024/Verify.md) |
| **endianness** | General Skills | 🟢 Easy | Understanding Big-Endian vs Little-Endian byte representations in C | [Read](picoCTF/picoCTF2024/endianness.md) |
| **heap 0** | Binary Exploitation | 🟢 Easy | Heap buffer overflow corrupting an adjacent variable in memory | [Read](picoCTF/picoCTF2024/heap_0.md) |
| **interencdec** | Cryptography | 🟢 Easy | Multi-stage decryption combining Base64 and Caesar rotation | [Read](picoCTF/picoCTF2024/interencdec.md) |
| **packer** | Reverse Engineering | 🟡 Medium | Identifying UPX packed ELF binaries, unpacking with `upx -d`, and binary analysis | [Read](picoCTF/picoCTF2024/packer.md) |

---

### 🚩 picoCTF 2023 & picoMini

| Challenge | Event | Category | Difficulty | Key Concepts & Techniques | Write-up |
| :--- | :--- | :--- | :---: | :--- | :---: |
| **SOAP** | picoCTF 2023 | Web Exploitation | 🟡 Medium | XML External Entity (XXE) injection targeting `/etc/passwd` | [Read](picoCTF/picoCTF2023/SOAP.md) |
| **caas** | picoMini | Web Exploitation | 🟡 Medium | Cowsay-as-a-service command injection via URL parameter | [Read](picoCTF/picoCTFMini/caas.md) |

---

<a id="arsenal"></a>
## 🧰 Tools & Arsenal

A non-exhaustive list of security tools and utilities utilized across these solutions:

| Category | Tools & Libraries |
| :--- | :--- |
| **Reconnaissance & Enumeration** | `Nmap`, `ffuf`, `dirsearch`, `subfinder`, `smbclient`, `Nikto` |
| **Web Exploitation** | `Burp Suite`, `Postman`, `CyberChef`, `curl`, `OWASP ZAP` |
| **Network & Forensics** | `Wireshark`, `tcpdump`, `ExifTool`, `binwalk`, `zsteg` |
| **Reverse Engineering & Pwn** | `GDB` (`pwndbg` / `GEF`), `Ghidra`, `UPX`, `pwntools`, `strings`, `radare2` |
| **Cryptography & Password Cracking** | `John the Ripper`, `Hashcat`, `CrackStation`, `dCode`, `PyCryptodome` |
| **Automation & Scripting** | `Python 3`, `Bash`, `Rust` |

---

<a id="structure"></a>
## 📁 Repository Structure

```tree
.
├── picoCTF/
│   ├── picoCTF2023/          # picoCTF 2023 challenges (SOAP, ...)
│   ├── picoCTF2024/          # picoCTF 2024 challenges (Git, Heap, Endianness, ...)
│   ├── picoCTF2025/          # picoCTF 2025 challenges (RSA, SSTI, Heapdump, ...)
│   ├── picoCTF2026/          # picoCTF 2026 challenges (SMB, Bytes, Git, ...)
│   └── picoCTFMini/          # picoMini series (caas, ...)
│
├── TryHackMe/
│   ├── Agent_T/              # Agent T machine (PHP 8.1.0-dev RCE)
│   ├── Cyborg/               # Cyborg machine (Borg Backup, MD5, PrivEsc)
│   ├── Dev_Diaries/          # Dev Diaries (OSINT, GitHub leak)
│   ├── Neighbour/            # Neighbour room (IDOR vulnerability)
│   ├── Publisher/            # Publisher room (SPIP RCE, AppArmor bypass)
│   ├── The_Sticker_Shop/     # The Sticker Shop (Stored XSS exfiltration)
│   └── README.md             # THM directory overview
│
└── README.md                 # Main repository index & portfolio
```

---

<a id="template"></a>
## 📝 Write-up Template

For consistent styling and Obsidian compatibility, write-ups follow this template:

```markdown
---
created at: YYYY-MM-DD || HH:MM
category: <Category Name>
tags:
  - <Event_Tag>
difficulty: <Easy | Medium | Hard>
---

# <Challenge or Room Name>

## Task / Room Description
> Brief overview of the challenge prompt, goal, and provided files or URLs.

## Solution

### 1. Reconnaissance & Enumeration
- Initial discovery commands, nmap/ffuf outputs, and findings.

### 2. Vulnerability Analysis
- Explanation of the root vulnerability (source code, protocol flaw, misconfiguration).

### 3. Exploitation & Flag
- Step-by-step commands, payload construction, or script execution.
```bash
# Exploit commands or payload here
```
- **Flag**: `picoCTF{...}` or `THM{...}`

## Key Takeaways
- What was learned and how this vulnerability is prevented.
```

---

<a id="disclaimer"></a>
## ⚖️ Disclaimer

> [!IMPORTANT]
> The scripts, write-ups, and materials in this repository are published **strictly for educational and defensive security purposes**. All security assessments were performed in authorized, sandboxed CTF environments or deliberately vulnerable virtual machines. Unauthorized access to computer systems is illegal under applicable cybercrime legislation.

---

<div align="center">
  <sub>Maintained with 🛡️ by <a href="https://github.com/Quality15">Quality15</a> • Last updated 2026</sub>
</div>
