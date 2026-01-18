---
layout: default
title: Clinical validation
---

<blockquote>
🏠 <a href="/">Back to homepage</a>
</blockquote>

This page provides public evidence artifacts for **ePokratis MedAiConnect (iOS)** validation work: the full validation report and a reproducibility package (scripts + supporting materials).

<div style="margin-top: 1.0rem; text-align:center;">
  <a href="/assets/pdfs/epokratis-medaiconnect-validation-report.pdf"
     target="_blank" rel="noopener noreferrer"
     onclick="gtag('event','evidence_download',{'artifact_type':'validation_pdf','file_name':'epokratis-medaiconnect-validation-report.pdf','source':'clinical_validation_page'});"
     style="display:inline-block; padding:10px 18px; margin:6px;
            background:#1f7a6d; color:#fff; text-decoration:none;
            border-radius:6px; font-weight:600;">
    Download Validation Report (PDF)
  </a>

  <a href="/assets/downloads/validation_package.zip"
     target="_blank" rel="noopener noreferrer"
     onclick="gtag('event','evidence_download',{'artifact_type':'validation_zip','file_name':'validation_package.zip','source':'clinical_validation_page'});"
     style="display:inline-block; padding:10px 18px; margin:6px;
            background:#2c5aa0; color:#fff; text-decoration:none;
            border-radius:6px; font-weight:600;">
    Download Reproducibility Package (ZIP)
  </a>
</div>

<p style="max-width:820px; margin:14px auto 0; font-size:0.95rem; color:#666;">
  Note: This material is provided for evidence and transparency. It does not provide diagnosis or medical advice and is intended as an adjunct to standard clinical practice.
</p>

---

## Study at a glance

- **Title:** Validation Study of ePokratis MedAiConnect Application and Bluetooth Medical Devices for Accurate and Reliable Vital Signs Measurement  
- **Site:** Athens Hospital (Athens, Greece)  
- **Study period:** **06 Feb 2025 – 06 Mar 2025**  
- **Participants:** **27 adults (age 20–91)**  
- **Objective:** Evaluate **accuracy, reliability, and data integrity** of measurements obtained via the iOS app with integrated Bluetooth medical devices, and support documentation expectations for **Apple App Store Review Guideline 1.4.1 (Safety – Physical Harm)**.  
- **Collaboration:** Conducted under a signed collaboration memorandum (memorandum of cooperation) between **Telematic Medical Applications Ltd.** and **Athens Hospital**.

---

## Devices evaluated

Six Bluetooth-enabled medical devices integrated with the iOS application:

- **TaiDoc TD-3128** — Blood Pressure Monitor  
- **TaiDoc TD-8255** — Fingertip Pulse Oximeter  
- **TaiDoc TD-1241** — Non-contact Forehead Thermometer  
- **TaiDoc TD-2555** — Digital Weight Scale  
- **Contec PM10** — Portable ECG Monitor  
- **TaiDoc TD-4216B** — Multi-functional Monitoring System (biomarkers)

---

## Reference standards (Athens Hospital)

Device measurements were evaluated against certified hospital-grade reference standards:

- **Blood Pressure:** Omron HEM-907XL Automatic Blood Pressure Monitor (ISO 81060-2:2018; CE-marked; FDA 510(k): K021800)  
- **Pulse oximetry:** Nellcor bedside SpO₂ monitoring system (ISO 80601-2-61:2017; CE-marked; FDA 510(k): K142865)  
- **Temperature:** Welch Allyn Braun ThermoScan PRO 6000 ear thermometer (ASTM E1965-98; EN ISO 80601-2-56:2017; CE-marked; FDA 510(k): K152298)  
- **Weight:** Seca 769 digital column medical scale (OIML R76-1 Class III; EN 45501; CE-marked)  
- **ECG / Heart rate:** Philips PageWriter TC20 ECG system (IEC 60601-2-25; IEC 60601-2-27; CE-marked; FDA 510(k): K133409)  
- **Biomarkers:** Laboratory blood tests using Roche Cobas c 111 Analyzer (CE-marked; FDA 510(k): K071211; ISO 15197:2013 (glucose) noted in report)
All reference devices are certified, regularly calibrated, and operated by trained healthcare professionals.

---

## Study protocol (data collection)

- For **five vital-sign devices** (BP, SpO₂/PR, temperature, weight, ECG/HR):  
  - Each device reading was paired with a **hospital-grade reference measurement**.  
  - Each device measurement was **repeated three times per participant** to assess repeatability and reliability.

