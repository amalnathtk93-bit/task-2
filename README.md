# task-2
# Task 02 – Phishing Email Analysis

This repository contains the full analysis for **Task 02: Phishing Email Investigation**.  
The objective of this task was to analyze a suspicious email, extract its technical details, verify its authenticity using header analysis tools, perform link/domain checks, identify phishing indicators, and produce a final report.

---

## 📌 Repository Structure

task-02-phishing-email-analysis/
│
├── report.md # Full detailed phishing analysis report
├── 
│ └── message.txt # Redacted raw email source (headers + body)
│
├── analysis screen shoot
│ ├── header_analysis.png
│ ├── url_analysis.png
└── README.md

---

## 🛠️ Tools Used

### **Email Header Analysis**
- **Google Admin Toolbox – Messageheader**  
  https://toolbox.googleapps.com/apps/messageheader/

- **MXToolbox Header Analyzer**  
  https://mxtoolbox.com/EmailHeaders.aspx

### **URL & Domain Scanning**
- **URLVoid**  
  https://urlvoid.com/

- **VirusTotal**  
  https://www.virustotal.com/

### **Raw Header Extraction**
- Gmail → *Show Original*

---

## 📝 Task Steps Performed

1. **Extracted the raw email header and body** from Gmail using *Show Original*.  
2. **Analyzed SPF, DKIM, DMARC, ARC** authentication results.  
3. **Verified sender information**, routing hops, and original recipient.  
4. **Performed URL/domain scans** for suspicious elements in the email.  
5. **Reviewed email body** for social engineering techniques.  
6. **Identified Indicators of Compromise (IOCs)**.  
7. **Documented all findings** in `report.md`.  
8. **Added screenshots** from tools as supporting evidence.  
---

## 🔍 Summary of Findings

- Sender domain was spoofed.  
- SPF authentication returned **softfail (IP Unknown)**.  
- Email was originally addressed to **another domain** (`nydiscover.review`).  
- Body contained a **fake $799.67 payment alert** and a **scam helpline number**.  
- Domains used were **not associated with PayPal**.  
- Email used **social engineering** to pressure the user.

**Final Verdict:** The email is confirmed to be a **phishing / refund scam**.  
See **phishing_report.md** for full analysis.

---

## ⚠️ Privacy & Redaction Notice

All personal email addresses, names, and sensitive information have been replaced with:

