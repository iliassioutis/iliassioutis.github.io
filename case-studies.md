---
layout: default
title: Case studies
---

<blockquote>
🏠 <a href="/">Back to homepage</a>
</blockquote>

Below are selected delivery case studies highlighting evidence-driven execution, regulated platforms, and technical leadership.

---

## Featured case studies

### 🧪 Clinical validation — ePokratis MedAiConnect (iOS)
One-month clinical validation study at **Athens Hospital** (**Feb 6–Mar 6, 2025**) with **27 adults (20–91)** evaluating **accuracy, reliability, and data integrity** for **six Bluetooth medical devices** integrated with the ePokratis MedAiConnect **iOS** app, supporting App Store safety evidence under **Guideline 1.4.1 (Safety – Physical Harm)**. Athens Hospital clinical staff supervised measurements and **cross-verified that app-displayed values matched the device outputs**.

- **Devices validated:** TaiDoc TD-3128 (BP/PR), TD-8255 (SpO₂/PR), TD-1241 (Thermometer), TD-2555 (Scale), Contec PM10 (ECG/HR), TaiDoc TD-4216B (biomarkers).
- **Protocol:** paired comparison vs **hospital-grade reference standards**; **3× repeats per participant** for vital-sign devices; TD-4216B subset: **23/27** blood samples, **3× repeats per biomarker** with **single clinical reference per biomarker** (invasive sampling constraint).
- **Reference standards (Athens Hospital):** Omron HEM-907XL (BP), Nellcor bedside SpO₂ system, Welch Allyn Braun ThermoScan PRO 6000 (temperature), Seca 769 medical scale (weight), Philips PageWriter TC20 ECG system, Roche Cobas c 111 lab analyzer (biomarkers) — all certified and clinically operated.
- **Methods:** **ICC** (Pingouin; **ICC3 / ICC3k**), **MAD**, **Agreement %**, and **Bland–Altman** (mean difference and **95% limits of agreement: LOA = MD ± 1.96×SD**) with clinically/standard-derived thresholds (e.g., ISO 81060-2 for BP, ISO 15197 for glucose).
- **Key outcomes (study summary tables):** vital-sign devices showed **excellent reliability** (ICC3 **0.975–0.9999**; ICC3k **0.992–0.99997**); TD-4216B biomarkers ranged **very good to excellent** (ICC3 **0.889–0.997**, ICC3k **0.960–0.999**). Regulatory/clinical thresholds were defined per measure and summarized as ‘Met in study: Yes’ in the report’s compliance table.
- **Data integrity:** end-to-end workflow verified; **no missing values, no corruption, consistent units/labels/timestamps**, and **100% in-app match** to device readings across all devices (no integrity issues observed).
- ✅ Artifacts: [Evidence & downloads](/clinical-validation) · [Report (PDF)](/assets/pdfs/epokratis-medaiconnect-validation-report.pdf) · [Repro pack (ZIP)](/assets/downloads/validation_package.zip)

---

### 🧠 UCL MPhil thesis — 3D non-rigid registration for image-guided interventions
Benchmarking and implementation of non-rigid registration algorithms for prostate surface alignment under occlusions/noise/outliers.

- 🔎 Page coming soon

---

### 📊 DHL Management (MBA Internship) — Customer profitability reporting & automated validation at scale (confidential)

MBA internship / research project (Cass Business School, City University London; **submitted 21 Sep 2009**) supporting the improvement and rollout of a **global customer profitability reporting** capability for a strategic account organization serving DHL’s **top global customers** across multiple industries and regions. The core problem was operational and very tangible:

- Month-end profitability reporting required **validating large, multi-source datasets** across many stakeholders.
- Validation consumed significant time and often triggered long email/meeting escalations (“where did the error occur, who owns it, and how do we correct it?”).
- Manual validation increased the probability of **human error**, while the organization needed **faster, more reliable reporting** to strengthen decision-making and customer portfolio management.

This work combined **process analysis + governance mapping + statistical validation automation** (Excel/VBA) to reduce manual effort and improve consistency, while aligning reporting to how profitability is truly defined across different DHL business units.

---

## Business context

The organization (a strategic customer relationship and customer service function) was created to manage a portfolio of **high-revenue global customers** across industries (e.g., automotive, manufacturing, life sciences/healthcare, technology, consumer products). Its purpose was to deliver measurable business value via:

- Global account management and cross-divisional coordination
- Tailored logistics and supply chain solutions (multi-product, multi-country)
- Consistent global service delivery and scalable, repeatable solutions

A key enabler of that strategy was **customer profitability reporting**—a “single view of the customer” that supports senior management decisions such as:

- Where to invest / where to redesign service delivery
- Which accounts are drifting toward unprofitability
- How to shape incentives and KPIs toward profitable growth

