---
layout: default
title: UCL MPhil thesis (Computer Science) — Medical Imaging & Computer Vision
---

<blockquote>
🏠 <a href="/">Back to homepage</a> · 📚 <a href="/research/">Research & Theses</a>
</blockquote>

## UCL MPhil thesis — 3D non-rigid registration for image-guided interventions

This page summarizes my MPhil research project at **University College London (UCL)** focused on **3D non-rigid surface registration** for **image-guided interventions**, with an application case in **AR-guided robotic prostatectomy** (da Vinci).

> Note: A public PDF link will be added here once the thesis is uploaded to this site.

---

## Problem
In robotic prostatectomy, the intra-operative view is partial and can be affected by **occlusions, noise, and outliers**. The goal is to align a **pre-operative MRI-derived prostate surface** to a **partial intra-operative surface** so that guidance can be improved.

---

## Approach
The work benchmarks and compares **three non-rigid registration algorithms** (with an ICP baseline) under controlled conditions.

- Designed synthetic datasets to systematically vary:
  - deformation strength
  - noise level
  - outliers
  - partial overlap / occlusions
  - non-Gaussian noise
- Evaluated accuracy using **Target Registration Error (TRE)**.
- Implemented the algorithms in **C++** and ran batch experiments on a UCL CS compute cluster.
- Built a **Qt/VTK** tool to support manual alignment and visualization.

---

## Deliverables
- A complete thesis with methodology, experimental design, and results.
- Reproducible benchmarking workflow (code + experiments) (public artifacts to be added).
- Visual tooling for alignment and inspection (Qt/VTK).

---

## Technology
- C++
- Qt
- VTK
- (Computer vision / medical imaging workflow)

---

## Artifacts
- 📄 Thesis (PDF): coming soon
- 🔎 Case study reference: [Case studies](/case-studies)
