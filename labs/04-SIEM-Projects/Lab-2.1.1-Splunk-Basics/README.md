# Lab 2.1.1: Splunk SIEM - Installation & Fundamentals

**Date:** 23-01-2026  
**Analyst:** Raiza  
**Status:**  Completed  
**Category:** SIEM Operations  
**Difficulty:** Intermediate  
**Time Invested:** 6 Hours

## Executive Summary

Successfully deployed Splunk SIEM and ingested security telemetry from Windows, web, and network sources. Created 7 detection use cases covering 60% of MITRE ATT&CK tactics. Built automated alerting for high-priority threats (brute force, web exploitation, C2 communication). Developed real-time dashboard providing at-a-glance security posture visibility.


**Real-World Application:**  
This lab replicates Day 1 onboarding at a SOC where analysts receive SIEM access and must immediately begin threat hunting and alert triage.

---

## Tools Used

| Tool | Version | Purpose |
|------|---------|---------|
| **Splunk Enterprise** | 10 | SIEM platform |
| **SPL** | N/A | Search Processing Language |
| **Sample Datasets** | Custom | Windows, web, firewall logs |

## OBJECTIVE

- Install Splunk Free (Enterprise trial or Free tier)
- Understand Splunk architecture (indexers, search heads, forwarders)
- Index sample security datasets
- Learn SPL (Search Processing Language) basics
- Create basic security searches
- Save searches as alerts
- Build simple dashboard
- Export search results for reporting

## Step-by-Step Implementation

1. Step: Splunk Instalation 
2. Step: Data Ingestion
3. Step: SPL Mastery
4. Step: Alert Configuration
5. Step: Dashboard Creation
6. 


### Key Achievements
- **Data Ingestion:** 3 data sources indexed successfully
- **Detection Creation:** 7 SPL-based detections
- **MITRE Coverage:** 6/10 tactics detected
- **Automation:** 3 real-time alerts configured
- **Visualization:** 5-panel SOC dashboard


##  SPL Reference – Commands Used in Log Analysis

| Function               | SPL Command Example                                                                 |
|------------------------|-------------------------------------------------------------------------------------|
| **Basic search**       | `index="windows_security"`                                                          |
| **Field filtering**    | `index="windows_security" EventCode=4625`                                           |
| **Statistical count**  |``` stats count by User```                                                      |
| **Threshold detection**|``` where count > 3```                                                               |
| **Time-based analysis**| ```timechart count```                                                               |
| **Table output**       |``` table _time, User, ComputerName```                                              |
| **Sorting**            |``` sort -count```                                                                   |
| **Limit results**      |``` head 10```                                                                       |
| **Search within results**|``` search "OR 1=1"```                                                             |
| **Lookup enrichment**  |``` lookup threat_intel_lookup ip as dest_ip OUTPUT threat_level```                 |
| **Subsearch**          |```search index="firewall_logs"  stats values(src_ip)]```                          |

## MITRE ATT&CK Coverage

**Covered Tactics (6/10):**
- Initial Access (SQL Injection detection)
-  Execution (Suspicious process detection)
-  Persistence (Account creation)
-  Privilege Escalation (Admin group changes)
-  Credential Access (Brute force)
-  Command & Control (Beaconing)
-  Exfiltration (Large uploads)

**Gap Analysis:**
-  Discovery (need more telemetry)
-  Lateral Movement (need network logs)
-  Collection (need file access logs)

**Improvement Plan:**
- Add more data sources (DNS, proxy, EDR)
- Create additional detection rules
- Target 80%+ MITRE coverage

## Lessons Learned

### Technical Skills
1. **SIEMs aggregate chaos:** 3 log sources = 1 coherent view
2. **SPL is powerful:** Statistical analysis in single line
3. **Visualization matters:** Dashboard tells story instantly
4. **Alerts need tuning:** Too sensitive = alert fatigue

### SOC Operations
1. **Data quality > quantity:** Garbage in = garbage out
2. **Context is everything:** Single event meaningless, pattern is actionable
3. **Automation is essential:** Can't manually watch logs 24/7
4. **Documentation = knowledge base:** Use cases = institutional memory

### Career Insights
1. **SIEM skills = job requirement:** Appears in 60%+ SOC postings
2. **Splunk certification valuable:** SPLK-1001 (Core Certified User)
3. **Detection engineering emerging:** More than just queries, it's tradecraft
4. **Business communication key:** Dashboards for management, SPL for analysts

---

## Conclusion

Successfully deployed enterprise-grade SIEM platform and demonstrated operational proficiency in log aggregation, threat detection, automated alerting, and security monitoring visualization. Created 7 production-ready detection use cases covering 60% of MITRE ATT&CK framework.

### Skills Validation
- **SIEM Operations:** Data ingestion, index management, search optimization
- **SPL Proficiency:** 10+ searches, subsearches, statistical analysis
- **Detection Engineering:** Use case creation, MITRE mapping, alert tuning
- **Visualization:** Dashboard design, panel configuration, real-time monitoring

**Next Lab: Lab 2.1.2 - Advanced Splunk**