# 🛡️ Windows Fundamentals Mastery - Lab Notes

This repository contains my technical documentation and key takeaways from the **Windows Fundamentals** series on TryHackMe. As a cybersecurity learner, understanding the Windows OS architecture, registry, and security mechanisms is critical for threat hunting and incident response.

---

## 🏗️ Part 1: OS Architecture & Core Management
Focuses on the user-facing side of Windows and basic administration.

* **File System & Permissions:** Deep dive into `NTFS` permissions and the `System32` directory.
* **Process Management:** Utilizing **Task Manager** (`taskmgr.exe`) to monitor PID, CPU, and RAM consumption.
* **Control Center:** Navigation through **Control Panel** and **Settings** for user account management (UAC).
* **Shortcut of the Day:** `Ctrl + Shift + Esc` (Instant Task Manager).

---

## ⚙️ Part 2: System Configuration & Internals
Moving from the GUI to the engine room of the Operating System.

* **System Configuration (`msconfig`):** Managing boot options and system services.
* **Computer Management (`compmgmt.msc`):**
    * **Task Scheduler:** Auditing automated tasks (e.g., `npcapwatchdog`).
    * **Event Viewer:** Analyzing logs for security audits (Event IDs).
    * **Shared Folders:** Identifying hidden administrative shares (e.g., `C$`, `ADMIN$`).
* **The Registry (`regedit`):**
    * Understanding Hives: `HKLM` (System-wide) & `HKCU` (User-specific).
    * **Persistence Hunting:** Checking "Run" keys for unauthorized startup applications.
* **Resource Monitor (`resmon`):** Advanced analysis of Network TCP connections and Disk I/O.
* **System Information (`msinfo32`):** Detailed hardware and Environment Variable auditing (e.g., `ComSpec`, `Path`).

---

## 🛡️ Part 3: Security & Data Protection
Hardening the system against modern threats.

* **Patch Management:** Managing **Windows Updates** and the "Patch Tuesday" cycle.
* **Windows Security (Defender):**
    * **Real-time Protection:** The frontline against malware execution.
    * **Firewall Profiles:** `Domain`, `Private`, and `Public`.
    * **Exploit Protection:** Implementing `ASLR` and `DEP` to mitigate memory-based attacks.
* **Hardware Security (TPM):** Utilizing the **Trusted Platform Module**.
* **Data Integrity:**
    * **BitLocker:** Full Disk Encryption (FDE).
    * **VSS (Volume Shadow Copy):** System snapshots for recovery.
    * *Security Note:* Monitoring for `vssadmin` abuse by ransomware.

---

## 🛠️ Tools & Commands Summary

| Utility | Command | Purpose |
| :--- | :--- | :--- |
| **Registry Editor** | `regedit.exe` | Edit system configuration database |
| **Resource Monitor** | `resmon.exe` | Real-time CPU/Net/Disk/RAM tracking |
| **System Info** | `msinfo32.exe` | Hardware/software summary |
| **Firewall** | `wf.msc` | Advanced firewall management |
| **IP Config** | `ipconfig /all` | Network configuration |
| **UAC Settings** | `UserAccountControlSettings.exe` | Manage UAC |

---

## 🧪 Practical Notes

* Used `ipconfig /all` to identify local IP and gateway  
* Checked Event Viewer logs for failed login attempts  

---

## 🎯 Attacker Perspective

* Misconfigured services in `msconfig` can allow persistence  
* Registry "Run" keys are common for malware auto-start  
* Shadow Copies can be abused or deleted by ransomware  

---

## 📌 Conclusion

This lab strengthened my understanding of Windows internals, system monitoring, and defensive security mechanisms.

---

> **Cyber Tip:** Always verify the digital signatures of processes in Task Manager. If a process name looks legit (like `lsass.exe`) but isn't located in `C:\Windows\System32`, it's likely a masquerading threat.
