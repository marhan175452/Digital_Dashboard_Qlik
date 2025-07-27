# *This project is a demonstration built using anonymized and obfuscated screenshots based on work I did professionally. All data, visuals, and text shown are non-confidential and intended for illustrative purposes only. Branding and internal identifiers have been removed or masked.*


# 🧠 Self Serve Digital Dashboard
This repository contains the complete **load script**, logic, and coding structure used to develop the **Self Serve Digital Dashboard (SSDD)** for M&S Bank. The dashboard is built in Qlik Sense and designed to provide data-driven visibility across customer digital behavior, product holding, and contact preferences.

## 🎯 Objective

To empower analysts and stakeholders with self-serve access to:

- Digital channel login behavior (MIB, PIB, 3DS)
- Product uptake (Credit Card, ESA, Loans)
- Customer segmentation (NTB vs ETB, tenure, demographics)
- Contact & marketing readiness (email, mobile, phoneable)
- Device profiling and campaign tracking

---

## 💡 Highlights

| Module             | What It Tracks                                                      |
|-------------------|----------------------------------------------------------------------|
| **Digital Activity**     | MIB & PIB logins, 3DS usage, OS breakdown (Android/iOS)         |
| **Product Details**      | Product counts, offers, delivery method, NTB/ETB                |
| **Contact & Marketing**  | Email/mobile availability, opt-in status (email, SMS, etc.)     |
| **Demographics**         | Customer age, gender, and tenure banding                        |
| **Digital Ladder**       | Engagement category over time (via CSV batch imports)           |
| **IVR**                  | Last 3 months’ IVR actions matched to customer base             |

---

## 🗃️ Repository Structure

qliksense-ssdd-dashboard/
├── qlik/
│ └── main_load_script.qvs # Full Qlik script
├── config/
│ └── metadata.md # Details on data sources & filters
├── README.md

## 🔧 Data Sources

**Primary Connection:** `LIB CONNECT TO 'WPB_MS_Oracle (DQM)'`  
**Supplemental:** Flat file connections (`.csv`) via Qlik Folder (for IVR, Digital Ladder)  
**Temporarily Disabled:** Teradata integration (due to infrastructure issue)

---

## ⚙️ Key Tables Queried

- `DM_CREDIT_CARD`
- `DM_EVERYDAY_SAVER`
- `DM_LOAN`
- `DM_CUSTOMER`
- `DM_APPLICATION`
- `DM_ECOMMERCE_MIA`
- `DM_MOBILE_BANK_SERVICING`
- `DM_MIB_LOGON`
- `DM_CDU_NUMBER_LOOKUP`
- and more…

---

## 🧾 Load Script Breakdown

- All script logic is consolidated into `main_load_script.qvs`
- Time segmentation used: **30 Days**, **90 Days**, **12 Months**
- Keys created for merging KPI facts with master product list
- Inline transformations using `IF()`, `CASE`, `JOIN`, `RESIDENT`, and more
