---
layout: default
title: Jira-style workflow example
---

<blockquote>
🏠 <a href="/">Back to homepage</a> · <a href="/project-delivery/">Project Delivery &amp; Methods</a>
</blockquote>

This page shows a **Jira-style end-to-end delivery workflow** using a **personal sandbox** with **fully fictitious tickets** (no client data).  
It demonstrates how I structure delivery from **requirements → build → QA/SIT → UAT → release**, including how artifacts connect and how I run **release readiness**.

> **Note**  
> This is not a Jira-administrator showcase. It’s a practical Jira-style example that reflects how I manage delivery, quality gates, and governance. 

---

## What this example covers

- Intake → framing → approval to start work
- Epic → stories/tasks → acceptance criteria → Definition of Done (DoD)
- Sprint / Kanban execution with blockers and dependency handling
- Quality gates (SIT / UAT) and release readiness
- Post-release validation, hypercare, and closure

---

## Scenario used in the sandbox (fictitious)

**Product context:** A regulated digital-health mobile app with secure backend  
**Feature:** Add a “Contactless vitals (camera)” measurement session + history entry  
**Constraints:** privacy-by-design, no camera media storage, audit-ready changes, staged rollout  
**Stakeholders:** Product, Mobile (iOS/Android), Backend, QA, Security/Privacy, Clinical/Validation, Support

> This mirrors the type of work I’ve delivered in practice, but the tickets, names, and IDs here are fully fictitious.

---

## Project setup (what you will see in Jira)

### Issue types used
- **Epic** (feature-level outcome)
- **Story** (user-facing increment)
- **Task** (engineering / implementation work)
- **Bug** (defects)
- **Spike** (timeboxed research / validation)
- **Sub-task** (QA checklist items, test execution, release tasks)

### Fields / conventions used (kept simple and realistic)
- **Priority**, **Labels**, **Component** (iOS / Android / Backend / QA / Security)
- **Fix Version / Release** (e.g., `v1.8.0`)
- **Acceptance criteria** and **test notes** in the ticket description
- **Definition of Done** checklist (lightweight, consistent)

---

## Workflow used (Jira-style)

**Statuses (simple + realistic):**
- **Backlog**
- **Ready**
- **In Progress**
- **In Review**
- **QA / SIT**
- **UAT**
- **Ready for Release**
- **Done**

**Typical transitions:**
- Backlog → Ready (refined, sized, dependencies identified)
- Ready → In Progress (pulled into a sprint / started)
- In Progress → In Review (PR ready, peer review started)
- In Review → QA/SIT (build delivered to test env, test execution begins)
- QA/SIT → UAT (business sign-off/testing)
- UAT → Ready for Release (release checklist completed)
- Ready for Release → Done (released + notes captured)

---

# End-to-end example tickets (what we will build)

Below is the complete ticket tree created in the sandbox.  


## 1) Intake / Epic

<a id="artifact-nav"></a>
### Navigation (this section)

