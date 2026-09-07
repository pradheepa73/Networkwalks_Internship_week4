# 🏥 Mediroza General Hospital – Penetration Test

<p align="center">
  <img src="https://img.shields.io/badge/Status-Completed-brightgreen?style=for-the-badge" alt="Status">
  <img src="https://img.shields.io/badge/Type-Black--Box%20Pentest-red?style=for-the-badge" alt="Type">
  <img src="https://img.shields.io/badge/Target-Healthcare%20Simulation-blue?style=for-the-badge" alt="Target">
  <img src="https://img.shields.io/badge/Networkwalks-B082%20%7C%20Week%204-orange?style=for-the-badge" alt="Batch">
</p>

## Networkwalks Internship – Week 4 Project

**Candidate:** Pradheepa.M  
**Internship Batch:** AUG26 Batch B082  
**Date:** September 2026  
**Environment:** Kali Linux 2026.2 (VirtualBox) / Windows 11 Host

---

## 📋 Executive Summary
A comprehensive **3-day black-box penetration test** was conducted against the simulated healthcare infrastructure of **Mediroza General Hospital**. The engagement successfully emulated a real-world adversary, compromising the application via a **SQL Injection** chain, bypassing authentication, and exfiltrating sensitive medical and financial data.

The assessment resulted in the extraction of **3 confidential patient pathology reports**, **30 employee payroll records**, and **10 shareholder agreements**. 

**Overall Risk Posture:** 🔴 **CRITICAL**

---

## 🧬 Attack Chain & Methodology

The testing followed a structured offensive security methodology to demonstrate the full impact of the discovered vulnerabilities.

```mermaid
graph TD
    A[🔍 Reconnaissance] --> B[💉 SQL Injection Bypass]
    B --> C[🏥 Patient Portal Access]
    C --> D[📄 3 Encrypted PDFs]
    D --> E[🔓 PDF Cracking]
    E --> F[📋 Metadata Analysis]
    F --> G[📁 /old/ Directory Found]
    G --> H[💾 SQL Backup Dump]
    H --> I[💰 Salaries & Shareholders]
    I --> J[📊 Professional Report]

    style A fill:#f9f9f9,stroke:#333,stroke-width:2px
    style B fill:#ff6b6b,stroke:#c0392b,stroke-width:2px,color:#fff
    style C fill:#feca57,stroke:#f39c12,stroke-width:2px
    style D fill:#48dbfb,stroke:#0984e3,stroke-width:2px
    style E fill:#ff9ff3,stroke:#e84393,stroke-width:2px
    style F fill:#54a0ff,stroke:#2e86de,stroke-width:2px
    style G fill:#5f27cd,stroke:#341f97,stroke-width:2px,color:#fff
    style H fill:#ff6348,stroke:#c0392b,stroke-width:2px,color:#fff
    style I fill:#f0932b,stroke:#e67e22,stroke-width:2px
    style J fill:#6ab04c,stroke:#2ecc71,stroke-width:2px
```
---

## 🔥 Key Findings & Data Exposure

| Identifier | Vulnerability | Severity | Exploit Result |
| :--- | :--- | :--- | :--- |
| **F-001** | **SQL Injection** (Boolean-Based) | 🔴 **Critical** | Admin login bypass using `admin' -- ` |
| **F-002** | **Weak Cryptographic Storage** (PDF) | 🟠 **High** | Decrypted 3 patient files with `rockyou.txt` |
| **F-003** | **Directory Listing & Data Leak** | 🔴 **Critical** | Exposed `mediroza_db_backup_2019.sql` |

### 📂 Exposed Data Breakdown

**1. Patient Medical Records**
- **Sipho Dlamini** (MG-P-10231) - Abnormal White Cell Count.
- **Priya Reddy** (MG-P-10244) - High Cholesterol & Triglycerides.
- **Emily Thompson** (MG-P-10258) - Iron Deficiency (Low Ferritin & Vitamin D).

**2. Hospital Payroll (30 Employees)**
> *The `staff` table exposed monthly salaries in ZAR. The highest salary was R160,000 (Medical Director), and the lowest was R19,000 (Receptionist).*

**3. Shareholder Structure**
> *Dr. Rajesh Naidoo holds a 18.0% majority stake, while Dr. Vikram Chetty holds a 4.0% Preferential share class.*

---

