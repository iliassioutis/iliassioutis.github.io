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

### 🧠 UCL MPhil thesis — 3D non-rigid registration for image-guided interventions (prostate)
Research project at **UCL** benchmarking **non-rigid point-set registration** (TPS-based warps) for prostate surface alignment under **occlusion/partial overlap**, **noise**, and **outliers**, using **synthetic datasets** and **Target Registration Error (TRE)** (including evaluation **beyond common overlap**).

- 🔎 **Read the thesis summary:** [UCL MPhil — 3D non-rigid registration](/research/ucl-mphil/)
- 📄 **Thesis (PDF):** <a href="/assets/pdfs/ucl-mphil-thesis.pdf" target="_blank" rel="noopener noreferrer">Download / view</a>

---

### 📊 DHL Management (MBA Internship) — GCS FACTs: finance data validation & forecasting automation (confidential)

*Confidentiality note: customer identifiers, internal contacts, and intranet-only details are omitted. This summary focuses on the validation workflow, analytics approach, and deliverables described in the thesis.*

#### Context
This MBA research project (Cass Business School, 2009) was initiated by **GCS senior management** to improve **monthly validation** of large customer datasets across **regions** (EMEA, Americas, AP) and multiple **business units (BUs)**. The goal was to strengthen quality control for customer reporting (e.g., **revenue, profitability, volume, A/R, and related cost views**) in a complex, BU-specific systems landscape.

#### Problem
Validation during monthly close was slow and error-prone:
- Large volumes of data were validated by many people, increasing the risk of **human error**.
- Failed validations often led to long internal discussions about **where** an issue occurred in the process and **how** to correct it.
- Processes differed by BU and region, and data often had to be reconciled across **system extracts** and **Excel-based files**.

#### Research approach
- **Secondary research:** internal/non-public sources to map the organization, reporting concepts, and data landscape.
- **Primary research:** structured interviews across time zones over ~two months and creation of detailed **Excel master files** documenting customer data sources and content by **BU / country / region**.

#### Validation workflow (documented in the thesis)
Two operational variants were described:

- **Excel-file-based validation (regional-led):**
  - regional finance teams extract data from BU source systems and compare them against BU-provided Excel files
  - create a master dataset, validate completeness and consistency, and upload pre-close validated data into a contributor environment
  - global consolidation and additional checks follow before final reporting

- **Contributor-based validation (global-led):**
  - the global team extracts and loads customer data directly to the contributor environment
  - corrections are applied using BU Excel inputs; regional teams can then add adjustments
  - similar pre-close / final-close checks follow through to reporting outputs

#### What was built (Excel/VBA analytics automation)
Because Excel was the practical platform used by the finance organization, statistical models were implemented in **Excel with VBA** to support validation and analysis.

- **FREIGHT model (time-series validation & forecasting)**
  - short-horizon forecasting using **moving averages (MA2 / MA3)**
  - forecast error tracked via **MAD (mean absolute deviation)**
  - time-series breakdown outputs (trend + seasonal proxy + residuals) where data sufficiency allowed
  - validation-month checking using **standard deviation–based logic**
  - automated generation of a monthly **validation report** (sample report referenced in appendices)

- **EXPRESS model (driver-based validation)**
  - modeled **revenue vs operational drivers** (e.g., weight and shipments) using regression (simple / multiple)
  - model diagnostics including **R² / adjusted R²**, coefficient significance (p-values), residual checks, and **Durbin–Watson** autocorrelation testing
  - automated summary tables and plots to support investigation of conspicuous data

#### Outcome (business value described)
- Improved visibility into validation steps and data-flow dependencies at BU/region/global levels.
- Enabled more systematic identification of **conspicuous data**, **outliers**, and **inconsistencies** during pre-close and final-close validation.
- Provided a repeatable analytics foundation in a toolset (Excel/VBA) aligned with how the finance teams operated.

---

### 🚚 Supply chain distribution optimization — Cross-docking & warehousing cost model (Excel/VBA) *(confidential)*

*Confidentiality note: company/customer identifiers, trade lanes, SKU-level data, tariff tables, and internal process documents are omitted. This summary focuses on the modeling approach, decision logic, and deliverables.*

#### Context
Industry collaboration project (2010–2011) focused on improving **distribution operations strategy** by comparing **traditional warehousing** versus **cross-docking variants** under realistic operational constraints (pallet building, picking, throughput, transportation pricing, and inventory).

#### Problem
Distribution decisions required balancing multiple cost drivers across two nodes (upstream and downstream DCs):
- Throughput operations (receiving, put-away, retrieval, shipping, picking)
- Transportation costs driven by **truck fill / pallet-spot ranges** (piecewise tariff structure)
- Inventory holding effects and planning-period assumptions
- Cross-docking mode differences (where consolidation happens and how pallets/cases are handled)

Manual analysis was slow, difficult to reproduce, and not suitable for structured “what-if” exploration.

#### What was built (Excel/VBA decision-support model)
A multi-sheet **Excel/VBA** application that converts scenario inputs into comparable cost outputs for multiple operating modes:

- **Operating modes supported**
  - Pure warehousing operations
  - Pick-by-line cross-docking
  - Pre-allocated cross-dock operator consolidation  
  *(all evaluated under the same demand context for comparability)*

- **Range-based transportation pricing**
  - Transportation modeled with **bracketed pallet-spot ranges** (piecewise tariffs)
  - A guided workflow generates the required number of brackets and applies the correct charge based on each shipment’s computed pallet spots

- **Cost engine & breakdown**
  - Computes costs for **both nodes** (upstream and downstream DC)
  - Categories include **throughput**, **transportation**, **inventory holding**, and **administration**
  - Produces a detailed breakdown for a chosen configuration plus scenario-level totals

#### How it was used (workflow)
- **Load scenario inputs** (orders, pallet-building drivers, and operational parameters)
- **Run multi-point exploration (grid search)** across feasible pallet-mix allocations (homogeneous / heterogeneous / picked)
- **Generate cost-surface plots** to identify low-cost regions and candidate operating points
- **Run single-point deep dive** to obtain a full cost breakdown for the selected configuration
- **Run sensitivity analysis**
  - 1D sensitivity on inventory drivers (e.g., holding charge / average inventory / planning period)
  - 2D sensitivity surfaces for throughput costs (picking vs receiving/shipping) and administration drivers  
  - Auto-generated charts saved into a dedicated “Graphs” area for decision decks

#### Outcome (business value)
- Enabled repeatable, evidence-driven comparison of **warehousing vs cross-docking strategies**
- Supported “what-if” decision-making with transparent assumptions and automated outputs
- Reduced manual effort and improved consistency of scenario evaluation through reusable model runs



