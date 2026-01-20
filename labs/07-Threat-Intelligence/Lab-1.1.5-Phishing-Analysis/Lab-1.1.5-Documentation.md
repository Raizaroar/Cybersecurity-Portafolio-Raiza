## Project Overview

Comprehensive training in phishing email analysis, covering email header inspection, sender authentication verification (SPF/DKIM/DMARC), malicious link/attachment identification, and IOC extraction. Phishing is the #1 attack vector globally (90% of breaches start with phishing), making this skill essential for all SOC analysts.

**Real-World Relevance:**  
Every SOC analyst receives daily reports of suspicious emails. This lab teaches the EXACT workflow used in production environments to triage, analyze, and respond to potential phishing threats.

## LAB ENVIRONMENT

- **Analysis System:** Kali Linux (safe, isolated)
- **Email Samples:** From PhishTank, public repositories
- **Tools:** Web-based (MXToolbox, URLScan) + CLI
- **Network:** Internet required for online tools
- **Safety:** NEVER click suspicious links or open attachments directly

## PREREQUISITES

- Lab 1.1.4 completed 
- Kali Linux VM running
- Internet connection
- Email client installed (Thunderbird recommended)
- Understanding of basic email concepts (From, To, Subject)

## Real-life scenario:

I'm an SOC Analyst and several users have reported suspicious emails:

***“Your Office 365 account will be suspended”***
***“Outstanding invoice - attached”***
***“Reset your bank password urgently”***

My job:

- Analyze email headers
- Verify sender authenticity
- Inspect links (without clicking)
- Analyze attachments (without executing them)
- Determine if it is phishing
- Extract IOCs and recommend actions