## 🛠️ Arsenal (Tools Used)

| Tool | Purpose | Status |
| :--- | :--- | :--- |
| **Gobuster** | Directory Enumeration & Fuzzing | ✅ |
| **Burp Suite** | Request Interception & Repeater | ✅ |
| **Manual SQLi** | Authentication Bypass (`admin' -- `) | ✅ |
| **pdfcrack** | Password Recovery (Rockyou.txt) | ✅ |
| **exiftool** | Metadata Extraction & Analysis | ✅ |
| **wget / grep** | Remote File Retrieval & Parsing | ✅ |
| **PowerShell** | Evidence Organization & Renaming | ✅ |

---

## 📁 Repository Structure

This repository is meticulously organized to mirror the 4 Milestones of the engagement.

```
Networkwalks_Internship_week4/
├── 📁 M1_Discovery/                 # Milestone 1: Reconnaissance & Breach
│   └── 📁 Screenshots/
│       ├── 01_Terminal_Setup.png
│       ├── 02_SQL_Injection_Payload.png
│       └── 11_Authenticated_Portal.png
├── 📁 M2_Cracking/                  # Milestone 2: Decryption
│   └── 📁 Screenshots/
│       ├── 12_Emily_Thompson_Report.png
│       ├── 18_PDFCrack_Recovering.png
│       └── ...
├── 📁 M3_Server_Access/             # Milestone 3: Lateral Movement & Exfil
│   └── 📁 Screenshots/
│       ├── 20_Old_Directory_Listing.png
│       ├── 23_SQL_Staff_Table.png
│       └── 24_SQL_Shareholders.png
├── 📄 Mediroza_Penetration_Test_Report_Pradheepa_M.pdf   # Final Deliverable
├── 📄 backup.sql                                            # Exposed Database Dump
└── 📄 README.md                                             # You are here!
```

---

## 📷 Visual Evidence Highlights

A total of **24 high-quality screenshots** are included in the `M1`, `M2`, and `M3` folders, documenting every successful step.

*Example: SQL Injection Bypass showing `admin' -- ` in the username field.*
<img width="1920" height="1040" alt="01_Terminal_Setup_Workspace" src="https://github.com/user-attachments/assets/54ec869b-07ac-4ad7-9135-1aac81535c4e" />

<img width="1920" height="1040" alt="02_SQL_Injection_Payload" src="https://github.com/user-attachments/assets/b1131309-5705-4274-a50c-2777d02be712" />

<img width="1920" height="1040" alt="03_Patient_Portal_Dashboard" src="https://github.com/user-attachments/assets/94955cea-13c2-4802-a422-78c66da0ca51" />

<img width="1920" height="1040" alt="04_Staff_Login_Page_URL" src="https://github.com/user-attachments/assets/8742771f-262d-457f-a0bf-99b95fafcc55" />

<img width="1920" height="1040" alt="05_Failed_Login_Attempt" src="https://github.com/user-attachments/assets/0ca44574-371c-4977-960b-2fb63fde3ff8" />

<img width="1920" height="1040" alt="06_Login_Error_Message" src="https://github.com/user-attachments/assets/010f8a07-1713-4f52-95e1-1caf9814887d" />

<img width="1920" height="1040" alt="07_Tool_Version_Checks" src="https://github.com/user-attachments/assets/b7b3855f-a682-40a5-90b9-c9a25f234982" />

<img width="1920" height="1040" alt="08_Homepage_View_Source_Recon" src="https://github.com/user-attachments/assets/5707a9db-3c4c-4132-98bc-c47c6120b7de" />

<img width="1920" height="1040" alt="09_Staff_Login_Browser_View" src="https://github.com/user-attachments/assets/bf95f70c-ab11-401f-b949-934f0be84986" />

<img width="1920" height="1040" alt="10_Salaries_Shareholders_CSV_Verify" src="https://github.com/user-attachments/assets/aeac846d-bf8a-46cc-8d48-ac0a74606a84" />

<img width="1920" height="1040" alt="11_Authenticated_Portal_3_PDFs" src="https://github.com/user-attachments/assets/a96dd96e-400f-4a4b-94fe-a6ba9bc9c24c" />

<img width="1919" height="1087" alt="12_Emily_Thompson_Report_Decrypted" src="https://github.com/user-attachments/assets/18b60420-a855-4121-a6d2-1b7da763b14b" />

