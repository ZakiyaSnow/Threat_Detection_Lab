 🛡️ Threat Detection Lab (Ubuntu 24.04 + auditd)

This lab simulates how a junior cybersecurity analyst can configure and validate audit-based detection controls in Ubuntu 24.04. The focus is on capturing system activity such as privileged command execution and reviewing logs using native Linux auditing tools.

This lab aligns with **NIST SP 800-53** controls such as **AU-6 (Audit Review)**, **AU-2 (Audit Records)**, and **SI-4 (System Monitoring)**. It supports RMF/ATO readiness by producing log evidence, control narratives, screenshots, and documentation artifacts.

---

## 🎯 Lab Objectives

- Configure `auditd` on Ubuntu 24.04 for event logging
- Create custom audit rules using `auditctl`
- Detect and log execution of privileged commands (e.g., `sudo`)
- Review logs using `ausearch` and save outputs as evidence
- Create persistent audit rules
- Document control implementation aligned with RMF/ATO

---

## 🛠️ Tools Used

| Tool       | Purpose                          |
|------------|----------------------------------|
| `auditd`   | Linux auditing daemon            |
| `auditctl` | Add real-time audit rules        |
| `ausearch` | Review audit logs by keyword     |
| `aureport` | Summarize audit logs             |
| `systemctl`| Service control (start/enable auditd) |

---

## 📁 Folder Structure

```
Threat_Detection_Lab/
├── Ubuntu/
│   ├── Audit_Rules/            # auditctl rules and .rules files
│   ├── Detection_Logs/         # ausearch outputs
│   ├── Notes/                  # markdown notes
│   └── Screenshots/            # captured screenshots
├── Documentation/
│   ├── AU-6_Control_Narrative.docx
│   ├── Control_Mapping_SP800-53.xlsx
│   └── ThreatDetection_Reflection_ZakiyaMoore.pdf
├── README.md
```

---

## ✅ Implemented Control: AU-6 (Audit Review)

**Control Objective:** Ensure audit logs are reviewed for unusual or unauthorized activity.

- Enabled `auditd`
- Created rule: `auditctl -a always,exit -F path=/usr/bin/sudo -F perm=x -k sudo_monitoring`
- Triggered activity using `sudo`
- Captured log using `ausearch -k sudo_monitoring`
- Saved log and screenshots as evidence
- Rule made persistent using `/etc/audit/rules.d/sudo.rules`

📸 Screenshots:
- `Auditd_Status.png`
- `Sudo_Rule_Configured.png`
- `Sudo_Log_Result.png`
- `Persistent_Sudo_Rule_File.png`

📄 Documentation:
- `AU-6_Control_Narrative.docx`
- Log output: `sudo_monitoring_log.txt`

---

## 📸 Screenshot Checklist – `sudo_monitoring`

| # | Screenshot Purpose                | Command                              | Filename                        |
|---|----------------------------------|--------------------------------------|---------------------------------|
| 1️⃣ | Confirm `auditd` is active       | `sudo systemctl status auditd`       | `Auditd_Status.png`             |
| 2️⃣ | Show rule was added             | `sudo auditctl -l \| grep sudo`      | `Sudo_Rule_Configured.png`      |
| 3️⃣ | Generate log activity           | `sudo ls /root` *(no screenshot)*    | *(skip)*                        |
| 4️⃣ | View logs matching rule         | `sudo ausearch -k sudo_monitoring`   | `Sudo_Log_Result.png`           |
| 5️⃣ | Save logs (optional)            | `cat sudo_monitoring_log.txt`        | `Saved_Log_Output.png` *(opt)*  |
| 6️⃣ | Show persistent rule file       | `cat /etc/audit/rules.d/sudo.rules`  | `Persistent_Sudo_Rule_File.png` |

---

## 📈 What's Next

- Add monitoring for access to `/etc/passwd` and failed login attempts
- Map controls to AU-2, AU-12, AC-6, and SI-4
- Expand documentation and narratives for additional controls
- Push updates to GitHub repo with each new detection scenario

---

> "Log what matters. Review what counts. Document everything."

Lab
