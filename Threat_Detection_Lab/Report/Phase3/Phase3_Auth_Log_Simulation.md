 Threat Detection Lab – Phase 3: Auth.log Attack Simulation

## Objective

Simulate failed login attempts and sudo misuse to trigger entries in `/var/log/auth.log`. This demonstrates the system's ability to capture authentication-related activity, supporting detection and audit requirements.

---

## Step 1: Trigger Failed Login via SSH

**Command:**

```bash
ssh fakeuser@localhost
```

**Expected Output:**

```
Permission denied, please try again.
```

**Logged Event:**

```
Failed password for invalid user fakeuser from 127.0.0.1 port 22 ssh2
```

**Screenshot:** `FakeUser_SSH_Attempt.png`

---

## Step 2: Trigger Failed sudo Authentication

**Command:**

```bash
sudo ls
```

(Then enter an incorrect password twice)

**Logged Event:**

```
pam_unix(sudo:auth): authentication failure
```

**Screenshot:** `Failed_Sudo_AuthLog.png`

---

## Step 3: Trigger Valid sudo Command

**Command:**

```bash
sudo whoami
```

**Logged Event:**

```
sudo: zakiya : TTY=pts/0 ; PWD=/home/zakiya ; USER=root ; COMMAND=/usr/bin/whoami
```

**Screenshot:** `Sudo_Success_AuthLog.png`

---

## Log Review Commands

```bash
sudo grep "Failed password" /var/log/auth.log
sudo grep "authentication failure" /var/log/auth.log
sudo grep "sudo" /var/log/auth.log
```

---

## Control Mapping – NIST SP 800-53

| Control ID | Control Name                | Description                                           |
| ---------- | --------------------------- | ----------------------------------------------------- |
| AC-7       | Unsuccessful Login Attempts | Detect and monitor failed authentication attempts     |
| SI-4       | System Monitoring           | System activity monitoring for security-relevant data |

---

## Validation Summary

All simulated attacks were successfully logged in `/var/log/auth.log`. Evidence of failed SSH logins and sudo misuse was captured using `grep` and `tail -f`. Screenshots were saved for documentation and mapped to NIST controls AC-7 and SI-4, supporting RMF and ATO documentation practices.

---

**Next Step:** Integrate findings into RMF workbook and update GitHub project documentation.
