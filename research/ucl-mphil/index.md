---
layout: default
title: UCL MPhil thesis (Computer Science) — Medical Imaging & Computer Vision
---

<blockquote>
🏠 <a href="/">Back to homepage</a> · 📚 <a href="/research/">Research & Theses</a>
</blockquote>

## UCL MPhil thesis — 3D non-rigid registration for image-guided interventions (prostate)

This page summarizes my MPhil research project at **University College London (UCL)** focused on **3D non-rigid surface registration** for **image-guided interventions**, targeting an application scenario in **robot-assisted prostate surgery** (da Vinci) where **pre-operative MRI anatomy** is aligned to a **partial intra-operative surface** reconstructed from stereo endoscopic video.

📄 **Thesis (PDF):** <a href="/assets/pdfs/ucl-mphil-thesis.pdf" target="_blank" rel="noopener noreferrer">Download / view</a>

---

## At a glance

- **Clinical context:** AR image guidance for minimally invasive surgery via **3D MRI anatomy** overlaid onto intra-operative views.
- **Core challenge:** **soft-tissue deformation** + **partial visibility (occlusion)** + **noise/outliers** + **no pre-defined correspondences**.
- **Algorithms benchmarked/extended:** non-rigid point-set registration methods combined with **TPS (thin-plate splines)**, with an ICP baseline.
- **Evaluation:** synthetic data with controlled perturbations + accuracy measured using **Target Registration Error (TRE)**, including a “beyond overlap” assessment.
- **Implementation:** C++ pipelines + reproducible batch experiments on a UCL CS cluster; a Qt/VTK/PCL GUI tool for manual initialization and dataset generation.

---

## Clinical motivation and AR guidance scenario

In minimally invasive surgery, limited field of view and reduced depth cues can be mitigated using **Augmented Reality (AR)** systems that:
1) construct **3D anatomical models** (e.g., from MRI/CT/US), and  
2) **register** these models to the intra-operative scene so subsurface structures are (virtually) revealed.

In this thesis, **3D MRI** is used as the pre-operative modality for prostate anatomy, while the intra-operative representation is a **3D point-cloud** reconstructed from stereo endoscopic video, as in a da Vinci workflow.

---

## Problem statement and real-world constraints

A reliable AR overlay requires registration under difficult conditions:

- The target model is often a **deformed subset** of the source, and the **overlap is unknown** in advance.
- The deformation is **non-linear** and not known a priori.
- **No explicit point-to-point correspondences** are provided before registration.
- The target may contain **noise** and/or **outliers**.

---

## What I contributed (high level)

This research is centered on making state-of-the-art non-rigid registration methods more applicable to **occluded / partial 3D surfaces**, which is a key barrier for intra-operative use.

Key deliverables included:
- Extending selected non-rigid registration frameworks to better handle **occlusion of 3D surfaces**.
- Designing comprehensive **synthetic prostate test datasets** that simulate realistic clinical conditions (deformation / noise / outliers / occlusion).
- Building structured test harnesses to explore each method’s **solution space** across datasets and parameters.
- Demonstrating the importance of **rigorous validation** when assessing warping accuracy.
- Implementing a **GUI tool** to support manual initialization and reproducible experiment workflows.

---

## Technical approach

### Registration paradigm
The thesis benchmarks **non-rigid point-set registration** under conditions where:
- correspondences are not given,
- the observed target is partial,
- and deformation must be recovered.

A key modeling element is **Thin-Plate Splines (TPS)** (a radial-basis-function deformation model) used to represent smooth non-linear warps.

### Algorithms studied
The work focuses on three non-rigid methods (paired with TPS warping) and compares their performance under controlled scenarios:

- **KC + TPS:** Kernel Correlation based correspondence/fit + TPS deformation
- **GMM + TPS:** Gaussian Mixture Model alignment + TPS deformation
- **EM + TPS:** Expectation-Maximization correspondence estimation + TPS deformation

An **ICP** baseline is used as a reference point for rigid alignment behavior.

---

## Experimental design and synthetic datasets

Because intra-operative scenes can be partial and heavily perturbed, the thesis designs synthetic datasets that progressively introduce real-world difficulties, including:

- deformation via TPS warps
- noise injection (including non-Gaussian cases)
- outliers
- partial views (occlusion)
- tests that measure performance **beyond common overlap** (i.e., not just in the region that happens to match)

A segmented 3D prostate mesh derived from MRI was used as the foundational shape for simulations.

---

## Evaluation and accuracy metric

### Target Registration Error (TRE)
Registration accuracy is evaluated using **TRE**, i.e., the RMS distance between homologous target points after registration (in synthetic experiments, ground truth correspondences are known by construction).

### Why “beyond overlap” matters
In partial-to-full (or partial-to-partial) settings, a method can appear accurate if you only score it inside the easy overlap region. This thesis explicitly evaluates **warping behavior beyond the common overlap**, which is essential if you want AR overlays to remain anatomically plausible when part of the organ is not visible.

---

## Key results (selected thesis conclusions)

### Full-model to full-model
- **EM + TPS** was the most accurate among the three methods for recovering deformation in **full-model-to-full-model** registrations.

### Occluded / partial target scenes (beyond overlap)
- In occluded target scenes where recovering deformation **beyond the overlap** is required, the results favored **modified KC+TPS and modified GMM+TPS** approaches (with measured warping accuracy beyond overlap on the order of ~2 mm in the reported experiments).

### Sensitivity to noise / scene size (practical takeaways)
- The thesis reports concrete operating regimes showing when registrations remain clinically plausible, including thresholds tied to:
  - **target scene size** (fraction of the surface visible)
  - **noise levels** and correspondence robustness

(These are summarized in the final thesis chapter; this web page keeps them high-level, and the PDF is the authoritative reference for the exact tables/values.)

---

## Implementation & tooling

### C++ pipeline + batch experiments
- Algorithms and experiment code were implemented in **C++**, using **VTK** for geometry/visualization workflows.
- Large experiment grids were executed via **batch jobs** on a UCL Computer Science cluster.

### Manual initialization & inspection GUI (Qt/VTK/PCL)
A custom GUI application supported manual initialization and reproducible workflows, including:

- scale + superimpose source/target and save aligned outputs
- optional downsampling
- surface reconstruction utilities
- cropping a full model into a partial view
- loading multiple 3D datasets into a common coordinate frame
- generating synthetic test data
- computing TRE metrics

---

## Relevance for modern evidence-driven delivery

Although this was academic research, the delivery pattern is strongly aligned with regulated / evidence-heavy work:

- explicit problem statement + constraints
- controlled test design to simulate realistic edge cases
- quantitative evaluation (TRE) with careful interpretation (including beyond-overlap assessment)
- reproducible experimentation at scale (batch runs)
- tooling to support traceability and inspection

---

## Artifacts

- 📄 **Thesis (PDF):** <a href="/assets/pdfs/ucl-mphil-thesis.pdf" target="_blank" rel="noopener noreferrer">Download / view</a>
- 🧾 **Research area:** [Research & Theses](/research/)
- 🔎 **Case study reference:** [Case studies](/case-studies)

