---
layout: default
title: Case studies
description: Delivery case studies highlighting clinical validation evidence, regulated platforms, AI healthcare, cloud integration, and technical leadership.
image: /assets/img/og-case-studies.png
---

<blockquote>
🏠 <a href="/">Back to homepage</a>
</blockquote>

Below are selected delivery case studies highlighting evidence-driven execution, regulated platforms, and technical leadership.

---

## Quick navigation
{: #quick-nav }
- [Clinical validation (ePokratis MedAiConnect, iOS)](#case-clinical-validation)
- [UCL MPhil thesis (3D non-rigid registration)](#case-ucl-mphil)
- [DHL GCS FACTs (finance validation & forecasting automation)](#case-dhl-facts)
- [Supply-chain distribution optimization (Excel/VBA cost model)](#case-supply-chain)
- [Data pipeline (industrial telemetry: Bronze/Silver/Gold + Quarantine)](#case-data-pipeline)

---

## Featured case studies

### 🧪 Clinical validation — ePokratis MedAiConnect (iOS)
{: #case-clinical-validation }
One-month clinical validation study at **Athens Hospital** (**Feb 6–Mar 6, 2025**) with **27 adults (20–91)** evaluating **accuracy, reliability, and data integrity** for **six Bluetooth medical devices** integrated with the ePokratis MedAiConnect **iOS** app, supporting App Store safety evidence under **Guideline 1.4.1 (Safety – Physical Harm)**. Athens Hospital clinical staff supervised measurements and **cross-verified that app-displayed values matched the device outputs**.

- **Devices validated:** TaiDoc TD-3128 (BP/PR), TD-8255 (SpO₂/PR), TD-1241 (Thermometer), TD-2555 (Scale), Contec PM10 (ECG/HR), TaiDoc TD-4216B (biomarkers).
- **Protocol:** paired comparison vs **hospital-grade reference standards**; **3× repeats per participant** for vital-sign devices; TD-4216B subset: **23/27** blood samples, **3× repeats per biomarker** with **single clinical reference per biomarker** (invasive sampling constraint).
- **Reference standards (Athens Hospital):** Omron HEM-907XL (BP), Nellcor bedside SpO₂ system, Welch Allyn Braun ThermoScan PRO 6000 (temperature), Seca 769 medical scale (weight), Philips PageWriter TC20 ECG system, Roche Cobas c 111 lab analyzer (biomarkers) — all certified and clinically operated.
- **Methods:** **ICC** (Pingouin; **ICC3 / ICC3k**), **MAD**, **Agreement %**, and **Bland–Altman** (mean difference and **95% limits of agreement: LOA = MD ± 1.96×SD**) with clinically/standard-derived thresholds (e.g., ISO 81060-2 for BP, ISO 15197 for glucose).
- **Key outcomes (study summary tables):** vital-sign devices showed **excellent reliability** (ICC3 **0.975–0.9999**; ICC3k **0.992–0.99997**); TD-4216B biomarkers ranged **very good to excellent** (ICC3 **0.889–0.997**, ICC3k **0.960–0.999**). Regulatory/clinical thresholds were defined per measure and summarized as ‘Met in study: Yes’ in the report’s compliance table.
- **Data integrity:** end-to-end workflow verified; **no missing values, no corruption, consistent units/labels/timestamps**, and **100% in-app match** to device readings across all devices (no integrity issues observed).
- ✅ Artifacts: [Evidence & downloads](/clinical-validation) · [Report (PDF)](/assets/pdfs/epokratis-medaiconnect-validation-report.pdf) · [Repro pack (ZIP)](/assets/downloads/validation_package.zip)

<blockquote>
⬆️ <a href="#quick-nav">Back to Quick navigation</a>
</blockquote>

---

### 🧠 UCL MPhil thesis — 3D non-rigid registration for image-guided interventions (prostate)
{: #case-ucl-mphil }
Research project at **UCL** benchmarking **non-rigid point-set registration** (TPS-based warps) for prostate surface alignment under **occlusion/partial overlap**, **noise**, and **outliers**, using **synthetic datasets** and **Target Registration Error (TRE)** (including evaluation **beyond common overlap**).

- 🔎 **Read the thesis summary:** [UCL MPhil — 3D non-rigid registration](/research/ucl-mphil/)
- 📄 **Thesis (PDF):** <a href="/assets/pdfs/ucl-mphil-thesis.pdf" target="_blank" rel="noopener noreferrer">Download / view</a>

---

### 📊 DHL Management (MBA Internship) — GCS FACTs: finance data validation & forecasting automation (confidential)
{: #case-dhl-facts }
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

<blockquote>
⬆️ <a href="#quick-nav">Back to Quick navigation</a>
</blockquote>

---

### 🏭 Supply-chain distribution optimization — Excel/VBA warehouse & cross-docking cost model (confidential)
{: #case-supply-chain }
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

<blockquote>
⬆️ <a href="#quick-nav">Back to Quick navigation</a>
</blockquote>

---

### 🏗️ Data pipeline — Industrial telemetry lakehouse (Bronze / Silver / Gold + Quarantine)
{: #case-data-pipeline }

#### Overview

This case study demonstrates a lightweight, **Azure-style lakehouse pipeline** and shows an end-to-end **Bronze → Silver/Quarantine → Gold** data flow for **synthetic industrial telemetry**, implemented in **Python** and orchestrated via **GitHub Actions** (manual trigger or scheduled run). It lands raw data into **Bronze**, applies validation rules during Bronze → Silver for **sensor_readings**, writes **clean records to Silver**, routes **rejected records to a Quarantine dataset** with reason codes for review, and produces **Gold** KPI outputs designed for reporting (e.g., Power BI).

- **Bronze (raw landed):** generates raw datasets for operational context — plants, assets, sensor readings, work orders, and quality inspections — under `lake/bronze/YYYY-MM-DD/`.
- **Silver + Quarantine (sensor_readings validation split):** validates **sensor_readings** only and splits the result:
  - **Silver:** clean records written to `lake/silver/YYYY-MM-DD/sensor_readings_clean.csv`
  - **Quarantine:** bad records written to `lake/quarantine/YYYY-MM-DD/sensor_readings_rejects.csv` with a `reject_reason` (reason codes)
- **Gold (curated outputs):** creates reporting-friendly outputs from Silver and enriches with asset metadata (from Bronze), producing:
  - `lake/gold/YYYY-MM-DD/plant_kpis.csv`
  - `lake/gold/YYYY-MM-DD/asset_health_daily.csv`
  - plus an easy-consumption copy: `exports/YYYY-MM-DD/plant_kpis.csv`
- **Traceability:** every run produces a **DQ report** (`reports/dq_YYYY-MM-DD.md`) and a downloadable **Actions artifacts ZIP** containing the full run outputs for that date.

<!-- quick artifact links -->
- Repo: [telemetry-pipeline-demo (GitHub)](https://github.com/iliassioutis/telemetry-pipeline-demo)
- Architecture diagram: [docs/diagrams/architecture.png](https://github.com/iliassioutis/telemetry-pipeline-demo/blob/main/docs/diagrams/architecture.png)
- Power BI report (PBIX): [docs/powerbi/telemetry-pipeline-demo-report.pbix](https://github.com/iliassioutis/telemetry-pipeline-demo/blob/main/docs/powerbi/telemetry-pipeline-demo-report.pbix)

**What the pipeline writes (folders):**
- Bronze (raw landed): `lake/bronze/YYYY-MM-DD/` (plants.csv, assets.csv, sensor_readings.jsonl, work_orders.csv, quality_inspections.csv, generation_meta.json)
- Silver (clean sensor readings): `lake/silver/YYYY-MM-DD/sensor_readings_clean.csv`
- Quarantine (rejected sensor readings): `lake/quarantine/YYYY-MM-DD/sensor_readings_rejects.csv`
- Gold (curated): `lake/gold/YYYY-MM-DD/plant_kpis.csv`, `lake/gold/YYYY-MM-DD/asset_health_daily.csv`
- Exports (easy consumption): `exports/YYYY-MM-DD/plant_kpis.csv`
- DQ report: `reports/dq_YYYY-MM-DD.md`

**What the Actions artifacts ZIP contains (download):**
- `exports/YYYY-MM-DD/plant_kpis.csv`
- `lake/bronze/YYYY-MM-DD/` (assets.csv, plants.csv, quality_inspections.csv, sensor_readings.jsonl, work_orders.csv, generation_meta.json)
- `lake/silver/YYYY-MM-DD/sensor_readings_clean.csv`
- `lake/quarantine/YYYY-MM-DD/sensor_readings_rejects.csv`
- `lake/gold/YYYY-MM-DD/` (plant_kpis.csv, asset_health_daily.csv)
- `reports/dq_YYYY-MM-DD.md`

#### Context

This demo uses **synthetic industrial operations data** to illustrate how an O&M telemetry pipeline is delivered end-to-end (no real customer data). Each run writes date-partitioned outputs (YYYY-MM-DD) so you can review results per day and reproduce runs using the same seed/parameters.

#### Key data fields (operational context)
{: #data-pipeline-fields }

##### How the entities connect (operationally)

Think of it like a hierarchy:

- A **Plant** is a manufacturing site (e.g., “Krakow Plant”). It has an ID: `plant_id`.
  - Each plant has **production lines** inside it (Line 1, Line 2, …). The count is `line_count`.

- An **Asset** is a piece of equipment (pump, motor, valve, etc.) installed in a plant.
  - In `assets.csv`, the column `plant_id` tells you **which plant the asset belongs to**.
  - So: `assets.plant_id` matches `plants.plant_id`.

- A **Sensor reading** is a telemetry measurement for one asset at a specific time.
  - In `sensor_readings.jsonl`, the column `asset_id` tells you **which asset produced the reading**.
  - So: `sensor_readings.asset_id` matches `assets.asset_id`.

- A **Work order** is a maintenance record for one asset (preventive or corrective).
  - In `work_orders.csv`, the column `asset_id` tells you **which asset the work order is for**.
  - So: `work_orders.asset_id` matches `assets.asset_id`.

- A **Quality inspection** is a quality check for a specific **plant + production line** at a time.
  - In `quality_inspections.csv`, `plant_id` tells you the plant, and `line_id` tells you the line within that plant.
  - So an inspection is tied to a specific “plant line” (example: `PLT-001` + `L02`).

##### Naming + format notes
- `*_id` fields are identifiers used to join tables.
- `*_ts_utc` / `ts_utc` are timestamps in **UTC** (ISO 8601, ending with `Z`).
- Units are encoded in the field name where possible: `temperature_c`, `pressure_bar`, `flow_l_min`, `vibration_mm_s`.
- **CSV** = rows/columns. **JSONL** = “JSON Lines” (one JSON object per line), good for streaming/time-series.

##### What this demo uses vs what is included for realism

- **Bronze (raw landed):** plants, assets, sensor_readings, work_orders, quality_inspections (+ generation_meta.json)
- **Silver + Quarantine:** sensor_readings only (validated + rejected rows with reason codes)
- **Gold outputs:** plant_kpis + asset_health_daily (derived from sensor_readings, enriched with asset metadata)
- **Work orders + inspections:** generated in Bronze for operational context, but **not yet part of Silver/Gold** in this demo

##### Why include work orders and quality inspections (even if Bronze-only here)

These two datasets are common in real operations pipelines and explain *business outcomes* that pure telemetry cannot:

- **Work orders (maintenance outcomes):** let you connect sensor behavior to reliability and cost — e.g. *which assets actually failed, how much downtime was caused, what was fixed, and whether it was preventive vs corrective*.
- **Quality inspections (production outcomes):** let you connect operating conditions to product quality — e.g. *which plant lines/batches show higher defect rates and whether certain conditions correlate with failures*.

##### Field glossary (expandable)
<div style="margin:10px 0; padding:10px 12px; border:1px solid #ddd; border-radius:10px; background:#f8f8f8;">
  <strong>Tip:</strong> The sections below are <strong>collapsible</strong>. Click the <strong>▶ title</strong> to open/close.
</div>

<details open markdown="1">
<summary style="cursor:pointer;">
  <span style="display:block; padding:8px 12px; border:1px solid #ddd; border-radius:10px; background:#ffffff;">
    <strong>▶ Plants</strong> <span style="opacity:.75;">(plants.csv)</span>
    <span style="float:right; opacity:.6;">Click to open/close</span>
  </span>
</summary>

- `plant_id` — unique plant/site identifier (e.g., `PLT-001`)
- `plant_name` — human-readable name
- `country` — country code (e.g., `PL`)
- `timezone` — IANA timezone string (e.g., `Europe/Warsaw`)
- `line_count` — number of production lines at the plant (drives `line_id` generation for inspections)

</details>

<div style="height:8px;"></div>

<details markdown="1">
<summary style="cursor:pointer;">
  <span style="display:block; padding:8px 12px; border:1px solid #ddd; border-radius:10px; background:#ffffff;">
    <strong>▶ Assets</strong> <span style="opacity:.75;">(assets.csv)</span>
    <span style="float:right; opacity:.6;">Click to open/close</span>
  </span>
</summary>

- `asset_id` — unique equipment identifier (e.g., `AST-00001`)
- `plant_id` — foreign key to Plants
- `asset_type` — equipment category (pump/motor/valve/etc.)
- `manufacturer`, `model` — equipment details
- `install_date` — installation date
- `criticality` — low/med/high (operational importance)
- `maintenance_strategy` — preventive/predictive/run-to-failure (how maintenance is planned)

</details>

<div style="height:8px;"></div>

<details markdown="1">
<summary style="cursor:pointer;">
  <span style="display:block; padding:8px 12px; border:1px solid #ddd; border-radius:10px; background:#ffffff;">
    <strong>▶ Sensor readings</strong> <span style="opacity:.75;">(sensor_readings.jsonl)</span>
    <span style="float:right; opacity:.6;">Click to open/close</span>
  </span>
</summary>

- `reading_id` — unique reading identifier
- `asset_id` — foreign key to Assets
- `ts_utc` — reading timestamp in UTC
- `temperature_c` — temperature in °C
- `vibration_mm_s` — vibration in mm/s
- `pressure_bar` — pressure in bar
- `flow_l_min` — flow in L/min
- `rpm` — rotational speed (revolutions per minute)
- `operating_state` — idle/running/off
- `sample_interval_sec` — sampling cadence in seconds (e.g., `900` = 15 minutes)

</details>

<div style="height:8px;"></div>

<details markdown="1">
<summary style="cursor:pointer;">
  <span style="display:block; padding:8px 12px; border:1px solid #ddd; border-radius:10px; background:#ffffff;">
    <strong>▶ Maintenance work orders</strong> <span style="opacity:.75;">(work_orders.csv — Bronze only in this demo)</span>
    <span style="float:right; opacity:.6;">Click to open/close</span>
  </span>
</summary>

- `wo_id` — unique work order identifier
- `asset_id` — foreign key to Assets
- `created_ts_utc`, `closed_ts_utc` — open/close timestamps in UTC
- `wo_type` — corrective/preventive
- `priority` — P1–P4 (P1 most urgent)
- `status` — lifecycle status (e.g., open/closed)
- `technician_team` — owning team
- `downtime_minutes` — downtime caused by the event
- `parts_cost_eur` — parts cost in EUR
- `failure_mode_code` — optional (nullable) code describing failure mode
- `root_cause_code` — optional (nullable) code describing root cause

<em>Nullable</em> means the field may be blank when unknown or not applicable.

</details>

<div style="height:8px;"></div>

<details markdown="1">
<summary style="cursor:pointer;">
  <span style="display:block; padding:8px 12px; border:1px solid #ddd; border-radius:10px; background:#ffffff;">
    <strong>▶ Quality inspections</strong> <span style="opacity:.75;">(quality_inspections.csv — Bronze only in this demo)</span>
    <span style="float:right; opacity:.6;">Click to open/close</span>
  </span>
</summary>

- `inspection_id` — unique inspection identifier
- `plant_id` — foreign key to Plants
- `line_id` — production line within the plant (e.g., `L01`)
- `ts_utc` — inspection timestamp in UTC
- `product_family` — product group being produced/checked
- `batch_id` — manufacturing batch identifier
- `result` — pass/fail
- `defect_code` — optional (nullable) defect code
- `defect_severity` — low/med/high (when a defect exists)

</details>

#### Problem
<!-- TODO -->

#### Solution design
<!-- TODO -->

#### Architecture
<!-- TODO: embed architecture image -->
<!-- Example image embed (use my final path/filename) -->
<!--
<div style="margin: 12px 0;">
  <img src="/assets/img/case-studies/data-pipeline/01-architecture.png"
       alt="Data pipeline architecture"
       style="max-width: 100%; height: auto;">
</div>
-->

#### Pipeline zones (Bronze / Silver / Gold / Quarantine)

All pipeline outputs are partitioned by run date:

- `lake/<zone>/YYYY-MM-DD/`

##### Bronze (raw landed)

Created by `src/generate_bronze.py`. This is the “as-landed” layer: raw files written per day for operational context.

- Output folder: `lake/bronze/YYYY-MM-DD/`
- Files written:
  - `plants.csv` (sites, country/timezone, number of lines)
  - `assets.csv` (equipment per plant: type, manufacturer/model, install date, criticality, maintenance strategy)
  - `sensor_readings.jsonl` (time-series telemetry per asset at a fixed cadence; default every 15 minutes)
  - `work_orders.csv` (maintenance history per asset: preventive/corrective, downtime, parts cost, optional failure/root-cause codes)
  - `quality_inspections.csv` (quality checks per plant line: pass/fail + optional defect code/severity)
  - `generation_meta.json` (run metadata: date, seed, counts, parameters)

To support the later validation/quarantine steps, the telemetry generator intentionally injects a small fraction of **bad sensor records** (controlled by `--bad-rate`, default `0.015`), including:
- missing `asset_id`
- out-of-range values (e.g., negative pressure or extreme temperature)
- duplicate `reading_id`

##### Silver (validated clean sensor readings)

Created by `src/bronze_to_silver.py`. This demo validates **sensor_readings only**.

- Output file: `lake/silver/YYYY-MM-DD/sensor_readings_clean.csv`
- Meaning: rows that pass required-field checks, timestamp format checks, numeric sanity ranges, and de-duplication by `reading_id`

##### Quarantine (rejected sensor readings)

Created by `src/bronze_to_silver.py`.

- Output file: `lake/quarantine/YYYY-MM-DD/sensor_readings_rejects.csv`
- Meaning: rows that fail validation or are duplicates
- Includes: `reject_reason` column with reason codes (for review and debugging)

##### Gold (curated KPIs for reporting)

Created by `src/silver_to_gold.py`. Produces reporting-friendly daily outputs derived from Silver and enriched with asset metadata from Bronze.

- Output folder: `lake/gold/YYYY-MM-DD/`
- Files written:
  - `plant_kpis.csv` (daily plant-level aggregates)
  - `asset_health_daily.csv` (daily asset-level summaries incl. a demo “health_score” metric)
- Export convenience copy:
  - `exports/YYYY-MM-DD/plant_kpis.csv`

##### DQ report (per run)

Created by `src/bronze_to_silver.py`.

- Output file: `reports/dq_YYYY-MM-DD.md`
- Meaning: totals, clean vs rejected counts, duplicate rejects, and top reject reasons

#### Automation (CI/CD)
<!-- TODO -->

#### Outputs (example visuals)
<!-- TODO: embed Power BI screenshots -->
<!--
<div style="margin: 12px 0;">
  <img src="/assets/img/case-studies/data-pipeline/02-powerbi-overview.png"
       alt="Power BI overview"
       style="max-width: 100%; height: auto;">
</div>
-->

<blockquote>
⬆️ <a href="#quick-nav">Back to Quick navigation</a>
</blockquote>
