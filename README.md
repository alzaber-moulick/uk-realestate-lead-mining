# UK Real Estate Lead Mining & Data Validation Pipeline

An automated data engineering and validation pipeline designed to source, clean, and verify high-intent UK Real Estate decision-maker leads for targeted B2B lead generation campaigns.

---

## 📌 Project Overview

This repository demonstrates an end-to-end data pipeline that extracts UK agency information, cleans structured fields (names, postcodes, phone numbers), and validates contact emails using a hybrid workflow of **Python (Pandas)** and **Apollo.io**.

* **Target Niche:** UK Real Estate Agencies & Property Management Companies
* **Target Titles:** Directors, Managing Directors, Heads of Sales, Owners
* **Geographic Focus:** United Kingdom (London & major metropolitan regions)

---


## 🛠️ Technical Workflow & Architecture

[ Raw Sourced Leads / CSV ]
│
▼
[ Python Data Sanitation (Pandas) ] ──► Standardize UK Postcodes & Phone Formats
│
▼
[ Apollo.io Data Enrichment ]     ──► Match Domain Emails & LinkedIn Profiles
│
▼
[ Email & Domain Validation ]     ──► Zero-Bounce & SMTP Inbox Verification
│
▼
[ Clean Deliverable Output ]     ──► Google Sheets / Client Ready CSV


### 1. Python Data Cleaning & Sanitation (`main.py`)
Using custom Python scripts leveraging the `pandas` library, the raw dataset undergoes:
* **UK Postcode Formatting:** Standardizing postcodes to valid UK alphanumeric formats (e.g., `SW3 2HJ`, `W1U 8AN`).
* **Phone Number Normalization:** Converting raw strings into standard UK international landline formats (`+44 20 ...`).
* **Deduplication:** Removing duplicate company domains and overlapping contact records.

### 2. Apollo.io Sourcing & Validation
The cleaned company entities and domain structures are mapped into **Apollo.io** to:
* Extract verified corporate email addresses linked to specific domain hosts.
* Cross-reference decision-maker titles (Managing Directors / Heads of Sales).
* Filter and discard inactive or catch-all email domains to guarantee high deliverability.

---

## 📁 Repository Structure

.
├── UK_Real_Estate_Leads_20_Cleaned.csv   # Processed sample dataset (20 verified agencies)
├── main.py                               # Python script for data cleaning & validation logic
└── README.md                             # Project documentation


---

## 📊 Sample Output Schema

<img width="1431" height="848" alt="Screenshot 2026-09-15 at 1 03 15 AM" src="https://github.com/user-attachments/assets/989f72c2-e594-424a-b528-16c9566526a4" />

The final output is delivered in a structured schema optimized for immediate CRM ingestion:

| Field Name | Description | Example |
| :--- | :--- | :--- |
| **Full Name** | Target Decision-maker | Alexander Hughes |
| **Company** | Registered UK Real Estate Agency | Foxtons Estate Agents |
| **Job Title** | Verified Corporate Title | Head of Sales |
| **Email** | Validated Business Email | london@foxtons.co.uk |
| **Phone** | Standardized Landline | +44 20 7893 6000 |
| **City/Region** | Primary Operating Location | London |
| **Postal Code** | Formatted UK Postcode | SW3 2HJ |
| **Property Focus** | Primary Business Niche | Residential Sales & Lettings |
| **Website** | Active Official Domain | https://www.foxtons.co.uk |

---

## 🚀 How to Run the Python Data Cleaner

1. **Clone the repository:**
   ```bash
   git clone [https://github.com/YOUR_GITHUB_USERNAME/uk-realestate-lead-mining.git](https://github.com/YOUR_GITHUB_USERNAME/uk-realestate-lead-mining.git)
   cd uk-realestate-lead-mining
