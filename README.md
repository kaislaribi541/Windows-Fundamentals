# 🛡️ Windows Fundamentals & Active Directory - Lab Notes

This repository contains my technical documentation and key takeaways from the **Windows Fundamentals** and **Active Directory** series on TryHackMe. As a cybersecurity learner, understanding Windows internals and domain environments is critical for threat hunting and incident response.

---

## 🏗️ Part 1: OS Architecture & Core Management

Focuses on the user-facing side of Windows and basic administration.

* **File System & Permissions:** Deep dive into `NTFS` permissions and the `System32` directory.  
* **Process Management:** Using **Task Manager** (`taskmgr.exe`) to monitor PID, CPU, and RAM.  
* **Control Center:** Navigating **Control Panel** and **Settings** (UAC).  
* **Shortcut:** `Ctrl + Shift + Esc` (Instant Task Manager).  

---

## ⚙️ Part 2: System Configuration & Internals

Moving from GUI to system internals.

* **System Configuration (`msconfig`):** Managing boot and services  
* **Computer Management (`compmgmt.msc`):**
  - Task Scheduler → audit automated tasks  
  - Event Viewer → analyze logs (Event IDs)  
  - Shared Folders → identify admin shares (`C$`, `ADMIN$`)  

* **Registry (`regedit`):**
  - Hives: `HKLM` & `HKCU`  
  - Persistence: checking **Run keys**

* **Resource Monitor (`resmon`)** → network + disk analysis  
* **System Info (`msinfo32`)** → hardware + env variables  

---

## 🛡️ Part 3: Security & Data Protection

* **Patch Management:** Windows Updates / Patch Tuesday  
* **Windows Defender:**
  - Real-time protection  
  - Firewall profiles (Domain / Private / Public)  
  - Exploit Protection (`ASLR`, `DEP`)  

* **TPM:** Hardware-based security  
* **Data Protection:**
  - BitLocker (FDE)  
  - VSS snapshots  
  - ⚠️ Monitor `vssadmin` abuse (ransomware)

---

## 🏛️ Part 4: Active Directory & Domain Administration

* **AD Structure:** Forests → Trees → Domains  
* **Objects & OUs:** Organizing users & machines  
* **GPOs:**
  - Restrict Control Panel  
  - Enforce password policies  
  - Auto-lock screens  

* **Authentication:**
  - Kerberos (secure, ticket-based)  
  - NetNTLM (legacy, weaker)  

* **Delegation:** Applying Least Privilege  

---

## 🛠️ Tools & Commands Summary

| Tool | Command | Purpose |
|------|--------|--------|
| Registry Editor | `regedit.exe` | System configuration |
| Resource Monitor | `resmon.exe` | System monitoring |
| Firewall | `wf.msc` | Firewall rules |
| AD Users | `dsa.msc` | Manage users/OUs |
| GPO Manager | `gpmc.msc` | Manage policies |
| GPO Update | `gpupdate /force` | Apply policies |

---

## 🧪 Practical Notes

* Used `ipconfig /all` to identify IP and gateway  
* Configured delegation on an OU  
* Reset password using PowerShell (`Set-ADAccountPassword`)  
* Verified GPOs using `gpresult /r`  

---

## 📌 Conclusion

This lab strengthened my understanding of Windows internals, system monitoring, and enterprise-level administration. Working with Active Directory and GPOs provided insight into how organizations secure infrastructure and detect privilege escalation or lateral movement.

---

> **Cyber Tip:** Always verify process paths and signatures. If a process like `lsass.exe` is not in `C:\Windows\System32`, it is likely malicious.
