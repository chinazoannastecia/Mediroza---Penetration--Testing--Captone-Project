# Mediroza-Penetration-Testing-Captone-Project
# **Project overview**
This repository documents a black-box penetration test of the Mediroza General Hospital web infrastructure at https://medirozahospital.com. The assessment was performed for the Networkwalks B083C Week 4 Capstone Project to identify weaknesses, demonstrate their impact through controlled exploitation, and recommend practical remediation.

Seven findings, ranging from Medium to Critical, were identified. The central issue was a SQL injection vulnerability in the patient portal login flow. In the authorized test environment, it enabled authentication bypass, access to confidential patient lab-report PDFs, discovery of sensitive PDF metadata, and retrieval of an exposed database backup containing staff salary and shareholder information.

# **Objectives**
Assess the web application from an external, unauthenticated perspective.
Identify weaknesses in authentication, input handling, file protection, and server configuration.
Demonstrate the real world impact of each finding in a controlled manner.
Document evidence and provide prioritized remediation recommendations.
# **Authorization and scope**
Testing was conducted with written authorization from the client as part of a controlled Networkwalks educational exercise.
| In scope | Exclude from scope |
| :--- | :--- |
| https://example.com | Social engineering |
| Public facing web application behavior | Denial of service testing |
| Patient portal and discovered paths within the agreed domain | Any testing outside the agreed domain |

#**Methodology**

The assessment followed a structured black box methodology:

#**Reconnaissance** - Passive information gathering using publicly available information and web-based tools.
#**Vulnerability identification** - Analysis of application behavior for authentication and input-handling weaknesses.
#**Controlled exploitation** - Demonstration of each issue's impact within the authorized environment.
#**Documentation** - Recording of findings, evidence, and remediation recommendations.
## **Tools Used**

| Tool | Purpose in the assessment |
| :--- | :--- |
| cURL | Sending HTTP requests and reviewing web-server responses |
| Browser Developer Tools | Inspecting page source and login-form behavior |
| Networkwalks Hash Calculator | Extracting PDF password hashes |
| Networkwalks Password Cracker | Testing PDF password hashes against wordlists |
| QPDF | Decrypting password-protected PDFs after password recovery |
| ExifTool | Reading hidden metadata from PDFs |
| Wget | Downloading files from the web server in the controlled test |
| ChatGPT | Converting raw SQL data into readable tables during analysis |

#**Executive summary**
The target's security posture was assessed as poor. A chain of individually preventable weaknesses enabled an unauthenticated attacker to progress from reconnaissance to patient-document access and, ultimately, access to a database backup exposed through a publicly listed directory.

The database extract contained sensitive information for 30 hospital employees and ownership information for 10 shareholders. To protect privacy, this README intentionally does not reproduce names, contact details, national ID numbers, salary figures, or ownership percentages from that extract.

Immediate remediation is recommended for all Critical and High findings.

## **Findings summary**

| ID | Finding | Location | Risk |
| :--- | :--- | :--- | :--- |
| F-01 | Username enumeration on login page | `patient/login.php` | 🟡 Medium |
| F-02 | SQL injection login bypass | `patient/login.php` | 🔴 Critical |
| F-03 | Encrypted PDFs accessible after login bypass | `patient/reports/` | 🟠 High |
| F-04 | Weak PDF passwords crackable with a wordlist | `patient_report_*.pdf` | 🟠 High |
| F-05 | Sensitive metadata left in patient PDF files | `patient_report_3.pdf` | 🟡 Medium |
| F-06 | Forgotten backup folder with directory listing enabled | `old/` | 🔴 Critical |
| F-07 | Confidential staff salaries and shareholder data in plain text | `old/mediroza_db_backup_2019.sql` | 🔴 Critical |
## **Detailed findings**

### F-01 - Username enumeration on login page
**Risk:** 🟡 Medium  
**Location:** `patient/login.php`
**Evidence:** Application returned "Username not found" for non-existent users, confirming valid usernames can be enumerated.

Evidence placeholder:
### F-01 — [Put your title here, e.g., SQL Injection]

**Evidence:**
![F-01 Evidence](./F-01.png)