---

## Why this problem is hard (and why “profitability” isn’t a single number)

A central insight from the research is that customer profitability is **not homogeneous** across the business:

- Different business units (BUs) follow different **business rules, cost models, and operational practices**.
- Customer behavior can vary significantly by product, even within the same customer.
- Profitability reporting based purely on traditional accounting often fails to reflect **commercial reality**, especially when overheads are large and allocation rules differ.
- As a result, **Gross Profit (GP)** can be defined differently across BUs—and **GP cannot be simply summed across BUs** when fixed-cost allocation approaches differ.

This directly impacts validation: you cannot validate profitability reliably unless you understand the underlying definition and the data lineage behind it.

---

## Operating model: regional + global governance, multi-source inputs

Profitability reporting was produced at **account level** and then consolidated by customer / product / BU / region / country / industry.

Data sources varied by BU and geography; the governance model typically looked like:

- **BU-owned source systems** capture operational and financial data (revenue, cost, volume, A/R).
- Regional finance teams extract data (or receive structured Excel extracts) and execute validation routines.
- A global team consolidates validated data for senior management reporting and dashboards.

Two operational variants existed in practice:

- **Excel-file-based validation** (manual/semimanual reconciliation and checks)
- **Contributor-based validation** within an enterprise BI environment (data loaded into contributor areas/cubes, then consolidated and published to reporting layers)

---

## The validation lifecycle (end-to-end)

Validation was not a single step; it followed a repeatable lifecycle with multiple intervention points:

- **Step 1 — Data cleanup after load**
  - “Cleaning” raw extracts immediately after ingestion (basic structural/format issues, missing fields, obvious anomalies)

- **Step 2 — Coarse-grained validation (pre-close → final close)**
  - Focused on identifying and flagging outliers and inconsistencies early enough to be corrected before final close
  - Business analysts tracked down anomalies and collaborated with BU owners to resolve issues

- **Step 3 — Fine-grained validation (post final close)**
  - Deeper statistical review of results to detect conspicuous data points and investigate root causes
  - Identification of data “gaps” (e.g., missing cost information causing profitability gaps) and reconciliation issues

Common validation checks included:

- **Completeness checks** at key hierarchy levels (customer/country/BU/product combinations)
- **Cross-measure consistency checks** (relationships between revenue & volume, revenue & profitability, A/R & revenue)
- **Month-over-month variance checks** to flag abnormal movements
- **Reconciliation checks** comparing consolidated outputs vs BU-provided consolidated reports

---

## Contributor-based workflow (how monthly data moved through the system)

A contributor-based workflow supported controlled monthly loads, reconciliation, and consolidation across regions and business units:

- Analysts retrieved BU data extracts (often **Excel outputs**) from BU-owned source environments.
- Data was uploaded into a **contributor area** (organized by domain such as Revenue / Costs / A/R / Profitability & KPI).
- Uploads were repeated by **region** (e.g., Americas, EMEA, APAC) and by **BU/product**, to ensure full global coverage.
- Uploaded data was stored in analyst-controlled “allocated spaces” (logically separated per month and dataset), then promoted through a **current vs previous** month structure.
- Data then moved from BU-level contributor spaces into **regional consolidation structures**, and finally into **reporting structures** used for dashboards and senior management views.

Key operational aspects captured in the workflow:

- Data was managed across **Current vs Previous month** reporting layers (to support month-over-month checks and controlled roll-forward).
- Promotion of data from “current” to “previous” month could be triggered as part of the monthly cycle.
- Consolidation occurred after BU/product uploads were complete, enabling a single consolidated view per region.
- Final outputs fed dashboards for profitability, volume, A/R and revenue, and enabled drill-down analysis and outlier visualization.

---

## Analytics & automation delivered (Excel/VBA “validation engine”)

A major contribution of the work was implementing **statistical validation and reporting automation** in Excel using **VBA**, designed to reduce repetitive manual checks and support consistent flagging of anomalies.

### 1) Freight validation algorithm (13-month model)

A dedicated validation model examined a **13-month** time window where the **13th month** was the “validation month.”

Core idea: decide whether the newest reported value is consistent with historical behavior, using progressively stricter gates.

- Compute the percentage change in the **mean** when adding month 13:
  - `A = [(Mean(7–13) - Mean(7–12)) / Mean(7–12)] × 100`
  - If `|A| > 20%`, month 13 becomes a validation candidate (user-adjustable cut-off)

- Compute the percentage change in the **standard deviation** when adding month 13:
  - `B = [(Stdev(7–13) - Stdev(7–12)) / Stdev(7–12)] × 100`
  - If `B ≤ 0`, the new value reduces variability → likely consistent with trend behavior
  - If `B > 25%`, treat as an “out-of-the-ordinary” event → validate (user-adjustable)
  - If `0 < B ≤ 25%`, apply a softer rule: check whether the value lies within
    - `Mean(7–12) ± 2×Stdev(7–12)`

