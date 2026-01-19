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

### 🏭 Supply-chain distribution optimization — Excel/VBA warehouse & cross-docking cost model (confidential)

*Confidentiality note: company name, trade lanes, customer identifiers, SKU codes, and all internal figures are omitted or generalized. This case study focuses on the modelling approach, Excel/VBA engineering, and decision-support outputs.*

#### Context
I built an **Excel/VBA decision-support tool** to evaluate and optimize **distribution operations** across a two-node network:

- **Node A:** supplier distribution center (DC)  
- **Node B:** retailer distribution center (DC)

The tool supports three operational strategies and compares **end-to-end total cost** outcomes:

1) **Pure warehousing operations** (traditional DC handling + inventory)  
2) **Pick-by-line cross-docking** (pre-allocation at the supplier; consolidation downstream)  
3) **Pre-allocated cross-docking operator (CDO) consolidation** (cross-dock consolidation scenario)

The workbook is designed for **scenario planning**: users can vary pallet-mix strategies, handling charges, admin charges, and transportation tariff structures, then run **single-point** and **multi-point** (grid sweep) analyses with **graph outputs**.

#### Problem
Operational planning involved balancing trade-offs that are hard to reason about manually:

- **Palletization strategy:** how much volume should be shipped as **homogeneous pallets** vs **heterogeneous pallets** vs **loose/picked cases**
- **Transportation economics:** stepwise tariffs depending on shipped pallet ranges (brackets), plus a hard constraint on truck capacity
- **DC operating costs:** receiving, put-away, take-away, shipping, picking, labeling
- **Inventory vs flow-through:** traditional warehousing vs cross-docking where storage is minimized/removed
- **Sensitivity questions:** “Which cost drivers matter most?” and “How robust is the optimum to changing tariffs or picking charges?”

Pick-by-line cross-docking is evaluated as a **two-leg flow** (Supplier→Retailer and Retailer→Stores), each with its own target pallet-mix percentages.

The objective was to provide a repeatable mechanism to identify **low-cost operating points** and to explain **why** they are low-cost via cost breakdowns and sensitivity graphs.

---

## What was built (solution overview)

### 1) A structured input-and-run workflow (Excel UI)
The workbook guides users through a consistent workflow:

- **SKU input table** (per trade lane / period)
  - SKU identifiers (kept generic in this description)
  - total ordered quantities (cases)
  - packaging characteristics (cases per layer, cases per pallet)
  - optionally received homogeneous pallets (availability constraints)

- **Cost input blocks**
  - **Throughput costs**: receiving, put-away, take-away, shipping, picking (layer/case), labeling  
  - **Inventory holding costs**: holding charge, average inventory, time period (for warehousing scenarios)  
  - **Administration costs**: per customer order, per invoice, shipment count  
  - **Transportation costs**: **piecewise pallet-range brackets** with per-bracket charges

- **Mode selectors**
  - choose operating strategy (warehousing / cross-dock variants)
  - choose calculation node where relevant (supplier DC vs retailer DC)

- **Buttons/macros** to:
  - clear input spaces
  - scaffold tariff brackets
  - create shipments (automatic mode)
  - run single-point calculations
  - run multi-point grid sweeps
  - delete charts
  - generate “best” graphs for export/presentation

### 2) A cost model with traceable components
For each scenario, the tool computes a structured breakdown of costs across the network:

- **Throughput / handling costs** (per pallet or per case, depending on activity)
  - receiving / shipping
  - put-away to storage and take-away from storage (warehousing)
  - picking by layer / picking by case (cross-dock consolidation where applicable)
  - labeling (when applicable)

- **Administration costs**
  - driver-based model using order/invoice parameters and shipment count

- **Transportation costs**
  - computed per shipment using **tariff brackets** tied to shipped pallet ranges
  - **hard guardrail:** max **33 pallet spots per truck** enforced during shipment evaluation