<img width="1911" height="1094" alt="13_Priya_Reddy_Report_Decrypted" src="https://github.com/user-attachments/assets/fb2c0247-d429-4e6c-93d8-eba9d5499697" />

<img width="1920" height="1140" alt="14_Sipho_Dlamini_Report_Decrypted" src="https://github.com/user-attachments/assets/bd52ab48-7884-46bc-825b-18124957a7d6" />

<img width="1920" height="1040" alt="15_Login_Form_View_Source_Analysis" src="https://github.com/user-attachments/assets/5c9f0f3d-d570-4094-b7d1-2a4560b2a462" />

<img width="1920" height="1040" alt="16_Rockyou_Wordlist_Preparation" src="https://github.com/user-attachments/assets/8b9fb063-0423-4361-8e65-5520d29a2733" />

<img width="1920" height="1040" alt="17_PDFCrack_Installation_Handling" src="https://github.com/user-attachments/assets/6b897e74-d4bf-46b6-8c48-5fc3eca48e18" />

<img width="1920" height="1040" alt="18_PDFCrack_Recovering_Weak_Passwords" src="https://github.com/user-attachments/assets/251c1d98-c9e8-4d96-9258-4916c0e497ab" />

<img width="1920" height="1040" alt="19_Exiftool_Standard_V2 3_Encryption" src="https://github.com/user-attachments/assets/868d4b7a-cc83-4909-8750-8d89fa021463" />

<img width="1920" height="1040" alt="20_Old_Directory_Listing_SQL_Backup" src="https://github.com/user-attachments/assets/ed85d725-0f20-4254-b810-cc96191caacc" />

<img width="1920" height="1040" alt="21_Exiftool_Output_All_3_PDFs" src="https://github.com/user-attachments/assets/2fb605d8-5349-4c62-9c09-fae6b9eb8377" />

<img width="1920" height="1040" alt="22_Wget_SQL_Backup_Grep_Start" src="https://github.com/user-attachments/assets/66bc85e7-b89e-4ea3-a761-70c4b3687106" />

<img width="1920" height="1040" alt="23_SQL_Staff_Table_Names_Salaries" src="https://github.com/user-attachments/assets/a2a2004b-4640-4d75-8da1-55e8aa4c597d" />

<img width="1920" height="1040" alt="24_SQL_Shareholders_Table_Ownership" src="https://github.com/user-attachments/assets/7833be07-3dc0-4669-94d4-9c5eb0523917" />

---

## 📄 Full Penetration Test Report

The complete, comprehensive report is available below:

📄 **[Mediroza_Penetration_Test_Report_Pradheepa_M.pdf](./Mediroza_Penetration_Test_Report_Pradheepa_M.pdf)**

> *This report contains detailed findings, exploitation steps, remediation recommendations, and a full breakdown of all discovered vulnerabilities.*

---

## ⚠️ Ethical & Legal Disclaimer

> **IMPORTANT**
> This project was conducted **strictly for educational purposes** as part of the **Networkwalks Internship Program (Batch B082 | Week 4)**. 
> The target environment (`https://medirozahospital.com`) is a **simulated training lab** designed explicitly for cybersecurity education. **Written authorization** was granted by the training provider prior to testing.
> 
> The techniques and code demonstrated in this repository must **never** be applied to any system, network, or application without obtaining **explicit, written permission** from the rightful owner. Unauthorized access is illegal and unethical.

---

## 👨‍💻 Author

**Pradheepa M**  
🔹 Networkwalks Intern – Batch B082  
🔹 [GitHub Profile](https://github.com/pradheepa73)  
🔹 [LinkedIn](https://www.linkedin.com/in/pradheepa-m-051728372)

*Feel free to connect or reach out for collaborations on offensive security research!*

---

## ⭐ Project Status

| Milestone | Objective | Status |
| :--- | :--- | :--- |
| M1 | Breach & Retrieve 3 PDFs | ✅ Complete |
| M2 | Crack Encryption & Extract Text | ✅ Complete |
| M3 | Find Salaries & Shareholders | ✅ Complete |
| M4 | Compile Professional Report | ✅ Complete |
| Final | Portfolio & GitHub Documentation | ✅ Complete |

---

<p align="center">
  <b>© 2026 Networkwalks Internship Program. All rights reserved.</b>
</p>
```

---
