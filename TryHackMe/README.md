# 🌐 TryHackMe Write-ups

Collection of detailed walkthroughs and exploitation notes for TryHackMe rooms and vulnerable machines.

[![Back to Main](https://img.shields.io/badge/⬅%20Back%20to-Main%20Repository-blue?style=flat-square)](../README.md)
[![TryHackMe](https://img.shields.io/badge/TryHackMe-Quality15-red?style=flat-square&logo=tryhackme&logoColor=white)](https://tryhackme.com/p/Quality15)

---

## 📋 Completed Rooms & Machines

| Room | Difficulty | Key Vulnerability / Focus Area | Write-up |
| :--- | :---: | :--- | :---: |
| **Agent T** | 🟢 Easy | PHP 8.1.0-dev `User-Agentt` backdoor RCE to instant root shell | [View](Agent_T/Agent_T.md) |
| **Cyborg** | 🟢 Easy | Dirsearch recon, Apache MD5 cracking, Borg backup extraction, sudo bash privesc | [View](Cyborg/Cyborg.md) |
| **Dev Diaries** | 🟢 Easy | Subdomain fuzzing (`subfinder`), leaked GitHub commits & developer recon | [View](Dev_Diaries/Dev%20Diaries.md) |
| **Neighbour** | 🟢 Easy | Insecure Direct Object References (IDOR) on user profile endpoints | [View](Neighbour/Neighbour.md) |
| **Publisher** | 🟡 Medium | SPIP 4.2.0 RCE, AppArmor profile bypass via unconfined bash binary | [View](Publisher/Publisher.md) |
| **The Sticker Shop** | 🟢 Easy | Stored XSS in customer feedback form to exfiltrate internal `/flag.txt` | [View](The_Sticker_Shop/The%20Sticker%20Shop.md) |

---

## 🗂️ Room Directory Structure

```tree
room_name/
├── files/            # Exploits, wordlists, and artifacts
├── screenshots/      # PoC screenshots & diagrams
└── room_name.md      # Comprehensive walkthrough
```