- **Inventory holding costs**
  - applied in warehousing mode using: holding charge × average inventory × period
  - **cross-docking assumption:** inventory holding cost is treated as **zero** (flow-through; no storage)

The outputs support both:
- **single-point** deep-dive cost tables (for a chosen pallet-mix plan)  
- **multi-point** comparisons across many pallet-mix combinations

### 3) A heuristic “shipment-building engine” (Excel/VBA)
A core part of the tool is an **empirical pallet design heuristic** that translates pallet-mix targets into feasible pallet/shipment composition.

High-level logic:

- **Stage 1 — Homogeneous pallets first**
  - SKUs are ranked by **descending ordered quantity** (proxy for demand preference)
  - full homogeneous pallets are selected from highest-ranked SKUs until the target homogeneous volume is met (without exceeding requested volume)

- **Stage 2 — Heterogeneous pallets via full layers**
  - remaining stock becomes input for heterogeneous consolidation
  - heterogeneous pallets are assembled using **full layers** from **≥2 SKUs**
  - layers are selected proportionally to ordered quantities while respecting SKU rank
  - an overage tolerance can be used to allow reaching targets within a cutoff

- **Stage 3 — Loose cases / picked pallets**
  - remaining demand is satisfied by consolidating loose cases using a similar proportional, rank-guided process

A practical approximation is used to estimate heterogeneous pallet counts:
- compute an average cases-per-pallet factor (**Ω / Omega**) based on the selected mix
- estimate hetero pallet count from total cases / Ω  
- note: per-SKU physical heights/weights are not explicitly modeled; averages are used to reduce complexity while keeping the heuristic operationally useful.

### 4) Multi-point optimization search + graphing
To help identify near-optimal strategies without manual trial-and-error, the workbook supports **grid sweeps**:

- user sets an increment (e.g., 5%, 10%, etc.)
- the tool enumerates feasible combinations of:
  - % homogeneous
  - % heterogeneous
  - % loose/picked (computed as the remainder)

For each point:
- run the end-to-end scenario calculation
- store total costs for supplier DC, retailer DC, and combined network total
- display a “target vs actual” percentage view to show how the heuristic translated targets into realized outcomes

**Graph outputs** provide quick insight:
- 3D line cross-section graphs along the homogeneous axis for the multi-point results
- dedicated “Graphs” sheet to preserve the best outputs for reporting/export

### 5) Sensitivity analysis tooling (1D + 2D sweeps)
Beyond “what is optimal,” the workbook supports “why is it optimal?” by providing sensitivity engines:

- **Inventory sensitivity** (1D sweep)
  - vary holding charge / average inventory / period over a range
  - output total cost response and generate a 3D line chart

- **Administration sensitivity** (2D sweep)
  - vary euros per invoice and euros per customer order
  - compute administration or total cost surface and generate a surface chart

- **Throughput sensitivity** (2D sweep)
  - vary picking charges and receiving/shipping charges
  - compute throughput or total cost surface and generate a surface chart

Chart utilities delete/rebuild charts reliably and optionally “promote” the best chart to a curated “Graphs” sheet (supporting export-ready reporting).

---

## Key guardrails and assumptions (model transparency)

### General considerations
- **One-day lead time** from supplier DC to retailer DC from receipt of orders.
- **Transportation time variability** (road conditions, bottlenecks, speed variance) is ignored.
- Demand variability is addressed by analyzing **aggregated ordered quantities** over a chosen period.
- Focus is on **unit throughput costs** (handling per pallet/case) rather than fixed facility costs, layout, queuing, or congestion effects.
- DC capacity is assumed not to be exceeded (no overflow scenarios modeled).
- Fixed route between nodes; analysis is route-specific.
- Transportation uses **user-defined shipped pallet loads per truck**, applies **piecewise tariff brackets** (pallet-range charges), and enforces a **max 33 pallet spots per truck** guardrail.
- For cross-docking flows, goods may be **staged briefly (<24h)** (no storage), so **inventory holding cost is treated as zero**.

