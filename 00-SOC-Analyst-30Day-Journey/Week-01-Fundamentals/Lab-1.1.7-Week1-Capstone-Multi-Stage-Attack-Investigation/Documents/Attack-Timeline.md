# COMPLETE ATTACK TIMELINE - INC-2025-001

## Kill Chain Phases

### Phase 1: INITIAL COMPROMISE (08:00 - 09:30)

**08:00:00** - Phishing email sent
- From: attacker@malicious-infra.ru (spoofed as HR)
- To: finance-team@securecorp.com
- Subject: Benefits enrollment
- Attachment: Benefits_Enrollment_2025.xlsx.exe (malware)

**09:15:00** - User receives email

**09:30:00** - User jsmith logs in to FINANCE-WS01
- Event ID 4624 (Successful Logon)

**09:31:00** - USER EXECUTES MALWARE ← INITIAL COMPROMISE
- Process: Benefits_Enrollment_2025.xlsx.exe
- User action: Double-clicked attachment

---

### Phase 2: PERSISTENCE (09:31 - 09:32)

**09:31:30** - Dropper creates backdoor
- File: C:\Users\Public\svchost.exe
- Registry: HKLM\...\Run\WindowsUpdate

**09:32:00** - C2 connection established
- Destination: 185.220.101.45:443
- Protocol: HTTPS (encrypted)
- Beacon interval: 60 seconds

---

### Phase 3: DISCOVERY (11:00 - 11:15)

**11:00:00** - Internal reconnaissance
- Command: net view
- Purpose: Enumerate network hosts

**11:00:00 - 11:10:00** - Port scanning
- Tool: Nmap
- Targets: 192.168.10.0/24
- Discovered: 15 live systems

**11:15:00** - DNS query for C2
- Domain: update-service.secure-corp-portal.com
- IP: 185.220.101.45

---

### Phase 4: LATERAL MOVEMENT (12:00 - 13:00)

**12:00:15** - Web app authentication attempt
- Target: WEB-APP-01 (192.168.10.100)
- Attempt: admin/admin (failed)

**12:00:30** - SQL INJECTION SUCCESSFUL ← PRIVILEGE ESCALATION
- Payload: ' OR 1=1--
- Result: Admin access bypassed

**12:05:00** - Admin panel accessed
- URL: /admin/dashboard.php

**12:10:00** - Database credentials stolen
- File: db-config.php
- Contains: MySQL username/password

**13:00:00** - Backdoor account created
- Username: backdoor
- Password: Passw0rd123!
- Role: admin

---

### Phase 5: COLLECTION (13:00 - 13:30)

**13:00:00** - Database connection
- Source: WEB-APP-01
- Target: DB-SQL-01:3306

**13:05:00** - Data extraction
- Query: SELECT * FROM customers
- Records: 45,000

**13:30:00** - File accessed
- Path: \\DB-SQL-01\SharedData\customer_database.xlsx
- User: jsmith

---

### Phase 6: EXFILTRATION (14:00 - 14:10)

**14:00:00** - DATA EXFILTRATION ← MISSION COMPLETE
- Destination: 185.220.101.45:443
- Data: 43.5 MB (customer database)
- Format: Password-protected ZIP

**14:10:00** - Exfiltration complete

---

### Phase 7: PERSISTENCE MAINTAINED (15:00+)

**15:00:00** - Backdoor still active
- Web account: backdoor user
- System: svchost.exe persistence
- C2: Beaconing every 60 seconds

**15:30:00** - Incident reported by IT

---

## Attack Summary

**Duration:** 6.5 hours (08:00 - 14:30)

**Compromised Systems:** 3 (FINANCE-WS01, WEB-APP-01, DB-SQL-01)

**Data Stolen:** 45,000 customer records (43.5 MB)

**Attacker IP:** 185.220.101.45 (Russia)

**Status:** ACTIVE THREAT (backdoors still present)