**Pages artifacts**
- [Pages index](#pages-index)
- [BRD](#brd-business-requirements-document--full-page-screenshots)
- [FRD](#frd-functional-requirements-document--full-page-screenshots)
- [RAID log](#raid-log-risks-assumptions-issues-dependencies--full-page-screenshots)
- [User journeys](#journeys--full-page-screenshots)
- [Figma walkthrough](#figma--full-page-screenshots)

**Jira views**
- [Epic — SCRUM-6](#epic-scrum-6)
- [Feature — SCRUM-5](#feature-scrum-5)
- [Sprint 0 — Backlog view](#sprint0-backlog)
- [Sprint 1 — Backlog view](#sprint1-backlog)

**Sprint 0 stories**
- [S-01 — SCRUM-7: Define scope + requirements](#sprint0-scrum-7)
- [S-02 — SCRUM-8: Requirements & user journeys](#sprint0-scrum-8)
- [S-03 — SCRUM-9: UX/UI wireframes + prototype](#sprint0-scrum-9)

**Sprint 1 work items**
- [S-04 — SCRUM-10: On-device AI wellness estimates integration](#sprint1-scrum-10)
- [S-05 — SCRUM-11: Bluetooth device ingestion + data integrity checks](#sprint1-scrum-11)
- [S-06 — SCRUM-12: Secure backend + APIs](#sprint1-scrum-12)
- [S-07 — SCRUM-13: Privacy & security controls](#sprint1-scrum-13)
- [S-08 — SCRUM-14: Test plan + SIT](#sprint1-scrum-14)
- [S-09 — SCRUM-15: UAT plan + sign-off pack](#sprint1-scrum-15)
- [S-10 — SCRUM-16: Release checklist + monitoring + hypercare plan](#sprint1-scrum-16)
- [BUG-01 — SCRUM-109: Android BLE reconnection unstable](#sprint1-scrum-109)
- [BUG-02 — SCRUM-110: History API returns 500 when optional field missing](#sprint1-scrum-110)

<a id="pages-index"></a>
### Pages index — Jira Pages list (BRD / FRD / RAID / Journeys / Figma)

<a href="/assets/img/jira-workflow/00-pages-index.png" target="_blank" rel="noopener">
  <img src="/assets/img/jira-workflow/00-pages-index.png"
       alt="Sandbox Pages index — BRD, FRD, RAID Log, User Journeys, Figma walkthrough"
       loading="lazy"
       style="max-width: 1400px; width: 100%; border: 1px solid #e5e7eb; border-radius: 8px; display:block; margin: 12px 0;">
</a>

<p style="font-size: 0.95em; color: #6b7280; margin-top: 6px;">
  Click the image to open full size.
</p>

<p style="margin: 6px 0 18px 0;">
  <a href="#artifact-nav">↑ Back to navigation</a>
</p>

<hr style="margin: 24px 0; border: 0; border-top: 1px solid #e5e7eb;">

<a id="brd-business-requirements-document--full-page-screenshots"></a>
### BRD (Business Requirements Document) — full page (screenshots)

<!-- BRD chunk 1 -->
<a href="/assets/img/jira-workflow/01-brd-01.png" target="_blank" rel="noopener">
  <img src="/assets/img/jira-workflow/01-brd-01.png"
       alt="BRD — E-01 (chunk 1)"
       loading="lazy"
       style="max-width: 1400px; width: 100%; border: 1px solid #e5e7eb; border-radius: 8px; display:block; margin: 12px 0;">
</a>

<!-- BRD chunk 2 -->
<a href="/assets/img/jira-workflow/01-brd-02.png" target="_blank" rel="noopener">
  <img src="/assets/img/jira-workflow/01-brd-02.png"
       alt="BRD — E-01 (chunk 2)"
       loading="lazy"
       style="max-width: 1400px; width: 100%; border: 1px solid #e5e7eb; border-radius: 8px; display:block; margin: 12px 0;">
</a>

<!-- BRD chunk 3 -->
<a href="/assets/img/jira-workflow/01-brd-03.png" target="_blank" rel="noopener">
  <img src="/assets/img/jira-workflow/01-brd-03.png"
       alt="BRD — E-01 (chunk 3)"
       loading="lazy"
       style="max-width: 1400px; width: 100%; border: 1px solid #e5e7eb; border-radius: 8px; display:block; margin: 12px 0;">
</a>

<!-- BRD chunk 4 -->
<a href="/assets/img/jira-workflow/01-brd-04.png" target="_blank" rel="noopener">
  <img src="/assets/img/jira-workflow/01-brd-04.png"
       alt="BRD — E-01 (chunk 4)"
       loading="lazy"
       style="max-width: 1400px; width: 100%; border: 1px solid #e5e7eb; border-radius: 8px; display:block; margin: 12px 0;">
</a>

<!-- BRD chunk 5 -->
<a href="/assets/img/jira-workflow/01-brd-05.png" target="_blank" rel="noopener">
  <img src="/assets/img/jira-workflow/01-brd-05.png"
       alt="BRD — E-01 (chunk 5)"
       loading="lazy"
       style="max-width: 1400px; width: 100%; border: 1px solid #e5e7eb; border-radius: 8px; display:block; margin: 12px 0;">
</a>

<!-- BRD chunk 6 -->
<a href="/assets/img/jira-workflow/01-brd-06.png" target="_blank" rel="noopener">
  <img src="/assets/img/jira-workflow/01-brd-06.png"
       alt="BRD — E-01 (chunk 6)"
       loading="lazy"
       style="max-width: 1400px; width: 100%; border: 1px solid #e5e7eb; border-radius: 8px; display:block; margin: 12px 0;">
</a>

<!-- BRD chunk 7 -->
<a href="/assets/img/jira-workflow/01-brd-07.png" target="_blank" rel="noopener">
  <img src="/assets/img/jira-workflow/01-brd-07.png"
       alt="BRD — E-01 (chunk 7)"
       loading="lazy"
       style="max-width: 1400px; width: 100%; border: 1px solid #e5e7eb; border-radius: 8px; display:block; margin: 12px 0;">
</a>

<p style="font-size: 0.95em; color: #6b7280; margin-top: 6px;">
  Click any image to open it full size.
</p>

<p style="margin: 6px 0 18px 0;">
  <a href="#artifact-nav">↑ Back to navigation</a>
</p>

<hr style="margin: 24px 0; border: 0; border-top: 1px solid #e5e7eb;">

<a id="frd-functional-requirements-document--full-page-screenshots"></a>
### FRD (Functional Requirements Document) — full page (screenshots)

<!-- FRD chunk 1 -->
<a href="/assets/img/jira-workflow/02-frd-01.png" target="_blank" rel="noopener">
  <img src="/assets/img/jira-workflow/02-frd-01.png"
       alt="FRD — E-01 (chunk 1)"
       loading="lazy"
       style="max-width: 1400px; width: 100%; border: 1px solid #e5e7eb; border-radius: 8px; display:block; margin: 12px 0;">
</a>

<!-- FRD chunk 2 -->
<a href="/assets/img/jira-workflow/02-frd-02.png" target="_blank" rel="noopener">
  <img src="/assets/img/jira-workflow/02-frd-02.png"
       alt="FRD — E-01 (chunk 2)"
       loading="lazy"
       style="max-width: 1400px; width: 100%; border: 1px solid #e5e7eb; border-radius: 8px; display:block; margin: 12px 0;">
</a>

<!-- FRD chunk 3 -->
<a href="/assets/img/jira-workflow/02-frd-03.png" target="_blank" rel="noopener">
  <img src="/assets/img/jira-workflow/02-frd-03.png"
       alt="FRD — E-01 (chunk 3)"
       loading="lazy"
       style="max-width: 1400px; width: 100%; border: 1px solid #e5e7eb; border-radius: 8px; display:block; margin: 12px 0;">
</a>

<!-- FRD chunk 4 -->
<a href="/assets/img/jira-workflow/02-frd-04.png" target="_blank" rel="noopener">
  <img src="/assets/img/jira-workflow/02-frd-04.png"
       alt="FRD — E-01 (chunk 4)"
       loading="lazy"
       style="max-width: 1400px; width: 100%; border: 1px solid #e5e7eb; border-radius: 8px; display:block; margin: 12px 0;">
</a>

<!-- FRD chunk 5 -->
<a href="/assets/img/jira-workflow/02-frd-05.png" target="_blank" rel="noopener">
  <img src="/assets/img/jira-workflow/02-frd-05.png"
       alt="FRD — E-01 (chunk 5)"
       loading="lazy"
       style="max-width: 1400px; width: 100%; border: 1px solid #e5e7eb; border-radius: 8px; display:block; margin: 12px 0;">
</a>

<!-- FRD chunk 6 -->
<a href="/assets/img/jira-workflow/02-frd-06.png" target="_blank" rel="noopener">
  <img src="/assets/img/jira-workflow/02-frd-06.png"
       alt="FRD — E-01 (chunk 6)"
       loading="lazy"
       style="max-width: 1400px; width: 100%; border: 1px solid #e5e7eb; border-radius: 8px; display:block; margin: 12px 0;">
</a>

<!-- FRD chunk 7 -->
<a href="/assets/img/jira-workflow/02-frd-07.png" target="_blank" rel="noopener">
  <img src="/assets/img/jira-workflow/02-frd-07.png"
       alt="FRD — E-01 (chunk 7)"
       loading="lazy"
       style="max-width: 1400px; width: 100%; border: 1px solid #e5e7eb; border-radius: 8px; display:block; margin: 12px 0;">
</a>

<!-- FRD chunk 8 -->
<a href="/assets/img/jira-workflow/02-frd-08.png" target="_blank" rel="noopener">
  <img src="/assets/img/jira-workflow/02-frd-08.png"
       alt="FRD — E-01 (chunk 8)"
       loading="lazy"
       style="max-width: 1400px; width: 100%; border: 1px solid #e5e7eb; border-radius: 8px; display:block; margin: 12px 0;">
</a>

<!-- FRD chunk 9 -->
<a href="/assets/img/jira-workflow/02-frd-09.png" target="_blank" rel="noopener">
  <img src="/assets/img/jira-workflow/02-frd-09.png"
       alt="FRD — E-01 (chunk 9)"
       loading="lazy"
       style="max-width: 1400px; width: 100%; border: 1px solid #e5e7eb; border-radius: 8px; display:block; margin: 12px 0;">
</a>

<p style="font-size: 0.95em; color: #6b7280; margin-top: 6px;">
  Click any image to open it full size.
</p>

<p style="margin: 6px 0 18px 0;">
  <a href="#artifact-nav">↑ Back to navigation</a>
</p>

<hr style="margin: 24px 0; border: 0; border-top: 1px solid #e5e7eb;">

<a id="raid-log-risks-assumptions-issues-dependencies--full-page-screenshots"></a>
### RAID log (Risks, Assumptions, Issues, Dependencies) — full page (screenshots)
- Risks: what might go wrong
- Assumptions: what we’re relying on being true
- Issues: active problems to resolve
- Dependencies: external inputs/blockers

<!-- RAID log chunk 1 -->
<a href="/assets/img/jira-workflow/03-raid-01.png" target="_blank" rel="noopener">
  <img src="/assets/img/jira-workflow/03-raid-01.png"
       alt="RAID log — E-01 (chunk 1)"
       loading="lazy"
       style="max-width: 1400px; width: 100%; border: 1px solid #e5e7eb; border-radius: 8px; display:block; margin: 12px 0;">
</a>

<!-- RAID log chunk 2 -->
<a href="/assets/img/jira-workflow/03-raid-02.png" target="_blank" rel="noopener">
  <img src="/assets/img/jira-workflow/03-raid-02.png"
       alt="RAID log — E-01 (chunk 2)"
       loading="lazy"
       style="max-width: 1400px; width: 100%; border: 1px solid #e5e7eb; border-radius: 8px; display:block; margin: 12px 0;">
</a>

<!-- RAID log chunk 3 -->
<a href="/assets/img/jira-workflow/03-raid-03.png" target="_blank" rel="noopener">
  <img src="/assets/img/jira-workflow/03-raid-03.png"
       alt="RAID log — E-01 (chunk 3)"
       loading="lazy"
       style="max-width: 1400px; width: 100%; border: 1px solid #e5e7eb; border-radius: 8px; display:block; margin: 12px 0;">
</a>

<!-- RAID log chunk 4 -->
<a href="/assets/img/jira-workflow/03-raid-04.png" target="_blank" rel="noopener">
  <img src="/assets/img/jira-workflow/03-raid-04.png"
       alt="RAID log — E-01 (chunk 4)"
       loading="lazy"
       style="max-width: 1400px; width: 100%; border: 1px solid #e5e7eb; border-radius: 8px; display:block; margin: 12px 0;">
</a>

<p style="font-size: 0.95em; color: #6b7280; margin-top: 6px;">
  Click any image to open it full size.
</p>

<p style="margin: 6px 0 18px 0;">
  <a href="#artifact-nav">↑ Back to navigation</a>
</p>

<hr style="margin: 24px 0; border: 0; border-top: 1px solid #e5e7eb;">

<a id="journeys--full-page-screenshots"></a>
### User journeys — full page (screenshots)

<!-- User journeys chunk 1 -->
<a href="/assets/img/jira-workflow/04-journeys-01.png" target="_blank" rel="noopener">
  <img src="/assets/img/jira-workflow/04-journeys-01.png"
       alt="User journeys — E-01 (chunk 1)"
       loading="lazy"
       style="max-width: 1400px; width: 100%; border: 1px solid #e5e7eb; border-radius: 8px; display:block; margin: 12px 0;">
</a>

<!-- User journeys chunk 2 -->
<a href="/assets/img/jira-workflow/04-journeys-02.png" target="_blank" rel="noopener">
  <img src="/assets/img/jira-workflow/04-journeys-02.png"
       alt="User journeys — E-01 (chunk 2)"
       loading="lazy"
       style="max-width: 1400px; width: 100%; border: 1px solid #e5e7eb; border-radius: 8px; display:block; margin: 12px 0;">
</a>

<!-- User journeys chunk 3 -->
<a href="/assets/img/jira-workflow/04-journeys-03.png" target="_blank" rel="noopener">
  <img src="/assets/img/jira-workflow/04-journeys-03.png"
       alt="User journeys — E-01 (chunk 3)"
       loading="lazy"
       style="max-width: 1400px; width: 100%; border: 1px solid #e5e7eb; border-radius: 8px; display:block; margin: 12px 0;">
</a>

<!-- User journeys chunk 4 -->
<a href="/assets/img/jira-workflow/04-journeys-04.png" target="_blank" rel="noopener">
  <img src="/assets/img/jira-workflow/04-journeys-04.png"
       alt="User journeys — E-01 (chunk 4)"
       loading="lazy"
       style="max-width: 1400px; width: 100%; border: 1px solid #e5e7eb; border-radius: 8px; display:block; margin: 12px 0;">
</a>

<!-- User journeys chunk 5 -->
<a href="/assets/img/jira-workflow/04-journeys-05.png" target="_blank" rel="noopener">
  <img src="/assets/img/jira-workflow/04-journeys-05.png"
       alt="User journeys — E-01 (chunk 5)"
       loading="lazy"
       style="max-width: 1400px; width: 100%; border: 1px solid #e5e7eb; border-radius: 8px; display:block; margin: 12px 0;">
</a>

<!-- User journeys chunk 6 -->
<a href="/assets/img/jira-workflow/04-journeys-06.png" target="_blank" rel="noopener">
  <img src="/assets/img/jira-workflow/04-journeys-06.png"
       alt="User journeys — E-01 (chunk 6)"
       loading="lazy"
       style="max-width: 1400px; width: 100%; border: 1px solid #e5e7eb; border-radius: 8px; display:block; margin: 12px 0;">
</a>

<!-- User journeys chunk 7 -->
<a href="/assets/img/jira-workflow/04-journeys-07.png" target="_blank" rel="noopener">
  <img src="/assets/img/jira-workflow/04-journeys-07.png"
       alt="User journeys — E-01 (chunk 7)"
       loading="lazy"
       style="max-width: 1400px; width: 100%; border: 1px solid #e5e7eb; border-radius: 8px; display:block; margin: 12px 0;">
</a>

<!-- User journeys chunk 8 -->
<a href="/assets/img/jira-workflow/04-journeys-08.png" target="_blank" rel="noopener">
  <img src="/assets/img/jira-workflow/04-journeys-08.png"
       alt="User journeys — E-01 (chunk 8)"
       loading="lazy"
       style="max-width: 1400px; width: 100%; border: 1px solid #e5e7eb; border-radius: 8px; display:block; margin: 12px 0;">
</a>

<!-- User journeys chunk 9 -->
<a href="/assets/img/jira-workflow/04-journeys-09.png" target="_blank" rel="noopener">
  <img src="/assets/img/jira-workflow/04-journeys-09.png"
       alt="User journeys — E-01 (chunk 9)"
       loading="lazy"
       style="max-width: 1400px; width: 100%; border: 1px solid #e5e7eb; border-radius: 8px; display:block; margin: 12px 0;">
</a>

<!-- User journeys chunk 10 -->
<a href="/assets/img/jira-workflow/04-journeys-10.png" target="_blank" rel="noopener">
  <img src="/assets/img/jira-workflow/04-journeys-10.png"
       alt="User journeys — E-01 (chunk 10)"
       loading="lazy"
       style="max-width: 1400px; width: 100%; border: 1px solid #e5e7eb; border-radius: 8px; display:block; margin: 12px 0;">
</a>

<p style="font-size: 0.95em; color: #6b7280; margin-top: 6px;">
  Click any image to open it full size.
</p>

<p style="margin: 6px 0 18px 0;">
  <a href="#artifact-nav">↑ Back to navigation</a>
</p>

<hr style="margin: 24px 0; border: 0; border-top: 1px solid #e5e7eb;">

<a id="figma--full-page-screenshots"></a>
### Figma walkthrough (prototype + UX notes) — full page (screenshots)

<!-- Figma walkthrough chunk 1 -->
<a href="/assets/img/jira-workflow/05-figma-01.png" target="_blank" rel="noopener">
  <img src="/assets/img/jira-workflow/05-figma-01.png"
       alt="Figma walkthrough — E-01 (chunk 1)"
       loading="lazy"
       style="max-width: 1400px; width: 100%; border: 1px solid #e5e7eb; border-radius: 8px; display:block; margin: 12px 0;">
</a>

<!-- Figma walkthrough chunk 2 -->
<a href="/assets/img/jira-workflow/05-figma-02.png" target="_blank" rel="noopener">
  <img src="/assets/img/jira-workflow/05-figma-02.png"
       alt="Figma walkthrough — E-01 (chunk 2)"
       loading="lazy"
       style="max-width: 1400px; width: 100%; border: 1px solid #e5e7eb; border-radius: 8px; display:block; margin: 12px 0;">
</a>

<!-- Figma walkthrough chunk 3 -->
<a href="/assets/img/jira-workflow/05-figma-03.png" target="_blank" rel="noopener">
  <img src="/assets/img/jira-workflow/05-figma-03.png"
       alt="Figma walkthrough — E-01 (chunk 3)"
       loading="lazy"
       style="max-width: 1400px; width: 100%; border: 1px solid #e5e7eb; border-radius: 8px; display:block; margin: 12px 0;">
</a>

<p style="font-size: 0.95em; color: #6b7280; margin-top: 6px;">
  Click any image to open it full size.
</p>

<p style="margin: 6px 0 18px 0;">
  <a href="#artifact-nav">↑ Back to navigation</a>
</p>

<hr style="margin: 24px 0; border: 0; border-top: 1px solid #e5e7eb;">

<a id="epic-scrum-6"></a>
### Epic — SCRUM-6: E-01 Digital health app release (fictitious) (screenshots)

<!-- Epic chunk 1 -->
<a href="/assets/img/jira-workflow/07-epic-scrum-6-01.png" target="_blank" rel="noopener">
  <img src="/assets/img/jira-workflow/07-epic-scrum-6-01.png"
       alt="Epic SCRUM-6 — overview and description (chunk 1)"
       loading="lazy"
       style="max-width: 1400px; width: 100%; border: 1px solid #e5e7eb; border-radius: 8px; display:block; margin: 12px 0;">
</a>

<!-- Epic chunk 2 -->
<a href="/assets/img/jira-workflow/07-epic-scrum-6-02.png" target="_blank" rel="noopener">
  <img src="/assets/img/jira-workflow/07-epic-scrum-6-02.png"
       alt="Epic SCRUM-6 — child work items list (chunk 2)"
       loading="lazy"
       style="max-width: 1400px; width: 100%; border: 1px solid #e5e7eb; border-radius: 8px; display:block; margin: 12px 0;">
</a>

<!-- Epic chunk 3 -->
<a href="/assets/img/jira-workflow/07-epic-scrum-6-03.png" target="_blank" rel="noopener">
  <img src="/assets/img/jira-workflow/07-epic-scrum-6-03.png"
       alt="Epic SCRUM-6 — linked work items and details (chunk 3)"
       loading="lazy"
       style="max-width: 1400px; width: 100%; border: 1px solid #e5e7eb; border-radius: 8px; display:block; margin: 12px 0;">
</a>

<!-- Epic chunk 4 -->
<a href="/assets/img/jira-workflow/07-epic-scrum-6-04.png" target="_blank" rel="noopener">
  <img src="/assets/img/jira-workflow/07-epic-scrum-6-04.png"
       alt="Epic SCRUM-6 — fix version and metadata (chunk 4)"
       loading="lazy"
       style="max-width: 1400px; width: 100%; border: 1px solid #e5e7eb; border-radius: 8px; display:block; margin: 12px 0;">
</a>

<p style="font-size: 0.95em; color: #6b7280; margin-top: 6px;">
  Click any image to open it full size.
</p>

<p style="margin: 6px 0 18px 0;">
  <a href="#artifact-nav">↑ Back to navigation</a>
</p>

<hr style="margin: 24px 0; border: 0; border-top: 1px solid #e5e7eb;">

<a id="feature-scrum-5"></a>
### Feature — SCRUM-5: F-01 end-to-end delivery (screenshots)

<!-- Feature chunk 1 -->
<a href="/assets/img/jira-workflow/08-feature-scrum-5-01.png" target="_blank" rel="noopener">
  <img src="/assets/img/jira-workflow/08-feature-scrum-5-01.png"
       alt="Feature SCRUM-5 — header and overview (chunk 1)"
       loading="lazy"
       style="max-width: 1400px; width: 100%; border: 1px solid #e5e7eb; border-radius: 8px; display:block; margin: 12px 0;">
</a>

<!-- Feature chunk 2 -->
<a href="/assets/img/jira-workflow/08-feature-scrum-5-02.png" target="_blank" rel="noopener">
  <img src="/assets/img/jira-workflow/08-feature-scrum-5-02.png"
       alt="Feature SCRUM-5 — parent and details (chunk 2)"
       loading="lazy"
       style="max-width: 1400px; width: 100%; border: 1px solid #e5e7eb; border-radius: 8px; display:block; margin: 12px 0;">
</a>

<!-- Feature chunk 3 -->
<a href="/assets/img/jira-workflow/08-feature-scrum-5-03.png" target="_blank" rel="noopener">
  <img src="/assets/img/jira-workflow/08-feature-scrum-5-03.png"
       alt="Feature SCRUM-5 — fix version and metadata (chunk 3)"
       loading="lazy"
       style="max-width: 1400px; width: 100%; border: 1px solid #e5e7eb; border-radius: 8px; display:block; margin: 12px 0;">
</a>

<p style="font-size: 0.95em; color: #6b7280; margin-top: 6px;">
  Click any image to open it full size.
</p>

<p style="margin: 6px 0 18px 0;">
  <a href="#artifact-nav">↑ Back to navigation</a>
</p>

<hr style="margin: 24px 0; border: 0; border-top: 1px solid #e5e7eb;">

<a id="sprint0-backlog"></a>
### Sprint 0 — Backlog view (overview + close-ups)

<!-- Wide overview (scrollable container so it stays readable) -->
<div style="overflow-x:auto; -webkit-overflow-scrolling:touch; border:1px solid #e5e7eb; border-radius:8px; padding:8px; margin:12px 0;">
  <a href="/assets/img/jira-workflow/06-sprint0-backlog-wide.png" target="_blank" rel="noopener">
    <img src="/assets/img/jira-workflow/06-sprint0-backlog-wide.png"
         alt="Jira backlog — Sprint 0 (wide overview)"
         loading="lazy"
         style="width:1800px; max-width:none; display:block;">
  </a>
</div>

<p style="font-size:0.95em; color:#6b7280; margin-top:6px;">
  Scroll horizontally to read. Click the image to open full size.
</p>

<!-- Close-up crops (readable without zooming) -->
<h4 style="margin-top:18px;">Close-up — items & summary (left)</h4>
<a href="/assets/img/jira-workflow/06-sprint0-backlog-left.png" target="_blank" rel="noopener">
  <img src="/assets/img/jira-workflow/06-sprint0-backlog-left.png"
       alt="Jira backlog — Sprint 0 (close-up: items and summary)"
       loading="lazy"
       style="max-width:1400px; width:100%; border:1px solid #e5e7eb; border-radius:8px; display:block; margin:12px 0;">
</a>

<h4 style="margin-top:18px;">Close-up — status & estimates (right)</h4>
<a href="/assets/img/jira-workflow/06-sprint0-backlog-right.png" target="_blank" rel="noopener">
  <img src="/assets/img/jira-workflow/06-sprint0-backlog-right.png"
       alt="Jira backlog — Sprint 0 (close-up: status and estimates)"
       loading="lazy"
       style="max-width:1400px; width:100%; border:1px solid #e5e7eb; border-radius:8px; display:block; margin:12px 0;">
</a>

<p style="font-size:0.95em; color:#6b7280; margin-top:6px;">
  Click any image to open it full size.
</p>

<p style="margin:6px 0 18px 0;">
  <a href="#artifact-nav">↑ Back to navigation</a>
</p>

<hr style="margin:24px 0; border:0; border-top:1px solid #e5e7eb;">

<a id="sprint0-scrum-7"></a>
### Sprint 0 — S-01 (SCRUM-7): Define scope + requirements (BRD/FRD) (screenshots)

<!-- Chunk 1 -->
<a href="/assets/img/jira-workflow/09-sprint0-scrum-7-01.png" target="_blank" rel="noopener">
  <img src="/assets/img/jira-workflow/09-sprint0-scrum-7-01.png"
       alt="Sprint 0 story SCRUM-7 — header and description (chunk 1)"
       loading="lazy"
       style="max-width: 1400px; width: 100%;
              border: 1px solid #e5e7eb; border-radius: 8px;
              display:block; margin: 12px 0;">
</a>

<!-- Chunk 2 -->
<a href="/assets/img/jira-workflow/09-sprint0-scrum-7-02.png" target="_blank" rel="noopener">
  <img src="/assets/img/jira-workflow/09-sprint0-scrum-7-02.png"
       alt="Sprint 0 story SCRUM-7 — acceptance criteria (chunk 2)"
       loading="lazy"
       style="max-width: 1400px; width: 100%;
              border: 1px solid #e5e7eb; border-radius: 8px;
              display:block; margin: 12px 0;">
</a>

<!-- Chunk 3 -->
<a href="/assets/img/jira-workflow/09-sprint0-scrum-7-03.png" target="_blank" rel="noopener">
  <img src="/assets/img/jira-workflow/09-sprint0-scrum-7-03.png"
       alt="Sprint 0 story SCRUM-7 — subtasks and linked artifacts (chunk 3)"
       loading="lazy"
       style="max-width: 1400px; width: 100%;
              border: 1px solid #e5e7eb; border-radius: 8px;
              display:block; margin: 12px 0;">
</a>

<p style="font-size: 0.95em; color: #6b7280; margin-top: 6px;">
  Click any image to open it full size.
</p>

<p style="margin: 6px 0 18px 0;">
  <a href="#artifact-nav">↑ Back to navigation</a>
</p>

<hr style="margin: 24px 0; border: 0; border-top: 1px solid #e5e7eb;">

<a id="sprint0-scrum-8"></a>
### Sprint 0 — S-02 (SCRUM-8): Requirements & user journeys (patient + clinician flows) (screenshots)

<!-- Chunk 1 -->
<a href="/assets/img/jira-workflow/09-sprint0-scrum-8-01.png" target="_blank" rel="noopener">
  <img src="/assets/img/jira-workflow/09-sprint0-scrum-8-01.png"
       alt="Sprint 0 story SCRUM-8 — header and description (chunk 1)"
       loading="lazy"
       style="max-width: 1400px; width: 100%;
              border: 1px solid #e5e7eb; border-radius: 8px;
              display:block; margin: 12px 0;">
</a>

<!-- Chunk 2 -->
<a href="/assets/img/jira-workflow/09-sprint0-scrum-8-02.png" target="_blank" rel="noopener">
  <img src="/assets/img/jira-workflow/09-sprint0-scrum-8-02.png"
       alt="Sprint 0 story SCRUM-8 — acceptance criteria (chunk 2)"
       loading="lazy"
       style="max-width: 1400px; width: 100%;
              border: 1px solid #e5e7eb; border-radius: 8px;
              display:block; margin: 12px 0;">
</a>

<!-- Chunk 3 -->
<a href="/assets/img/jira-workflow/09-sprint0-scrum-8-03.png" target="_blank" rel="noopener">
  <img src="/assets/img/jira-workflow/09-sprint0-scrum-8-03.png"
       alt="Sprint 0 story SCRUM-8 — subtasks and metadata (chunk 3)"
       loading="lazy"
       style="max-width: 1400px; width: 100%;
              border: 1px solid #e5e7eb; border-radius: 8px;
              display:block; margin: 12px 0;">
</a>

<p style="font-size: 0.95em; color: #6b7280; margin-top: 6px;">
  Click any image to open it full size.
</p>

<p style="margin: 6px 0 18px 0;">
  <a href="#artifact-nav">↑ Back to navigation</a>
</p>

<hr style="margin: 24px 0; border: 0; border-top: 1px solid #e5e7eb;">

<a id="sprint0-scrum-9"></a>
### Sprint 0 — S-03 (SCRUM-9): UX/UI wireframes + clickable prototype (Figma) (screenshots)

<!-- Chunk 1 -->
<a href="/assets/img/jira-workflow/09-sprint0-scrum-9-01.png" target="_blank" rel="noopener">
  <img src="/assets/img/jira-workflow/09-sprint0-scrum-9-01.png"
       alt="Sprint 0 story SCRUM-9 — header and description (chunk 1)"
       loading="lazy"
       style="max-width: 1400px; width: 100%;
              border: 1px solid #e5e7eb; border-radius: 8px;
              display:block; margin: 12px 0;">
</a>

<!-- Chunk 2 -->
<a href="/assets/img/jira-workflow/09-sprint0-scrum-9-02.png" target="_blank" rel="noopener">
  <img src="/assets/img/jira-workflow/09-sprint0-scrum-9-02.png"
       alt="Sprint 0 story SCRUM-9 — scope, deliverables, and acceptance criteria (chunk 2)"
       loading="lazy"
       style="max-width: 1400px; width: 100%;
              border: 1px solid #e5e7eb; border-radius: 8px;
              display:block; margin: 12px 0;">
</a>

<!-- Chunk 3 -->
<a href="/assets/img/jira-workflow/09-sprint0-scrum-9-03.png" target="_blank" rel="noopener">
  <img src="/assets/img/jira-workflow/09-sprint0-scrum-9-03.png"
       alt="Sprint 0 story SCRUM-9 — definition of done, notes, and subtasks list (chunk 3)"
       loading="lazy"
       style="max-width: 1400px; width: 100%;
              border: 1px solid #e5e7eb; border-radius: 8px;
              display:block; margin: 12px 0;">
</a>

<!-- Chunk 4 -->
<a href="/assets/img/jira-workflow/09-sprint0-scrum-9-04.png" target="_blank" rel="noopener">
  <img src="/assets/img/jira-workflow/09-sprint0-scrum-9-04.png"
       alt="Sprint 0 story SCRUM-9 — linked work items and Confluence content (chunk 4)"
       loading="lazy"
       style="max-width: 1400px; width: 100%;
              border: 1px solid #e5e7eb; border-radius: 8px;
              display:block; margin: 12px 0;">
</a>

<!-- Chunk 5 -->
<a href="/assets/img/jira-workflow/09-sprint0-scrum-9-05.png" target="_blank" rel="noopener">
  <img src="/assets/img/jira-workflow/09-sprint0-scrum-9-05.png"
       alt="Sprint 0 story SCRUM-9 — details and metadata (chunk 5)"
       loading="lazy"
       style="max-width: 1400px; width: 100%;
              border: 1px solid #e5e7eb; border-radius: 8px;
              display:block; margin: 12px 0;">
</a>

<p style="font-size: 0.95em; color: #6b7280; margin-top: 6px;">
  Click any image to open it full size.
</p>

<p style="margin: 6px 0 18px 0;">
  <a href="#artifact-nav">↑ Back to navigation</a>
</p>

<hr style="margin: 24px 0; border: 0; border-top: 1px solid #e5e7eb;">

<a id="sprint1-backlog"></a>
### Sprint 1 — Backlog view (overview + close-ups)

<!-- Wide overview (scrollable container so it stays readable) -->
<div style="overflow-x:auto; -webkit-overflow-scrolling:touch; border:1px solid #e5e7eb; border-radius:8px; padding:8px; margin:12px 0;">
  <a href="/assets/img/jira-workflow/10-sprint1-backlog-wide.png" target="_blank" rel="noopener">
    <img src="/assets/img/jira-workflow/10-sprint1-backlog-wide.png"
         alt="Jira backlog — Sprint 1 (wide overview)"
         loading="lazy"
         style="width:1800px; max-width:none; display:block;">
  </a>
</div>

<p style="font-size:0.95em; color:#6b7280; margin-top:6px;">
  Scroll horizontally to read. Click the image to open full size.
</p>

<!-- Close-up crops (readable without zooming) -->
<h4 style="margin-top:18px;">Close-up — items list (left)</h4>
<a href="/assets/img/jira-workflow/10-sprint1-backlog-left.png" target="_blank" rel="noopener">
  <img src="/assets/img/jira-workflow/10-sprint1-backlog-left.png"
       alt="Jira backlog — Sprint 1 (close-up: work items list)"
       loading="lazy"
       style="max-width:1400px; width:100%; border:1px solid #e5e7eb; border-radius:8px; display:block; margin:12px 0;">
</a>

<h4 style="margin-top:18px;">Close-up — statuses & estimates (right)</h4>
<a href="/assets/img/jira-workflow/10-sprint1-backlog-right.png" target="_blank" rel="noopener">
  <img src="/assets/img/jira-workflow/10-sprint1-backlog-right.png"
       alt="Jira backlog — Sprint 1 (close-up: statuses and estimates)"
       loading="lazy"
       style="max-width:1400px; width:100%; border:1px solid #e5e7eb; border-radius:8px; display:block; margin:12px 0;">
</a>

<p style="font-size:0.95em; color:#6b7280; margin-top:6px;">
  Click any image to open it full size.
</p>

<p style="margin:6px 0 18px 0;">
  <a href="#artifact-nav">↑ Back to navigation</a>
</p>

<hr style="margin:24px 0; border:0; border-top:1px solid #e5e7eb;">

<a id="sprint1-scrum-10"></a>
### Sprint 1 — S-04 (SCRUM-10): On-device AI wellness estimates integration (no media stored) (screenshots)

<!-- Chunk 1 -->
<a href="/assets/img/jira-workflow/10-sprint1-scrum-10-01.png" target="_blank" rel="noopener">
  <img src="/assets/img/jira-workflow/10-sprint1-scrum-10-01.png"
       alt="Sprint 1 story SCRUM-10 — header, description, scope/notes, and acceptance criteria (chunk 1)"
       loading="lazy"
       style="max-width: 1400px; width: 100%;
              border: 1px solid #e5e7eb; border-radius: 8px;
              display:block; margin: 12px 0;">
</a>

<!-- Chunk 2 -->
<a href="/assets/img/jira-workflow/10-sprint1-scrum-10-02.png" target="_blank" rel="noopener">
  <img src="/assets/img/jira-workflow/10-sprint1-scrum-10-02.png"
       alt="Sprint 1 story SCRUM-10 — subtasks list and linked work items (chunk 2)"
       loading="lazy"
       style="max-width: 1400px; width: 100%;
              border: 1px solid #e5e7eb; border-radius: 8px;
              display:block; margin: 12px 0;">
</a>

<!-- Chunk 3 -->
<a href="/assets/img/jira-workflow/10-sprint1-scrum-10-03.png" target="_blank" rel="noopener">
  <img src="/assets/img/jira-workflow/10-sprint1-scrum-10-03.png"
       alt="Sprint 1 story SCRUM-10 — pinned fields, details, sprint, estimate, and fix version (chunk 3)"
       loading="lazy"
       style="max-width: 1400px; width: 100%;
              border: 1px solid #e5e7eb; border-radius: 8px;
              display:block; margin: 12px 0;">
</a>

<p style="font-size: 0.95em; color: #6b7280; margin-top: 6px;">
  Click any image to open it full size.
</p>

<p style="margin: 6px 0 18px 0;">
  <a href="#artifact-nav">↑ Back to navigation</a>
</p>

<hr style="margin: 24px 0; border: 0; border-top: 1px solid #e5e7eb;">

<a id="sprint1-scrum-11"></a>
### Sprint 1 — S-05 (SCRUM-11): Bluetooth device ingestion + data integrity checks (screenshots)

<!-- Chunk 1 -->
<a href="/assets/img/jira-workflow/10-sprint1-scrum-11-01.png" target="_blank" rel="noopener">
  <img src="/assets/img/jira-workflow/10-sprint1-scrum-11-01.png"
       alt="Sprint 1 story SCRUM-11 — header and description (chunk 1)"
       loading="lazy"
       style="max-width: 1400px; width: 100%;
              border: 1px solid #e5e7eb; border-radius: 8px;
              display:block; margin: 12px 0;">
</a>

<!-- Chunk 2 -->
<a href="/assets/img/jira-workflow/10-sprint1-scrum-11-02.png" target="_blank" rel="noopener">
  <img src="/assets/img/jira-workflow/10-sprint1-scrum-11-02.png"
       alt="Sprint 1 story SCRUM-11 — acceptance criteria and notes/evidence (chunk 2)"
       loading="lazy"
       style="max-width: 1400px; width: 100%;
              border: 1px solid #e5e7eb; border-radius: 8px;
              display:block; margin: 12px 0;">
</a>

<!-- Chunk 3 -->
<a href="/assets/img/jira-workflow/10-sprint1-scrum-11-03.png" target="_blank" rel="noopener">
  <img src="/assets/img/jira-workflow/10-sprint1-scrum-11-03.png"
       alt="Sprint 1 story SCRUM-11 — subtasks list (chunk 3)"
       loading="lazy"
       style="max-width: 1400px; width: 100%;
              border: 1px solid #e5e7eb; border-radius: 8px;
              display:block; margin: 12px 0;">
</a>

<!-- Chunk 4 -->
<a href="/assets/img/jira-workflow/10-sprint1-scrum-11-04.png" target="_blank" rel="noopener">
  <img src="/assets/img/jira-workflow/10-sprint1-scrum-11-04.png"
       alt="Sprint 1 story SCRUM-11 — blocked-by link, linked work items, and Confluence content (chunk 4)"
       loading="lazy"
       style="max-width: 1400px; width: 100%;
              border: 1px solid #e5e7eb; border-radius: 8px;
              display:block; margin: 12px 0;">
</a>

<!-- Chunk 5 -->
<a href="/assets/img/jira-workflow/10-sprint1-scrum-11-05.png" target="_blank" rel="noopener">
  <img src="/assets/img/jira-workflow/10-sprint1-scrum-11-05.png"
       alt="Sprint 1 story SCRUM-11 — pinned fields and details (chunk 5)"
       loading="lazy"
       style="max-width: 1400px; width: 100%;
              border: 1px solid #e5e7eb; border-radius: 8px;
              display:block; margin: 12px 0;">
</a>

<p style="font-size: 0.95em; color: #6b7280; margin-top: 6px;">
  Click any image to open it full size.
</p>

<p style="margin: 6px 0 18px 0;">
  <a href="#artifact-nav">↑ Back to navigation</a>
</p>

<hr style="margin: 24px 0; border: 0; border-top: 1px solid #e5e7eb;">

<a id="sprint1-scrum-12"></a>
### Sprint 1 — S-06 (SCRUM-12): Secure backend + APIs (auth, encryption, audit logging) (screenshots)

<!-- Chunk 1 -->
<a href="/assets/img/jira-workflow/10-sprint1-scrum-12-01.png" target="_blank" rel="noopener">
  <img src="/assets/img/jira-workflow/10-sprint1-scrum-12-01.png"
       alt="Sprint 1 story SCRUM-12 — header, description, acceptance criteria, and notes/evidence (chunk 1)"
       loading="lazy"
       style="max-width: 1400px; width: 100%;
              border: 1px solid #e5e7eb; border-radius: 8px;
              display:block; margin: 12px 0;">
</a>

<!-- Chunk 2 -->
<a href="/assets/img/jira-workflow/10-sprint1-scrum-12-02.png" target="_blank" rel="noopener">
  <img src="/assets/img/jira-workflow/10-sprint1-scrum-12-02.png"
       alt="Sprint 1 story SCRUM-12 — subtasks list (chunk 2)"
       loading="lazy"
       style="max-width: 1400px; width: 100%;
              border: 1px solid #e5e7eb; border-radius: 8px;
              display:block; margin: 12px 0;">
</a>

<!-- Chunk 3 -->
<a href="/assets/img/jira-workflow/10-sprint1-scrum-12-03.png" target="_blank" rel="noopener">
  <img src="/assets/img/jira-workflow/10-sprint1-scrum-12-03.png"
       alt="Sprint 1 story SCRUM-12 — linked work items and Confluence content (chunk 3)"
       loading="lazy"
       style="max-width: 1400px; width: 100%;
              border: 1px solid #e5e7eb; border-radius: 8px;
              display:block; margin: 12px 0;">
</a>

<!-- Chunk 4 -->
<a href="/assets/img/jira-workflow/10-sprint1-scrum-12-04.png" target="_blank" rel="noopener">
  <img src="/assets/img/jira-workflow/10-sprint1-scrum-12-04.png"
       alt="Sprint 1 story SCRUM-12 — details and metadata (chunk 4)"
       loading="lazy"
       style="max-width: 1400px; width: 100%;
              border: 1px solid #e5e7eb; border-radius: 8px;
              display:block; margin: 12px 0;">
</a>

<p style="font-size: 0.95em; color: #6b7280; margin-top: 6px;">
  Click any image to open it full size.
</p>

<p style="margin: 6px 0 18px 0;">
  <a href="#artifact-nav">↑ Back to navigation</a>
</p>

<hr style="margin: 24px 0; border: 0; border-top: 1px solid #e5e7eb;">

<a id="sprint1-scrum-13"></a>
### Sprint 1 — S-07 (SCRUM-13): Privacy & security controls (consent, retention, deletion) (screenshots)

<!-- Chunk 1 -->
<a href="/assets/img/jira-workflow/10-sprint1-scrum-13-01.png" target="_blank" rel="noopener">
  <img src="/assets/img/jira-workflow/10-sprint1-scrum-13-01.png"
       alt="Sprint 1 story SCRUM-13 — header, description, and acceptance criteria (chunk 1)"
       loading="lazy"
       style="max-width: 1400px; width: 100%;
              border: 1px solid #e5e7eb; border-radius: 8px;
              display:block; margin: 12px 0;">
</a>

<!-- Chunk 2 -->
<a href="/assets/img/jira-workflow/10-sprint1-scrum-13-02.png" target="_blank" rel="noopener">
  <img src="/assets/img/jira-workflow/10-sprint1-scrum-13-02.png"
       alt="Sprint 1 story SCRUM-13 — subtasks list (chunk 2)"
       loading="lazy"
       style="max-width: 1400px; width: 100%;
              border: 1px solid #e5e7eb; border-radius: 8px;
              display:block; margin: 12px 0;">
</a>

<!-- Chunk 3 -->
<a href="/assets/img/jira-workflow/10-sprint1-scrum-13-03.png" target="_blank" rel="noopener">
  <img src="/assets/img/jira-workflow/10-sprint1-scrum-13-03.png"
       alt="Sprint 1 story SCRUM-13 — linked work items and Confluence content (chunk 3)"
       loading="lazy"
       style="max-width: 1400px; width: 100%;
              border: 1px solid #e5e7eb; border-radius: 8px;
              display:block; margin: 12px 0;">
</a>

<!-- Chunk 4 -->
<a href="/assets/img/jira-workflow/10-sprint1-scrum-13-04.png" target="_blank" rel="noopener">
  <img src="/assets/img/jira-workflow/10-sprint1-scrum-13-04.png"
       alt="Sprint 1 story SCRUM-13 — details, sprint, estimate, and fix version (chunk 4)"
       loading="lazy"
       style="max-width: 1400px; width: 100%;
              border: 1px solid #e5e7eb; border-radius: 8px;
              display:block; margin: 12px 0;">
</a>

<p style="font-size: 0.95em; color: #6b7280; margin-top: 6px;">
  Click any image to open it full size.
</p>

<p style="margin: 6px 0 18px 0;">
  <a href="#artifact-nav">↑ Back to navigation</a>
</p>

<hr style="margin: 24px 0; border: 0; border-top: 1px solid #e5e7eb;">

<a id="sprint1-scrum-14"></a>
### Sprint 1 — S-08 (SCRUM-14): Test plan + SIT (integration + regression) (screenshots)

<!-- Chunk 1 -->
<a href="/assets/img/jira-workflow/10-sprint1-scrum-14-01.png" target="_blank" rel="noopener">
  <img src="/assets/img/jira-workflow/10-sprint1-scrum-14-01.png"
       alt="Sprint 1 story SCRUM-14 — header and description (chunk 1)"
       loading="lazy"
       style="max-width: 1400px; width: 100%;
              border: 1px solid #e5e7eb; border-radius: 8px;
              display:block; margin: 12px 0;">
</a>

<!-- Chunk 2 -->
<a href="/assets/img/jira-workflow/10-sprint1-scrum-14-02.png" target="_blank" rel="noopener">
  <img src="/assets/img/jira-workflow/10-sprint1-scrum-14-02.png"
       alt="Sprint 1 story SCRUM-14 — acceptance criteria continuation (chunk 2)"
       loading="lazy"
       style="max-width: 1400px; width: 100%;
              border: 1px solid #e5e7eb; border-radius: 8px;
              display:block; margin: 12px 0;">
</a>

<!-- Chunk 3 -->
<a href="/assets/img/jira-workflow/10-sprint1-scrum-14-03.png" target="_blank" rel="noopener">
  <img src="/assets/img/jira-workflow/10-sprint1-scrum-14-03.png"
       alt="Sprint 1 story SCRUM-14 — subtasks list (chunk 3)"
       loading="lazy"
       style="max-width: 1400px; width: 100%;
              border: 1px solid #e5e7eb; border-radius: 8px;
              display:block; margin: 12px 0;">
</a>

<!-- Chunk 4 -->
<a href="/assets/img/jira-workflow/10-sprint1-scrum-14-04.png" target="_blank" rel="noopener">
  <img src="/assets/img/jira-workflow/10-sprint1-scrum-14-04.png"
       alt="Sprint 1 story SCRUM-14 — linked work items and pinned fields (chunk 4)"
       loading="lazy"
       style="max-width: 1400px; width: 100%;
              border: 1px solid #e5e7eb; border-radius: 8px;
              display:block; margin: 12px 0;">
</a>

<!-- Chunk 5 -->
<a href="/assets/img/jira-workflow/10-sprint1-scrum-14-05.png" target="_blank" rel="noopener">
  <img src="/assets/img/jira-workflow/10-sprint1-scrum-14-05.png"
       alt="Sprint 1 story SCRUM-14 — details, sprint, estimate, and fix version (chunk 5)"
       loading="lazy"
       style="max-width: 1400px; width: 100%;
              border: 1px solid #e5e7eb; border-radius: 8px;
              display:block; margin: 12px 0;">
</a>

<p style="font-size: 0.95em; color: #6b7280; margin-top: 6px;">
  Click any image to open it full size.
</p>

<p style="margin: 6px 0 18px 0;">
  <a href="#artifact-nav">↑ Back to navigation</a>
</p>

<hr style="margin: 24px 0; border: 0; border-top: 1px solid #e5e7eb;">

<a id="sprint1-scrum-15"></a>
### Sprint 1 — S-09 (SCRUM-15): UAT plan + sign-off pack (release readiness) (screenshots)

<!-- Chunk 1 -->
<a href="/assets/img/jira-workflow/10-sprint1-scrum-15-01.png" target="_blank" rel="noopener">
  <img src="/assets/img/jira-workflow/10-sprint1-scrum-15-01.png"
       alt="Sprint 1 story SCRUM-15 — header, description, and acceptance criteria (chunk 1)"
       loading="lazy"
       style="max-width: 1400px; width: 100%;
              border: 1px solid #e5e7eb; border-radius: 8px;
              display:block; margin: 12px 0;">
</a>

<!-- Chunk 2 -->
<a href="/assets/img/jira-workflow/10-sprint1-scrum-15-02.png" target="_blank" rel="noopener">
  <img src="/assets/img/jira-workflow/10-sprint1-scrum-15-02.png"
       alt="Sprint 1 story SCRUM-15 — notes and scope boundaries (chunk 2)"
       loading="lazy"
       style="max-width: 1400px; width: 100%;
              border: 1px solid #e5e7eb; border-radius: 8px;
              display:block; margin: 12px 0;">
</a>

<!-- Chunk 3 -->
<a href="/assets/img/jira-workflow/10-sprint1-scrum-15-03.png" target="_blank" rel="noopener">
  <img src="/assets/img/jira-workflow/10-sprint1-scrum-15-03.png"
       alt="Sprint 1 story SCRUM-15 — subtasks list (chunk 3)"
       loading="lazy"
       style="max-width: 1400px; width: 100%;
              border: 1px solid #e5e7eb; border-radius: 8px;
              display:block; margin: 12px 0;">
</a>

<!-- Chunk 4 -->
<a href="/assets/img/jira-workflow/10-sprint1-scrum-15-04.png" target="_blank" rel="noopener">
  <img src="/assets/img/jira-workflow/10-sprint1-scrum-15-04.png"
       alt="Sprint 1 story SCRUM-15 — linked work items and pinned fields (chunk 4)"
       loading="lazy"
       style="max-width: 1400px; width: 100%;
              border: 1px solid #e5e7eb; border-radius: 8px;
              display:block; margin: 12px 0;">
</a>

<!-- Chunk 5 -->
<a href="/assets/img/jira-workflow/10-sprint1-scrum-15-05.png" target="_blank" rel="noopener">
  <img src="/assets/img/jira-workflow/10-sprint1-scrum-15-05.png"
       alt="Sprint 1 story SCRUM-15 — details, labels, sprint, estimate, and fix version (chunk 5)"
       loading="lazy"
       style="max-width: 1400px; width: 100%;
              border: 1px solid #e5e7eb; border-radius: 8px;
              display:block; margin: 12px 0;">
</a>

<p style="font-size: 0.95em; color: #6b7280; margin-top: 6px;">
  Click any image to open it full size.
</p>

<p style="margin: 6px 0 18px 0;">
  <a href="#artifact-nav">↑ Back to navigation</a>
</p>

<hr style="margin: 24px 0; border: 0; border-top: 1px solid #e5e7eb;">

<a id="sprint1-scrum-16"></a>
### Sprint 1 — S-10 (SCRUM-16): Release checklist + monitoring + hypercare plan (screenshots)

<!-- Chunk 1 -->
<a href="/assets/img/jira-workflow/10-sprint1-scrum-16-01.png" target="_blank" rel="noopener">
  <img src="/assets/img/jira-workflow/10-sprint1-scrum-16-01.png"
       alt="Sprint 1 story SCRUM-16 — header and description (chunk 1)"
       loading="lazy"
       style="max-width: 1400px; width: 100%;
              border: 1px solid #e5e7eb; border-radius: 8px;
              display:block; margin: 12px 0;">
</a>

<!-- Chunk 2 -->
<a href="/assets/img/jira-workflow/10-sprint1-scrum-16-02.png" target="_blank" rel="noopener">
  <img src="/assets/img/jira-workflow/10-sprint1-scrum-16-02.png"
       alt="Sprint 1 story SCRUM-16 — acceptance criteria continuation and definition of done (chunk 2)"
       loading="lazy"
       style="max-width: 1400px; width: 100%;
              border: 1px solid #e5e7eb; border-radius: 8px;
              display:block; margin: 12px 0;">
</a>

<!-- Chunk 3 -->
<a href="/assets/img/jira-workflow/10-sprint1-scrum-16-03.png" target="_blank" rel="noopener">
  <img src="/assets/img/jira-workflow/10-sprint1-scrum-16-03.png"
       alt="Sprint 1 story SCRUM-16 — subtasks list (chunk 3)"
       loading="lazy"
       style="max-width: 1400px; width: 100%;
              border: 1px solid #e5e7eb; border-radius: 8px;
              display:block; margin: 12px 0;">
</a>

<!-- Chunk 4 -->
<a href="/assets/img/jira-workflow/10-sprint1-scrum-16-04.png" target="_blank" rel="noopener">
  <img src="/assets/img/jira-workflow/10-sprint1-scrum-16-04.png"
       alt="Sprint 1 story SCRUM-16 — linked work items and Confluence content (chunk 4)"
       loading="lazy"
       style="max-width: 1400px; width: 100%;
              border: 1px solid #e5e7eb; border-radius: 8px;
              display:block; margin: 12px 0;">
</a>

<!-- Chunk 5 -->
<a href="/assets/img/jira-workflow/10-sprint1-scrum-16-05.png" target="_blank" rel="noopener">
  <img src="/assets/img/jira-workflow/10-sprint1-scrum-16-05.png"
       alt="Sprint 1 story SCRUM-16 — details, labels, sprint, estimate, and fix version (chunk 5)"
       loading="lazy"
       style="max-width: 1400px; width: 100%;
              border: 1px solid #e5e7eb; border-radius: 8px;
              display:block; margin: 12px 0;">
</a>

<p style="font-size: 0.95em; color: #6b7280; margin-top: 6px;">
  Click any image to open it full size.
</p>

<p style="margin: 6px 0 18px 0;">
  <a href="#artifact-nav">↑ Back to navigation</a>
</p>

<hr style="margin: 24px 0; border: 0; border-top: 1px solid #e5e7eb;">

### EPIC: Contactless vitals session + history (v1.8.0)
**Purpose:** Deliver a privacy-safe measurement flow and history entry with clear provenance.

**Key outcomes**
- User can run a measurement session
- Results saved as numeric values (where applicable), with provenance label
- No camera media stored or uploaded
- Release is gated with SIT/UAT and a clear release checklist

**Links**
- Depends on: backend endpoint availability, UX copy approved, security review notes
- Produces: release notes, test evidence, sign-off record

📸 **Screenshot placeholder:** Epic view (summary + description + acceptance criteria)  
📸 **Screenshot placeholder:** Epic issue links + children list

---

## 2) Discovery / Validation Spikes (timeboxed)

### SPIKE: Validate measurement assumptions + failure modes
- Document expected failure cases (motion, lighting, unsupported device)
- Define “cannot estimate” behavior and user messaging
- Identify how we record provenance (AI vs Device vs Manual)

📸 Screenshot placeholder: Spike ticket with deliverables checklist

### SPIKE: Privacy review (DPIA-style notes)
- Data flow mapping: camera frames processed on-device, no storage
- Retention decision: numeric results stored (or session-only, depending on platform)
- User controls: delete measurement, account deletion implications
- Sub-processors (if applicable) documented

📸 Screenshot placeholder: Spike ticket with data flow notes section

---

## 3) Requirements / Stories

### STORY: Measurement session UI (mobile)
**Acceptance criteria**
- Start/stop session flow
- Clear user guidance (positioning, stillness, lighting)
- Explicit messaging: not diagnostic / not medical advice
- “Cannot estimate” shown with reason category (e.g., motion too high)

📸 Screenshot placeholder: Story ticket with acceptance criteria

### STORY: Save history entry with provenance label
**Acceptance criteria**
- History entry stores numeric values and timestamp
- Source label stored and displayed: AI / Device / Manual
- Deleting an item removes it from history (and sync behavior if applicable)

📸 Screenshot placeholder: Story ticket showing fields + labels + version

### STORY: Backend endpoint for history sync (if backend exists)
**Acceptance criteria**
- Authenticated endpoint for write/read history item
- Validation rules and schema versioning
- Audit-friendly logging (no sensitive payload logging)

📸 Screenshot placeholder: Backend story ticket

---

## 4) Engineering Tasks (implementation)

### TASK: iOS implementation
- Implement session screen
- Implement measurement state machine
- Implement history save
- Unit tests for core logic

📸 Screenshot placeholder: Task with sub-tasks

### TASK: Android implementation
- Implement session screen
- Implement on-device processing boundary (no media upload)
- Implement history save + sync label behavior

📸 Screenshot placeholder: Task with sub-tasks

### TASK: Backend implementation 
- Create endpoint
- Add schema validation
- Add rate limiting / abuse guardrails

📸 Screenshot placeholder: Task with checklist

---

## 5) Quality gates (SIT/UAT) — tickets that prove “ready”

### STORY: SIT test execution (QA)
**Includes**
- Test plan checklist (happy path + failures)
- Device/OS coverage list
- Evidence capture instructions (what we keep)

📸 Screenshot placeholder: SIT ticket with test checklist

### STORY: UAT sign-off (Product/Business)
**Includes**
- UAT script
- Sign-off checkbox or comment template
- Known limitations documented

📸 Screenshot placeholder: UAT ticket with sign-off template

---

## 6) Release governance

### TASK: Release readiness checklist (v1.8.0)
Checklist:
- Scope frozen / change log updated
- SIT passed (link to SIT ticket)
- UAT signed (link to UAT ticket)
- Privacy/security notes completed (link to spike)
- Release notes drafted
- Rollback plan documented
- Hypercare owner assigned

📸 Screenshot placeholder: Release checklist ticket

### RELEASE: Version `v1.8.0`
- Included issues list
- Release date
- Notes + link to known issues

📸 Screenshot placeholder: Jira Release / FixVersion screen

---

## 7) Post-release / Hypercare / Closure

### TASK: Hypercare monitoring (first 72 hours)
- Monitor crash/error signals (if applicable)
- Support escalation routing
- Quick patch criteria defined

📸 Screenshot placeholder: Hypercare ticket

### TASK: Closure / lessons learned
- What went well
- What to improve
- Follow-up backlog items

📸 Screenshot placeholder: Closure ticket

---

## Reporting screenshots we will capture (later)

- Board view (workflow columns)
- Backlog view (prioritized + refined)
- Sprint view (commitment + progress)
- One burndown / CFD chart (optional)
- Release page showing included issues

---

## Next step (Step 3)
Jira sandbox and tickets.
