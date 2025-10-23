# elabst2
🕵️‍♂️ Phishing Email Analysis – Microsoft Spoofing Case Study
📄 Overview

This project demonstrates a step-by-step forensic analysis of a phishing email impersonating Microsoft.
The investigation covers sender validation, header inspection, link and URL checks, and language analysis, ending with a final security assessment.

The objective is to showcase practical email forensics and threat detection skills used in cybersecurity investigations.

🧰 Tools & Environment

| Tool                                                          | Purpose                                 |
| ------------------------------------------------------------- | --------------------------------------- |
| **Kali Linux / Ubuntu**                                       | Analysis environment                    |
| **grep, cat, less**                                           | Text extraction and pattern search      |
| **Online Header Analyzer** (MXToolbox / Google Admin Toolbox) | Email header validation                 |
| **VirusTotal / URLVoid**                                      | Link & domain safety checks             |
| **Wireshark (optional)**                                      | Network-level trace analysis            |
| **LibreOffice / ReportLab**                                   | Documentation and PDF report generation |



🧩 Steps Followed
| Step                            | Description                                 | Command / Tool Used          |                             |        |            |                          |
| ------------------------------- | ------------------------------------------- | ---------------------------- | --------------------------- | ------ | ---------- | ------------------------ |
| **1. Obtain sample email**      | Downloaded `.eml` phishing sample           | `wget sample-1034.eml`       |                             |        |            |                          |
| **2. Examine sender address**   | Checked “From” and “Reply-To” fields        | `grep -iE 'from:             | reply-to:' sample-1034.eml` |        |            |                          |
| **3. Analyze headers**          | Parsed full headers to check SPF/DKIM/DMARC | Online header analyzer       |                             |        |            |                          |
| **4. Check suspicious links**   | Extracted all links                         | `grep -iE 'http              | https' human_text.txt`      |        |            |                          |
| **5. Identify urgent language** | Searched for suspicious/urgent terms        | `grep -iE 'alert             | urgent                      | verify | click here | unusual' human_text.txt` |
| **6. Find mismatched URLs**     | Compared displayed and real hyperlinks      | Hover/inspect method         |                             |        |            |                          |
| **7. Check grammar/spelling**   | Manually reviewed extracted text            | Manual observation           |                             |        |            |                          |
| **8. Summarize findings**       | Compiled results in structured table        | Markdown summary (see below) |                             |        |            |                          |

🧾 Phishing Analysis Summary
| Checkpoint                   | Finding                                                   | Status                  | Severity    |
| ---------------------------- | --------------------------------------------------------- | ----------------------- | ----------- |
| **1. Sample email obtained** | File `sample-1034.eml` analyzed safely                    | ✅ Legitimate procedure  | 🟢 Low      |
| **2. Sender spoofing**       | `no-reply@access-accsecurity.com` impersonating Microsoft | 🚩 Fake domain          | 🔴 High     |
| **3. Reply-To mismatch**     | `solutionteamrecognizd03@gmail.com`                       | 🚩 Attacker-controlled  | 🔴 High     |
| **4. Header discrepancies**  | Return-Path & SPF/DKIM failures                           | 🚩 Spoofed mail routing | 🔴 High     |
| **5. Suspicious link**       | `http://thebandalisty.com/track/...` (dead domain)        | 🚩 Phishing indicator   | 🟠 Medium   |
| **6. Urgent wording**        | “Unusual sign.in activity”, “Click here”                  | ⚠️ Social engineering   | 🟠 Medium   |
| **7. Grammar & spelling**    | Noticeable typos and inconsistencies                      | ⚠️ Common in phishing   | 🟡 Low      |
| **8. Final assessment**      | Multiple high-risk indicators                             | ❌ Confirmed phishing    | 🔴 Critical |

📊 Key Findings

Email originated from a non-Microsoft mail server (Germany)

SPF, DKIM, DMARC — all failed or missing

Contained a phishing link redirect and urgency-based language

Designed to harvest Microsoft account credentials


🧠 Lessons Learned

Always verify sender domain authenticity.

Use header analyzers to confirm SPF/DKIM/DMARC.

Hover over links before clicking — check for domain mismatches.

Be skeptical of urgency or grammar errors in official emails.

Document and report confirmed phishing cases to your SOC or CERT team.

📁 Repository Structure

phishing-email-analysis/
│
├── sample-1034.eml             
# Raw phishing email sample

├── human_text.txt               
# Extracted readable text

├── analysis_summary.pdf          
# Final report (PDF)

├── phishing_report.docx          
# Word version

├── README.md                     
# Project documentation

└── screenshots/                  
# Supporting screenshots

⚠️ Disclaimer

This repository is for educational and ethical cybersecurity research only.
Do not use the techniques demonstrated here for malicious or unauthorized activity.
Always analyze phishing content in a safe, offline virtualbox or sandbox environment.