- For **TD-4216B (multi-biomarker)**:  
  - **23/27 participants** provided blood samples for biomarker comparison (glucose, β-ketone, total cholesterol, uric acid, lactate).  
  - Device measurements were **repeated three times per biomarker**; due to the invasive nature of sampling, a **single clinical reference** per biomarker per participant was used.

- Execution and oversight:  
  - Telematic Medical Applications’ trained collaborators operated the devices per manufacturer protocols and supported installation/operation.  
  - Athens Hospital clinical personnel performed reference measurements, supervised procedures, and **cross-verified that app-displayed values reflected the device outputs**.

---

## Statistical methodology (reproducible)

The report applies established statistical techniques to evaluate reliability and agreement:

- **Reliability:** **Intraclass Correlation Coefficient (ICC)** using Pingouin (Python; v0.5.5), focusing on **ICC3** (single fixed rater) and **ICC3k** (average of three repeated measurements).  
- **Precision & agreement across repeats:** **Mean Absolute Difference (MAD)** and **Agreement Percentage** using predefined clinical tolerance thresholds.  
- **Method agreement:** **Bland–Altman** analysis (mean difference/bias and **95% limits of agreement**, ±1.96 SD) comparing device vs reference.

---

## Key results (summary)

**Reliability (ICC):** All devices showed **excellent** reliability under supervised conditions.  
- Vital-sign devices achieved **ICC3 ≈ 0.975–0.9999** and **ICC3k ≈ 0.992–0.99997** (e.g., BP/PR, thermometer, weight, ECG).  
- TD-4216B biomarkers ranged **very good to excellent** (**ICC3: 0.889–0.997**, **ICC3k: 0.960–0.999**).

**Accuracy & agreement (Bland–Altman / MAD / Agreement %):** Mean bias was small and agreement was strong across measures. Examples from the study summary table:  
- **Blood pressure (TD-3128):** bias **+0.22 / +0.38 mmHg**, MAD **2.57 / 2.35 mmHg**, agreement **92.59% / 88.89%** (systolic/diastolic).  
- **SpO₂ (TD-8255):** bias **+0.19%**, MAD **1.31%**, agreement **96.30%**.  
- **Temperature (TD-1241):** bias **−0.02°C**, MAD **0.13°C**, agreement **92.59%**.  
- **Weight (TD-2555):** bias **+0.02 kg**, MAD **0.13 kg**, agreement **96.30%**.  
- **ECG heart rate (PM10):** bias **−0.54 bpm**, MAD **0.54 bpm**, agreement **92.59%**.  
- **TD-4216B biomarkers:** Glucose and β-ketone reached **100% agreement** (Glucose MAD **4.78 mg/dL**, β-ketone MAD **0.03 mmol/L**).

(See Tables 17–19 in the report for the full summary and applicable standards/thresholds.)

---

## Data transmission integrity and governance

- **Bluetooth workflow:** device readings were transmitted to the iOS app and immediately displayed.  
- A Telematic Medical Applications staff member recorded app-displayed values into a structured Excel sheet in real time, in the presence of clinical staff; the daily sheet was shared with Athens Hospital for cross-verification and archival.  
- **Validation outcome:** all six devices successfully transmitted data to the app with **no missing values, no corruption, and 100% match** between device display readings and in-app values; timestamps/units/labels were consistently stored.

### GDPR-aligned handling (as described in the report)
- Participants provided **informed consent**.  
- Analysis datasets were **pseudonymized (GDPR Art. 4(5))**; linking keys were retained only by Athens Hospital and not shared with the company.  
- Data processing remained within the EU.

---

## What’s included

- **Validation Report (PDF):** study context, protocol, statistical methodology, device-by-device results, and integrity/governance documentation.
- **Reproducibility Package (ZIP):**
  - `scripts/` — Python scripts used for analysis and plots
  - `data/` — supporting analysis files and result tables

These artifacts are shared to support evidence-driven delivery and review readiness.

---

## How to use the reproducibility package

1. Download and unzip the package.
2. Review the included folder structure (`scripts/`, `data/`).
3. Run scripts from the `scripts/` folder using Python 3 (requirements depend on the script).

If you have questions or would like a walkthrough, I’m happy to help.

---

## Contact

If you'd like a walkthrough or additional context, feel free to [get in touch](/contact).