This staged design avoids flooding analysts with false positives while still catching extreme deviations.

Operational features documented in the tool:

- Requires **Enable Macros** + Excel **Analysis ToolPak / ToolPak-VBA**
- Handles up to **65,536 customers** (Excel row limit of the era)
- Generates:
  - Per-customer drill-down (analysis + forecasting)
  - Full validation report listing all flagged customers
  - “FinalReport” filtered to high-impact accounts using a revenue-per-business-day threshold
  - “Miscellaneous” exceptions for missing completeness patterns (e.g., missing current month but non-zero recent history)
- Included unweighted moving-average forecasting (e.g., **MA2/MA3**) and automated sorting by severity

### 2) Revenue decomposition + predictability (trend/seasonality/cycle)

A second VBA module performed customer-level analysis by decomposing revenue behavior into components:

- Linear trend estimation (slope/intercept)
- Seasonal adjustment (e.g., semester-style adjustments)
- Residual computation and visualization
- Automated chart generation for quick pattern recognition
- Moving-average forecasts and “actual vs predicted” comparisons

This supported analyst decisions such as:
- “Is this change real customer behavior, seasonality, or a likely reporting issue?”

### 3) Express validation model (19-month model, revenue + volume)

A more advanced model supported validation when revenue must be consistent with **volume drivers**:

- Separate input sheets for **Revenue, Weight, and Shipments**
- A **19-month** window (with month 19 as the validation month)
- Rule: revenue validation requires accompanying volume information and sufficient history (e.g., at least several complete months)
- Volume variables were validated first (using the freight-style logic where applicable), then used to predict revenue.

The model implemented:

- Simple regression (Revenue ~ Weight) and (Revenue ~ Shipments)
- Multiple regression (Revenue ~ Weight + Shipments)
- Automatic model selection logic based on fit and diagnostics
- Residual analysis and visual identification of outliers
- Durbin–Watson checks for autocorrelation and additional statistical tests via ToolPak routines
- Automated charts:
  - Revenue vs Weight scatter
  - Revenue vs Shipments scatter
  - Weight vs Shipments scatter
  - Month-by-month KPI-style ratios (e.g., revenue/weight, revenue/shipments)

Outputs included:

- A comprehensive report of validation issues (including incomplete-data scenarios)
- A “FinalReport” filtered to highest-impact customers using a higher threshold
- Automated sorting and exception handling to guide analyst attention efficiently

---

## How validation fed reporting (pre-close, consolidation, final close)

The documented flow also shows how analytics supported month-end governance:

- **Pre-close validation**
  - Yearly and monthly consistency checks
  - Current vs previous month matching at customer/country/BU/product level
  - Discrepancy flagging for BU analyst follow-up

- **Pre-close consolidation**
  - Compare consolidated profitability outputs in the BI environment against consolidated versions prepared by BUs
  - Resolve discrepancies before final reporting

- **Final-close validation**
  - Identify “gaps” and missing/invalid data patterns
  - Ensure consolidated KPIs and dashboards were consistent and interpretable

The end state was senior-management-ready dashboards and matrices covering:
- Profitability (including gross margin ratio views and outlier visualization)
- Volume metrics and productivity-style ratios
- Accounts receivable health (e.g., aging-based metrics)
- Revenue views and consolidated reporting outputs

---

## Outcomes and practical value

Even when published artifacts must remain confidential, the value delivered is clear and can be stated safely:

- Reduced reliance on ad-hoc manual checks by providing **repeatable statistical validation routines**
- Standardized outlier detection across customers and regions
- Improved ability to separate true business changes (seasonality / customer behavior) from data issues (incomplete loads, inconsistent metrics, anomalous values)
- Strengthened month-end governance by making validation more transparent, auditable, and explainable
- Produced a concrete foundation for scaling toward more process-/activity-based cost thinking, where appropriate, to reduce profitability “data gaps”

---

## What this demonstrates (skills you can credibly claim)

- End-to-end understanding of a complex multi-region reporting pipeline (data lineage + governance + controls)
- Strong validation mindset: completeness, reconciliation, consistency, and explainable anomaly detection
- Statistical modeling and diagnostics applied pragmatically to business operations
- Automation in constrained tooling environments (Excel/VBA + ToolPak) to generate repeatable outputs
- Stakeholder alignment across BU owners, regional finance teams, and global reporting stakeholders

---

- 🔒 **Artifacts:** the underlying thesis/work and system screenshots are not published due to DHL confidentiality; this write-up is intentionally anonymized and excludes customer-identifying details and internal-only system identifiers, while preserving the process and technical substance.

