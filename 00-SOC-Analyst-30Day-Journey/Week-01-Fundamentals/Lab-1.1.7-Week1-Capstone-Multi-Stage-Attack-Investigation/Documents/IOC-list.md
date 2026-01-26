# INDICATORS OF COMPROMISE - INC-2025-001

**Incident:** SecureCorp Data Breach
**Date:** January 22, 2025
**Analyst:** Raiza
**Confidence:** HIGH

---

## Network IOCs (BLOCK AT FIREWALL)

### C2 Infrastructure
```
185.220.101.45          # Primary C2 server (Russia)
45.142.212.61           # Phishing email server
```

### Domains
```
malicious-infra.ru                           # Attacker infrastructure
secure-corp-portal.com                       # Typosquatting domain
secure-corp-portal.net                       # Reply-to domain
update-service.secure-corp-portal.com        # C2 domain
```

### URLs
```
http://192.168.10.100/admin/login.php?user=' OR 1=1--
http://192.168.10.100/admin/db-config.php
http://192.168.10.100/admin/create-user.php
```

---

## File IOCs (QUARANTINE/DELETE)

### Malware Hashes
```
MD5:    7c3f9f4e8d2c1b6a5e4f3c2d1a9b8e7f
SHA256: a1b2c3d4e5f6g7h8i9j0k1l2m3n4o5p6q7r8s9t0u1v2w3x4y5z6a7b8c9d0e1f2
```

### File Paths
```
C:\Users\jsmith\Downloads\Benefits_Enrollment_2025.xlsx.exe
C:\Users\Public\svchost.exe
\\DB-SQL-01\SharedData\customer_database.xlsx (exfiltrated)
```

### File Names
```
Benefits_Enrollment_2025.xlsx.exe
svchost.exe (in C:\Users\Public\)
```

---

## Registry IOCs (MONITOR/REMOVE)
```
HKLM\Software\Microsoft\Windows\CurrentVersion\Run\WindowsUpdate
Value: C:\Users\Public\svchost.exe
```

---

## Account IOCs (DISABLE/DELETE)

### Compromised Accounts
```
Domain: jsmith@securecorp.com
System: FINANCE-WS01
Status: Credentials likely stolen (keylogger)
```

### Malicious Accounts
```
Username: backdoor
Password: Passw0rd123!
Location: WEB-APP-01 admin panel
Created: 2025-01-22 13:00:00
```

---

## Email IOCs (BLOCK)

### Sender Addresses
```
hr-notifications@secure-corp-portal.com
attacker@malicious-infra.ru
benefits@secure-corp-portal.net
```

### Subject Lines
```
"URGENT: Updated Benefits Enrollment - Action Required"
```

---

## Behavioral IOCs (CREATE DETECTION RULES)

### Network Patterns
```
- Outbound HTTPS to 185.220.101.45:443 every 60 seconds
- Large outbound transfers (>40 MB) to non-corporate IPs
- Internal port scanning (Nmap signatures)
```

### Process Patterns
```
- svchost.exe running from C:\Users\Public\
- net.exe with "view" parameter
- SQL injection patterns in web logs
```

### Authentication Patterns
```
- Multiple failed logins followed by SQL injection
- New admin accounts created via web interface
```

---

## MITRE ATT&CK Techniques (for SIEM/EDR rules)
```
T1566.001 - Phishing: Spearphishing Attachment
T1204.002 - User Execution: Malicious File
T1547.001 - Boot/Logon Autostart: Registry Run Keys
T1036.005 - Masquerading: Match Legitimate Name
T1071.001 - Application Layer Protocol: Web Protocols
T1046 - Network Service Scanning
T1018 - Remote System Discovery
T1190 - Exploit Public-Facing Application
T1078.003 - Valid Accounts: Local Accounts
T1136.001 - Create Account: Local Account
T1005 - Data from Local System
T1039 - Data from Network Shared Drive
T1020 - Automated Exfiltration
T1041 - Exfiltration Over C2 Channel
T1560.001 - Archive Collected Data
```

---

## Recommended Actions

### IMMEDIATE (Next 1 hour)
- [ ] Block all network IOCs at firewall
- [ ] Quarantine FINANCE-WS01 from network
- [ ] Disable user account: jsmith
- [ ] Delete web account: backdoor
- [ ] Block email sender domains

### SHORT-TERM (Next 24 hours)
- [ ] Reimage FINANCE-WS01
- [ ] Patch SQL injection vulnerability on WEB-APP-01
- [ ] Reset all admin passwords
- [ ] Review all admin account activity
- [ ] Scan all systems for malware hash

### LONG-TERM (Next week)
- [ ] Implement email authentication (DMARC reject)
- [ ] Deploy EDR on all workstations
- [ ] Enable MFA for all accounts
- [ ] Security awareness training (phishing)
- [ ] Web Application Firewall (WAF) deployment