# Phishing Email Detection Checklist

**Use this checklist for EVERY suspicious email.**

---

## 1. Sender Verification (CRITICAL)

- [ ] Check "From" address domain carefully
  - Does it match the claimed organization exactly?
  - Look for typos (micros0ft.com, goog1e.com)
  
- [ ] Compare "From" vs "Return-Path"
  - Different domains =  RED FLAG
  
- [ ] Check "Reply-To" address
  - Should match "From" for legitimate emails
  
- [ ] Verify display name vs actual email
  - Example: "Microsoft" <attacker@evil.com> = FAKE

---

## 2. Email Authentication

- [ ] SPF Record
  -  PASS = Good
  -  FAIL = Unauthorized sender
  
- [ ] DKIM Signature
  -  PASS = Authentic
  -  FAIL = Tampered/Forged
  
- [ ] DMARC Policy
  -  PASS = Legitimate
  -  FAIL = Should be rejected

---

## 3. Content Analysis

- [ ] Greeting
  - Generic ("Dear Customer") = Worse
  - Personalized ("Dear John Smith") =  Better
  
- [ ] Language Quality
  - Professional = Could be legit OR sophisticated phishing
  - Poor grammar/spelling =  Likely phishing
  
- [ ] Urgency/Fear Tactics
  - "Account will be closed" = Bad
  - "Suspicious activity" = Bad
  - "Immediate action required" = Bad 
  
- [ ] Requests
  - Asking for credentials =  NEVER legitimate
  - Requesting sensitive info = Bad 

---

## 4. Link Analysis (NEVER CLICK)

- [ ] Hover over link (don't click)
  - Does displayed text match actual URL?
  
- [ ] Check domain in URL
  - microsoft.com = Legitimate
  - microsoft-secure.malicious.com = Fake
  
- [ ] Look for URL shorteners
  - bit.ly, tinyurl.com = Hides destination
  
- [ ] Use URLScan.io
  - Paste URL for safe analysis
  - Check verdict before visiting

---

## 5. Attachment Analysis (NEVER OPEN)

- [ ] File extension
  - .pdf, .docx, .xlsx = Usually safe (but check for macros)
  - .exe, .scr, .bat = DANGEROUS
  - Double extensions (.pdf.exe) = MALWARE
  
- [ ] File size
  - Suspiciously small (5KB "invoice.pdf") = Malicious
  - Suspiciously large (50MB email) = Malicious
  
- [ ] Generate hash
  - sha256sum filename
  - Check hash on VirusTotal
  
- [ ] Expected vs Actual
  - Expecting invoice but got .exe = Malicious

---

## 6. Context Verification

- [ ] Were you expecting this email?
  - Unsolicited = Higher suspicion
  
- [ ] Does sender know information they shouldn't?
  - Personal details in phishing = Spearphishing
  
- [ ] Can you verify via another channel?
  - Call company directly (NOT number in email)
  - Visit official website (type URL, don't click link)

---

## 7. Technical Indicators

- [ ] Originating IP reputation
  - Check AbuseIPDB.com
  - Check MXToolbox blacklists
  
- [ ] Domain age
  - Newly registered (< 30 days) = Bad
  - Check WHOIS lookup
  
- [ ] SSL/TLS certificate
  - Legitimate companies use HTTPS
  - Self-signed certs = Bad

---

## FINAL DECISION MATRIX

### LEGITIMATE (Forward/Act)

- SPF/DKIM/DMARC: PASS
- Known sender
- Expected communication
- No suspicious links/attachments
- Professional content

### SUSPICIOUS (Investigate Further)

- One authentication failure
- Unexpected but plausible
- Minor red flags
- Verify through alternate channel

### PHISHING (Report/Delete)


- Multiple authentication failures
- Typosquatted domain
- Malicious links/attachments
- Urgency/fear tactics
- Requests credentials

---

## ACTIONS TO TAKE

***If Legitimate:***
1. Process normally
2. Document if unusual

***If Suspicious:***
1. DO NOT CLICK ANYTHING
2. Forward to security team
3. Verify with sender via phone/alternate email
4. Await analysis

***If Phishing:***
1. DO NOT CLICK/OPEN ANYTHING
2. Report to security team immediately
3. Forward to phishing@company.com
4. Delete from inbox
5. Alert colleagues if targeted campaign
6. Change passwords if credentials entered

---
