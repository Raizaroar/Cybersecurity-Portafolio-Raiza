# SOC in Splunk 

## Project Overview

This project is to design and implement a mini Security Operations Center (SOC) using Splunk, focused on detecting and visualizing failed login attempts. This is achieved by ingesting and analysing system logs. (e.g., auth.log from Kali), the project build a dashboard and SPL searches that highlight suspicious activity based on IP addresses, usernames, and login behavior.

Duration: 2-3 hours

Difficulty: Entry Level

Platform: Kali Linux 2025.2-virtualbox-amd64

## Tools Used:

Platform: Splunk Enterprise / Splunk Free
Simulated logs: auth.log


## Objective

1. Collecting and parsing authentication logs.

2. Creating a dashboard to monitor anomalies and failed logins.

3. Correlating events to identify potential brute-force or unauthorized access attempts.

4. Generating alerts to demonstrate how analysts can respond to abnormal conditions.

## Lab Environment

 System Information

OS: Kali Linux 2025.2-virtualbox-amd64

Splunk Enterprise (trial)

Network Interface: eth0 / wlan0

## SOC in Splunk

Analyst: Raiza Rosas Aguilar
Date: 30-11-25
Duration: 2 hours
Logs Analysis: successful

## Executive Summary

The primary objective is to detect and visualize failed login attempts, correlating events by IP address and user identity to highlight suspicious behavior such as brute-force attempts or unauthorized access. Splunk’s SPL queries and dashboards provide actionable insights, while alert configurations simulate incident response processes.

### Log Enrichment

GeoIP Mapping: Use Splunk’s IP Intelligence or external lookup tables to geolocate IP addresses.

User Categorization: Tag users by role (admin, guest, service) to detect privilege misuse or anomalies.

### Advanced Correlation

- *SPL searches that detect:*

Multiple failed logins followed by a successful one.

Logins from geographically distant IPs within short timeframes (impossible travel).

Access attempts outside business hours or from unusual user-agent strings.

### Simulated Response Actions

- *Configure alerts that:*

Trigger scripts to block IPs (e.g., via iptables or hosts.deny).

Log incidents into a mock ticketing system (e.g., simple dashboard).

### External Tool Integration

- *Simulate ingestion from:*

ModSecurity: to demonstrate WAF log analysis.

### Thematic Dashboards

- *Create separate dashboards for:*

User activity and login behavior.

Network traffic and suspicious patterns.

Active alerts and incident trends.

Platform: Splunk Enterprise / Splunk Free
Simulated logs: auth.log
Visualizations: Main dashboard with metrics by user, by IP, failed attempts, suspicious web traffic.
Alerts: SPL searches that detect anomalous conditions.

![Análisis de Wireshark](../../../../assets/screenshots/04-SIEM-Projects/Splunk/Lab-01-MyOwnSOC/Lab-01-MyOwnSOC.png)

## Search Engines examples

Detection of failed access attempts by user:

```Bash
index=main source="/var/log/auth.log" "Failed password"
| rex "from (?<src>\d+\.\d+\.\d+\.\d+)"
| top limit=10 src
```
