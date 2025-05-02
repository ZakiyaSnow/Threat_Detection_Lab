# Control Mapping – NIST SP 800-53

| Control ID | Control Name       | What Was Implemented                          | Command/Tool Used                  | Screenshot(s)                  | Status   |
|------------|--------------------|-----------------------------------------------|------------------------------------|-------------------------------|----------|
| AU-6       | Audit Review        | Monitored sudo command execution              | auditctl, ausearch                 | Sudo_Rule_Configured.png      | ✅ Done  |
| AU-2       | Audit Records       | Enabled auditd for audit record logging       | auditd, auditctl                   | Auditd_Status.png             | ✅ Done  |
| SI-4       | System Monitoring   | Reviewed logs for suspicious behavior         | ausearch, aureport                 | Sudo_Log_Result.png           | ✅ Done  |
| AU-12      | Audit Generation    | Persistent rule for sudo in `.rules` file     | /etc/audit/rules.d/ config         | Persistent_Sudo_Rule_File.png | ✅ Done  |