### Empirical pallet design rules (heuristic transparency)
- pallet construction follows: **homogeneous → heterogeneous (layers) → loose cases**
- SKUs ranked by ordered quantities; ranking used as a proxy for preference
- heterogeneous pallets built from full layers across multiple SKUs, selected proportionally and by rank
- heterogeneous pallet count estimated using **average cases-per-pallet (Ω)**; per-SKU physical dimensions not explicitly modeled

---

## Outcome and value
This tool enabled **repeatable, parameter-driven scenario planning** for distribution strategy selection:

- compare warehousing vs cross-docking variants on a consistent cost basis
- quickly identify low-cost pallet-mix strategies using multi-point sweeps
- explain results with cost breakdown tables and sensitivity surfaces
- enforce operational constraints (e.g., truck pallet-spot capacity) during scenario evaluation
- deliver export-ready charts for management discussion and decision support

---

## Execution flow (how the workbook runs)

1) **Inputs**
   - SKU table (ordered cases + cases/layer + cases/pallet + optional availability constraints)
   - Target pallet-mix percentages (homogeneous / heterogeneous / loose or picked)
   - Cost inputs (throughput, admin, inventory where applicable)
   - Transportation tariff brackets (piecewise pallet-range charges) + truck capacity guardrail
   - Mode selectors (strategy + node where relevant)

2) **Select scenario**
   - (1) Pure warehousing operations (handling + inventory)
   - (2) Pick-by-line cross-docking (two-leg flow: Supplier → Retailer, then Retailer → Stores)
   - (3) Pre-allocated consolidation scenario (cross-dock consolidation variant)

3) **Single-point run (one chosen pallet-mix)**
   - Build shipments (automatic) and translate target mix → feasible palletization using the 3-stage heuristic:
     - Stage 1: homogeneous pallets
     - Stage 2: heterogeneous pallets from full layers (≥2 SKUs)
     - Stage 3: loose/picked cases
   - Compute cost breakdown:
     - Throughput + Administration + Transportation (+ Inventory when applicable)
   - Produce outputs:
     - Supplier / Retailer / Total costs
     - “Target vs actual” mix (to show heuristic realization vs targets)

4) **Multi-point sweep (grid search over mix %)**
   - Enumerate feasible (homogeneous%, heterogeneous%) combinations
   - Derive picked% = 1 − (homogeneous% + heterogeneous%)
   - Run the single-point engine for each grid point
   - Store results table + generate cross-section graphs (along the homogeneous axis)

5) **Sensitivity runs (optional)**
   - Inventory (1D sweep), Administration (2D sweep), Throughput (2D sweep)
   - Rebuild charts and optionally promote “best” charts to the curated **Graphs** sheet

---

### Execution flow (diagram)

```text
INPUTS
  - SKU table + packaging parameters
  - Target mix % (homogeneous / heterogeneous / loose|picked)
  - Cost inputs (throughput, admin, inventory when applicable)
  - Transport brackets + 33 pallet-spot guardrail
  - Scenario + node selectors
        |
        v
SELECT SCENARIO
  (1) Warehousing
  (2) Pick-by-line cross-docking (two-leg flow)
  (3) Pre-allocated consolidation (cross-dock consolidation variant)
        |
        v
SINGLE-POINT RUN
  Shipments orchestrator
    -> Pallet heuristic (3 stages)
    -> Cost model (Throughput + Admin + Transport + Inventory where applicable)
    -> Outputs (Supplier / Retailer / Total + Target vs Actual mix)
        |
        +---------------------------+
        |                           |
        v                           v
MULTI-POINT SWEEP              SENSITIVITY RUNS
  (grid over mix %)              (inventory / admin / throughput)
  -> store results table         -> rebuild charts
  -> cross-section graphs        -> optionally promote to "Graphs" sheet
```

