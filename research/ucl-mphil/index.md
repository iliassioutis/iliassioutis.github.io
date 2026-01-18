---
layout: default
title: UCL MPhil thesis (Computer Science) — Medical Imaging & Computer Vision
---

<blockquote>
🏠 <a href="/">Back to homepage</a> · 📚 <a href="/research/">Research & Theses</a>
</blockquote>

## UCL MPhil thesis — 3D non-rigid registration for image-guided interventions (prostate)

This page summarizes my MPhil research project at **University College London (UCL)** on **3D non-rigid surface registration** for **image-guided interventions**, targeting an application scenario in **robot-assisted prostate surgery** (da Vinci) where **pre-operative MRI anatomy** is aligned to a **partial intra-operative surface** reconstructed from stereo endoscopic video.

📄 **Thesis (PDF):** <a href="/assets/pdfs/ucl-mphil-thesis.pdf" target="_blank" rel="noopener noreferrer">Download / view</a>

---

## At a glance

- **Clinical context:** AR image guidance for minimally invasive surgery via **3D MRI anatomy** aligned to intra-operative views.
- **Core challenge:** **soft-tissue deformation** + **partial visibility (occlusion)** + **noise/outliers** + **no pre-defined correspondences**.
- **Algorithms benchmarked/extended:** non-rigid point-set registration methods combined with **TPS (thin-plate splines)**, with an **ICP baseline**.
- **Evaluation:** synthetic prostate data with controlled perturbations; accuracy measured with **Target Registration Error (TRE)**, including explicit evaluation in the **space beyond common overlap**.
- **Implementation:** **C++/VTK** pipelines; reproducible batch experiments on a UCL CS compute cluster; a **Qt/VTK** GUI tool with point-cloud utilities (incl. downsampling via VTK/PCL options) to support reproducible workflows.

---

## Clinical motivation and AR guidance scenario

In minimally invasive surgery, limited field of view and reduced depth cues can be mitigated using **Augmented Reality (AR)** systems that:

<ol>
  <li>construct <strong>3D anatomical models</strong> (e.g., from MRI/CT/US),</li>
  <li><strong>register</strong> these models to the intra-operative scene so subsurface structures can be visualized.</li>
</ol>

In this thesis, a **segmented 3D prostate surface derived from MRI** serves as the pre-operative model, while the intra-operative representation is treated as a **partial 3D point-cloud** reconstructed from stereo endoscopic video.

---

## Problem statement and real-world constraints

A reliable AR overlay requires registration under difficult conditions:

- The target model can be a **deformed subset** of the source, and the **overlap is not known** in advance.
- Deformation is **non-linear** and not known a priori.
- **No explicit point-to-point correspondences** are provided before registration.
- The target may include **measurement noise** and/or **outliers**.

---

## What I contributed (high level)

This research focuses on making state-of-the-art non-rigid registration methods more applicable to **occluded / partial 3D surfaces**.

Key deliverables included:
- Reformulating selected non-rigid registration methods to address **occlusion** in full-model-to-partial-model settings.
- Designing comprehensive **synthetic prostate datasets** simulating clinically relevant perturbations (deformation / noise / outliers / occlusion).
- Building structured experimental workflows to evaluate performance across controlled scenarios and parameter settings.
- Demonstrating why **validation beyond common overlap** is critical when assessing non-rigid warps for partial registrations.
- Implementing a **GUI tool** to support manual initialization, dataset preparation, and reproducible experimentation.

---

## Technical approach

### Registration paradigm
The thesis benchmarks **non-rigid point-set registration** where:
- correspondences are not given,
- the observed target is partial,
- and deformation must be recovered.

A key modeling element is **Thin-Plate Splines (TPS)** (a radial-basis-function deformation model) used to represent smooth non-linear warps.

### Algorithms studied
Three non-rigid methods (paired with TPS warping) are examined and compared under controlled scenarios:

- **KC + TPS:** Kernel Correlation + TPS deformation
- **GMM + TPS:** Gaussian Mixture Model alignment + TPS deformation
- **EM + TPS:** Expectation-Maximization correspondence estimation + TPS deformation

An **ICP** baseline is used as a reference point for rigid alignment behavior.

---

## Experimental design and synthetic datasets

Synthetic datasets progressively introduce real-world difficulties, including:

- deformation via TPS warps
- noise injection (including non-Gaussian cases)
- outliers
- partial views (occlusion)
- evaluation of warping accuracy both **in the overlap region** and **beyond common overlap**

A segmented 3D prostate surface derived from MRI is used as the foundational shape for simulations.

---

## Evaluation and accuracy metric

### Target Registration Error (TRE)
Accuracy is evaluated using **TRE**, computed in synthetic experiments where **ground truth is known by construction** (reported as mean ± standard deviation across experiment conditions).

### Why “beyond common overlap” matters
For partial registrations, evaluating accuracy only in the region of overlap can be misleading. This thesis explicitly evaluates warping behavior in the **space beyond common overlap**, and treats this as the most reliable validation scheme for full-to-partial registrations.

---

## Key results (from the thesis conclusions)

### Full-model to full-model registrations
- **EM + TPS** outperformed **KC + TPS** and **GMM + TPS** in full-model-to-full-model synthetic prostate registrations.
- Reported warping accuracies for **EM + TPS** were **below 2 mm** for clinically relevant simulations.

### Full-model to partial/occluded target scenes
- For occlusion-aware full-model-to-partial-model registrations, **KC + TPS** and **GMM + TPS** were the only methods reported to yield valid point-to-point (and “clinically acceptable”) correspondences in the tested settings.
- The **EM/TPS** approach could not recover deformation accurately in full-model-to-occluded-model registrations due to how correspondences are estimated.

### Beyond-overlap warping accuracy (reported example)
For occluded (~38% of the original surface) and deformed synthetic target prostates, the thesis reports beyond-overlap warping accuracy of:
- **(2.1650 ± 1.0154) mm** using modified **KC/TPS**
- **(2.1677 ± 0.9716) mm** using modified **GMM/TPS**

The thesis also reports a corresponding maximum allowable Gaussian noise standard deviation **σ = 0.345** (with μ = 0) for both methods under those conditions, without pushing mean registration error above **3 mm**.

---

## Implementation & tooling

### C++ pipeline + batch experiments
- Algorithms and experiment code were implemented in **C++**, using **VTK** for geometry and visualization workflows.
- Large experiment grids were executed via **batch jobs** on a UCL Computer Science compute cluster.

### Manual initialization & inspection GUI (Qt/VTK + point-cloud utilities)
A custom GUI application supported reproducible workflows, including:
- scaling and superimposing source/target point clouds and saving aligned outputs
- downsampling (VTK- or PCL-based options)
- cropping a full model into a partial target scene (occlusion simulation)
- generating synthetic test datasets
- computing and reporting TRE-based metrics

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

