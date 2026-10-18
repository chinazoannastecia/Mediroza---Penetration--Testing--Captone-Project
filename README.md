# Mediroza-Penetration-Testing-Captone-Project
Project overview
This repository documents a black-box penetration test of the Mediroza General Hospital web infrastructure at https://medirozahospital.com. The assessment was performed for the Networkwalks B082 Week 4 Capstone Project to identify weaknesses, demonstrate their impact through controlled exploitation, and recommend practical remediation.

Seven findings, ranging from Medium to Critical, were identified. The central issue was a SQL injection vulnerability in the patient portal login flow. In the authorized test environment, it enabled authentication bypass, access to confidential patient lab-report PDFs, discovery of sensitive PDF metadata, and retrieval of an exposed database backup containing staff salary and shareholder information.

Objectives
Assess the web application from an external, unauthenticated perspective.
Identify weaknesses in authentication, input handling, file protection, and server configuration.
Demonstrate the real world impact of each finding in a controlled manner.
Document evidence and provide prioritized remediation recommendations.
Authorization and scope
Testing was conducted with written authorization from the client as part of a controlled Networkwalks educational exercise.
| In scope | Exclude from scope |
| :--- | :--- |
| https://example.com | Social engineering |
| Public facing web application behavior | Denial of service testing |
| Patient portal and discovered paths within the agreed domain | Any testing outside the agreed domain |
