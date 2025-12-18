# Metasploitable 2 – Remote Root Compromise (vsFTPd 2.3.4)

## 📌 Project Overview
This project documents the exploitation of **Metasploitable 2**, an intentionally vulnerable Linux virtual machine, as part of a controlled local penetration testing lab. The objective was to identify exposed services, research known vulnerabilities, and successfully gain unauthorized access to the system.

The attack was performed **ethically and legally** in a local VMware lab environment using Kali Linux.

---

## 🧪 Lab Environment
- **Attacker Machine:** Kali Linux
- **Target Machine:** Metasploitable 2
- **Virtualization:** VMware
- **Network Type:** Host-Only / NAT (isolated lab)
- **Tools Used:** Nmap, Metasploit Framework

---

## 🎯 Target Identification
The Metasploitable 2 machine was discovered via network scanning.

nmap -sn 192.168.181.0/24

<img width="599" height="323" alt="image" src="https://github.com/user-attachments/assets/e452feb9-0311-4901-9a29-c56b5a6f61e4" />


nmap -sV 192.168.181.129

<img width="749" height="547" alt="image" src="https://github.com/user-attachments/assets/afc85ca0-a9f4-4aa9-9453-29d40a6bf568" />

Key Finding

FTP Service: vsFTPd 2.3.4

This version is known to contain a hardcoded backdoor vulnerability that allows remote command execution.

## **💥 Vulnerability Details**

  Service: vsFTPd

  Version: 2.3.4

  Vulnerability Type: Backdoor / Remote Command Execution

  Disclosure Year: 2011

  Impact: Unauthenticated root shell access

## **🚀 Exploitation**

The vulnerability was exploited using the Metasploit Framework.

<img width="1151" height="550" alt="image" src="https://github.com/user-attachments/assets/d51223c7-887d-4ea4-9eb4-9c41771aa081" />

<img width="918" height="241" alt="image" src="https://github.com/user-attachments/assets/482aa3bc-ac89-4d4e-9631-189b1c0f39f7" />

<img width="699" height="139" alt="image" src="https://github.com/user-attachments/assets/898c838e-e6d3-4ace-ba32-d678794c6fa3" />

Result

  >Backdoor service spawned on TCP port 6200

  >Root-level command shell obtained

  >Full system compromise achieved

UID: uid=0(root) gid=0(root)
Command shell session opened

Additional enumeration was performed:
<img width="744" height="552" alt="image" src="https://github.com/user-attachments/assets/2c29a6ea-76f7-4a49-a7e6-23e8e2231a34" />

<img width="830" height="555" alt="image" src="https://github.com/user-attachments/assets/e6f56c8e-4fb1-421b-ac1a-a518580ff92c" />

<img width="1152" height="534" alt="image" src="https://github.com/user-attachments/assets/8c685b5f-0acc-4451-af1d-44de4005098e" />

## **📈 Impact Assessment**

An attacker exploiting this vulnerability can:

  Execute arbitrary commands as root

  Access sensitive system files

  Maintain persistence

  Fully compromise the host

  This demonstrates the critical risk of running outdated services.

## **🛡️ Mitigation & Defensive Recommendations**

  Remove or upgrade vulnerable FTP services

  Disable FTP in favor of SFTP

  Enforce strict patch management

  Restrict network exposure of internal services

  Apply the principle of least privilege

## **🧠 Key Learnings**

  Importance of service version enumeration

  Value of researching known vulnerabilities

  Practical exploitation using Metasploit

  Understanding real-world misconfigurations

  Proper documentation of penetration testing activities

## **⚠️ Legal & Ethical Disclaimer**

This project was conducted solely in a controlled lab environment on intentionally vulnerable systems. No unauthorized systems were accessed. This documentation is for educational purposes only.

## 🔗 References

  Metasploitable Project

  Metasploit Framework Documentation

  Nmap Documentation






