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
> This is not a Jira administrator showcase. It’s a practical Jira-style example that reflects how I manage delivery, quality gates, and governance.
 
---

<p><strong>Optional: Live Jira sandbox</strong><br>
If you have a Jira account and I’ve granted access, you can open the live sandbox here:
<a href="https://isioutis.atlassian.net/jira/software/projects/SCRUM/boards/1/backlog" target="_blank" rel="noopener noreferrer">Delivery Sandbox (Jira)</a>.
</p>

<p style="margin: 6px 0 18px 0;">
If you need access, email me at <a href="mailto:isioutis@hotmail.com">isioutis@hotmail.com</a>.
</p>

---

## What this example covers

- Intake → framing → approval to start work
- Epic → stories/tasks → acceptance criteria → Definition of Done (DoD)
- Sprint execution with blockers and dependency handling (via linked work items)
- Quality gates (QA / SIT → UAT) and release readiness
- Release checklist + go-live preparation + monitoring/hypercare **planning** (shown as tickets/checklists)

---

## Scenario used in the sandbox (fictitious)

- **Product context:** A regulated digital-health mobile app (iOS/Android) with a secure backend
- **Release goal:** Add a “Contactless vitals” journey: a camera-based measurement session that produces on-device AI wellness estimates and stores **derived wellness estimates only** (no photos/videos), plus a history entry with **provenance labels** (AI / Device / Manual)
- **Supporting work included:** secure APIs (authentication + authorization + audit logging), Bluetooth device ingestion + data integrity checks, consent/retention/deletion controls, SIT + UAT planning, and a release readiness checklist
- **Constraints:** privacy-by-design, no camera media storage, audit-ready changes, staged rollout
- **Stakeholders:** Product, Mobile (iOS/Android), Backend, QA, Security/Privacy, Clinical/Validation, Support   

> This mirrors the type of delivery I’ve done in practice, but the tickets, names, and IDs here are fully fictitious.

---

## Project setup (what you will see in Jira)

### Issue types used
- **Epic** (feature-level outcome)
- **Feature** (optional grouping item; linked to the Epic in this sandbox — stories are parented to the Epic)
- **Story** (user-facing increment)
- **Task** (engineering / implementation work)
- **Bug** (defects)
- **Sub-task** (checklists, QA execution, release tasks)

> **Note:** Spikes are common in real delivery for timeboxed research, but this specific sandbox example focuses on story/task execution (so no dedicated Spike tickets are shown).

### Fields / conventions used (kept simple and realistic)
- **Priority**
- **Labels** (used to tag area/ownership, e.g., backend, qa, security)
- **Fix Version / Release tag** (planned release label in the sandbox, e.g., `v1.8.0`)
- **Acceptance criteria** and **test notes** inside the ticket description
- **Linked work items** (e.g., blocks / is blocked by / relates to) for dependencies and RAID linkage
- **Definition of Done** checklist (lightweight, consistent)

---

## Workflow used (Jira-style)

**Statuses configured in the sandbox:**
- **To Do**
- **In Progress**
- **In Review**
- **QA / SIT**
- **UAT**
- **Done**

**Transitions (as configured in this Jira workflow):**
- **Start → To Do** *(Create)*
- **Any status → To Do** *(send back / re-open)*
- **Any status → In Progress** *(start work)*
- **Any status → In Review** *(ready for peer review / PR review)*
- **Any status → QA / SIT** *(build deployed to test env; test execution starts)*
- **Any status → UAT** *(business testing / stakeholder validation)*
- **UAT → Done** *(Release / Close — the “release gate” transition, used for release sign-off)*
- **Any status → Done** *(Done — manual closure for non-release outcomes such as: duplicate, won’t do, out of scope, superseded by another ticket, cancelled)*

**Typical delivery path I follow:**
- To Do → In Progress → In Review → QA / SIT → UAT → Done *(Release / Close)*

**Common “send-back” loops (when defects or gaps are found):**
- In Review → In Progress *(review feedback)*
- QA / SIT → In Progress *(fix defects)*
- UAT → QA / SIT or In Progress *(UAT findings / adjustments)*

---

## End-to-end example tickets (sandbox)

Below is a complete ticket tree created in the sandbox, showing how I structure delivery from intake through release and closure.

<a id="artifact-nav"></a>
### Navigation (this section)

**Jira Pages artifacts**
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

**Backlog RAID work items (Jira)**
- [RAID R-01 — SCRUM-23: Bluetooth compatibility (supported device list + test matrix)](#backlog-scrum-23)
- [RAID R-02 — SCRUM-24: On-device AI may fail (“cannot estimate” + user guidance)](#backlog-scrum-24)
- [RAID R-03 — SCRUM-25: Privacy risk (accidental logging/storage of camera media or identifiers)](#backlog-scrum-25)
- [RAID R-04 — SCRUM-26: Backend performance degradation under peak usage (teleconsult/chat/uploads)](#backlog-scrum-26)
- [RAID I-01 — SCRUM-27: Android Bluetooth reconnection unstable after background/resume](#backlog-scrum-27)
- [RAID D-02 — SCRUM-28: Use provenance labels (AI / Device / Manual) everywhere](#backlog-scrum-28)

**Sprint 0 stories**
- [S-01 — SCRUM-7: Define scope + requirements](#sprint0-scrum-7)
- [S-01a — SCRUM-17: Scope workshop + in-scope/out-of-scope agreed (subtask)](#sprint0-scrum-17)
- [S-01b — SCRUM-18: Draft BRD (business requirements) (subtask)](#sprint0-scrum-18)
- [S-01c — SCRUM-19: Draft FRD (functional requirements) (subtask)](#sprint0-scrum-19)
- [S-01d — SCRUM-20: Create initial backlog (MVP vs later) (subtask)](#sprint0-scrum-20)
- [S-01e — SCRUM-21: Start RAID log (risks/issues/assumptions/decisions) (subtask)](#sprint0-scrum-21)
- [S-01f — SCRUM-22: Review + sign-off (stakeholder approval recorded) (subtask)](#sprint0-scrum-22)
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

<a href="/assets/img/jira-workflow/00-pages-index.png" target="_blank" rel="noopener noreferrer">
  <img src="/assets/img/jira-workflow/00-pages-index.png"
       alt="Sandbox Pages index — BRD, FRD, RAID Log, User Journeys, Figma walkthrough"
       loading="lazy"
       style="max-width: 1400px; width: 100%; height:auto; border: 1px solid #e5e7eb; border-radius: 8px; display:block; margin: 12px 0;">
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
<a href="/assets/img/jira-workflow/01-brd-01.png" target="_blank" rel="noopener noreferrer">
  <img src="/assets/img/jira-workflow/01-brd-01.png"
       alt="BRD — E-01 (chunk 1)"
       loading="lazy"
       style="max-width: 1400px; width: 100%; height:auto; border: 1px solid #e5e7eb; border-radius: 8px; display:block; margin: 12px 0;">
</a>

<!-- BRD chunk 2 -->
<a href="/assets/img/jira-workflow/01-brd-02.png" target="_blank" rel="noopener noreferrer">
  <img src="/assets/img/jira-workflow/01-brd-02.png"
       alt="BRD — E-01 (chunk 2)"
       loading="lazy"
       style="max-width: 1400px; width: 100%; height:auto; border: 1px solid #e5e7eb; border-radius: 8px; display:block; margin: 12px 0;">
</a>

<!-- BRD chunk 3 -->
<a href="/assets/img/jira-workflow/01-brd-03.png" target="_blank" rel="noopener noreferrer">
  <img src="/assets/img/jira-workflow/01-brd-03.png"
       alt="BRD — E-01 (chunk 3)"
       loading="lazy"
       style="max-width: 1400px; width: 100%; height:auto; border: 1px solid #e5e7eb; border-radius: 8px; display:block; margin: 12px 0;">
</a>

<!-- BRD chunk 4 -->
<a href="/assets/img/jira-workflow/01-brd-04.png" target="_blank" rel="noopener noreferrer">
  <img src="/assets/img/jira-workflow/01-brd-04.png"
       alt="BRD — E-01 (chunk 4)"
       loading="lazy"
       style="max-width: 1400px; width: 100%; height:auto; border: 1px solid #e5e7eb; border-radius: 8px; display:block; margin: 12px 0;">
</a>

<!-- BRD chunk 5 -->
<a href="/assets/img/jira-workflow/01-brd-05.png" target="_blank" rel="noopener noreferrer">
  <img src="/assets/img/jira-workflow/01-brd-05.png"
       alt="BRD — E-01 (chunk 5)"
       loading="lazy"
       style="max-width: 1400px; width: 100%; height:auto; border: 1px solid #e5e7eb; border-radius: 8px; display:block; margin: 12px 0;">
</a>

<!-- BRD chunk 6 -->
<a href="/assets/img/jira-workflow/01-brd-06.png" target="_blank" rel="noopener noreferrer">
  <img src="/assets/img/jira-workflow/01-brd-06.png"
       alt="BRD — E-01 (chunk 6)"
       loading="lazy"
       style="max-width: 1400px; width: 100%; height:auto; border: 1px solid #e5e7eb; border-radius: 8px; display:block; margin: 12px 0;">
</a>

<!-- BRD chunk 7 -->
<a href="/assets/img/jira-workflow/01-brd-07.png" target="_blank" rel="noopener noreferrer">
  <img src="/assets/img/jira-workflow/01-brd-07.png"
       alt="BRD — E-01 (chunk 7)"
       loading="lazy"
       style="max-width: 1400px; width: 100%; height:auto; border: 1px solid #e5e7eb; border-radius: 8px; display:block; margin: 12px 0;">
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
<a href="/assets/img/jira-workflow/02-frd-01.png" target="_blank" rel="noopener noreferrer">
  <img src="/assets/img/jira-workflow/02-frd-01.png"
       alt="FRD — E-01 (chunk 1)"
       loading="lazy"
       style="max-width: 1400px; width: 100%; height:auto; border: 1px solid #e5e7eb; border-radius: 8px; display:block; margin: 12px 0;">
</a>

<!-- FRD chunk 2 -->
<a href="/assets/img/jira-workflow/02-frd-02.png" target="_blank" rel="noopener noreferrer">
  <img src="/assets/img/jira-workflow/02-frd-02.png"
       alt="FRD — E-01 (chunk 2)"
       loading="lazy"
       style="max-width: 1400px; width: 100%; height:auto; border: 1px solid #e5e7eb; border-radius: 8px; display:block; margin: 12px 0;">
</a>

<!-- FRD chunk 3 -->
<a href="/assets/img/jira-workflow/02-frd-03.png" target="_blank" rel="noopener noreferrer">
  <img src="/assets/img/jira-workflow/02-frd-03.png"
       alt="FRD — E-01 (chunk 3)"
       loading="lazy"
       style="max-width: 1400px; width: 100%; height:auto; border: 1px solid #e5e7eb; border-radius: 8px; display:block; margin: 12px 0;">
</a>

<!-- FRD chunk 4 -->
<a href="/assets/img/jira-workflow/02-frd-04.png" target="_blank" rel="noopener noreferrer">
  <img src="/assets/img/jira-workflow/02-frd-04.png"
       alt="FRD — E-01 (chunk 4)"
       loading="lazy"
       style="max-width: 1400px; width: 100%; height:auto; border: 1px solid #e5e7eb; border-radius: 8px; display:block; margin: 12px 0;">
</a>

<!-- FRD chunk 5 -->
<a href="/assets/img/jira-workflow/02-frd-05.png" target="_blank" rel="noopener noreferrer">
  <img src="/assets/img/jira-workflow/02-frd-05.png"
       alt="FRD — E-01 (chunk 5)"
       loading="lazy"
       style="max-width: 1400px; width: 100%; height:auto; border: 1px solid #e5e7eb; border-radius: 8px; display:block; margin: 12px 0;">
</a>

<!-- FRD chunk 6 -->
<a href="/assets/img/jira-workflow/02-frd-06.png" target="_blank" rel="noopener noreferrer">
  <img src="/assets/img/jira-workflow/02-frd-06.png"
       alt="FRD — E-01 (chunk 6)"
       loading="lazy"
       style="max-width: 1400px; width: 100%; height:auto; border: 1px solid #e5e7eb; border-radius: 8px; display:block; margin: 12px 0;">
</a>

<!-- FRD chunk 7 -->
<a href="/assets/img/jira-workflow/02-frd-07.png" target="_blank" rel="noopener noreferrer">
  <img src="/assets/img/jira-workflow/02-frd-07.png"
       alt="FRD — E-01 (chunk 7)"
       loading="lazy"
       style="max-width: 1400px; width: 100%; height:auto; border: 1px solid #e5e7eb; border-radius: 8px; display:block; margin: 12px 0;">
</a>

<!-- FRD chunk 8 -->
<a href="/assets/img/jira-workflow/02-frd-08.png" target="_blank" rel="noopener noreferrer">
  <img src="/assets/img/jira-workflow/02-frd-08.png"
       alt="FRD — E-01 (chunk 8)"
       loading="lazy"
       style="max-width: 1400px; width: 100%; height:auto; border: 1px solid #e5e7eb; border-radius: 8px; display:block; margin: 12px 0;">
</a>

<!-- FRD chunk 9 -->
<a href="/assets/img/jira-workflow/02-frd-09.png" target="_blank" rel="noopener noreferrer">
  <img src="/assets/img/jira-workflow/02-frd-09.png"
       alt="FRD — E-01 (chunk 9)"
       loading="lazy"
       style="max-width: 1400px; width: 100%; height:auto; border: 1px solid #e5e7eb; border-radius: 8px; display:block; margin: 12px 0;">
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
<a href="/assets/img/jira-workflow/03-raid-01.png" target="_blank" rel="noopener noreferrer">
  <img src="/assets/img/jira-workflow/03-raid-01.png"
       alt="RAID log — E-01 (chunk 1)"
       loading="lazy"
       style="max-width: 1400px; width: 100%; height:auto; border: 1px solid #e5e7eb; border-radius: 8px; display:block; margin: 12px 0;">
</a>

<!-- RAID log chunk 2 -->
<a href="/assets/img/jira-workflow/03-raid-02.png" target="_blank" rel="noopener noreferrer">
  <img src="/assets/img/jira-workflow/03-raid-02.png"
       alt="RAID log — E-01 (chunk 2)"
       loading="lazy"
       style="max-width: 1400px; width: 100%; height:auto; border: 1px solid #e5e7eb; border-radius: 8px; display:block; margin: 12px 0;">
</a>

<!-- RAID log chunk 3 -->
<a href="/assets/img/jira-workflow/03-raid-03.png" target="_blank" rel="noopener noreferrer">
  <img src="/assets/img/jira-workflow/03-raid-03.png"
       alt="RAID log — E-01 (chunk 3)"
       loading="lazy"
       style="max-width: 1400px; width: 100%; height:auto; border: 1px solid #e5e7eb; border-radius: 8px; display:block; margin: 12px 0;">
</a>

<!-- RAID log chunk 4 -->
<a href="/assets/img/jira-workflow/03-raid-04.png" target="_blank" rel="noopener noreferrer">
  <img src="/assets/img/jira-workflow/03-raid-04.png"
       alt="RAID log — E-01 (chunk 4)"
       loading="lazy"
       style="max-width: 1400px; width: 100%; height:auto; border: 1px solid #e5e7eb; border-radius: 8px; display:block; margin: 12px 0;">
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
<a href="/assets/img/jira-workflow/04-journeys-01.png" target="_blank" rel="noopener noreferrer">
  <img src="/assets/img/jira-workflow/04-journeys-01.png"
       alt="User journeys — E-01 (chunk 1)"
       loading="lazy"
       style="max-width: 1400px; width: 100%; height:auto; border: 1px solid #e5e7eb; border-radius: 8px; display:block; margin: 12px 0;">
</a>

<!-- User journeys chunk 2 -->
<a href="/assets/img/jira-workflow/04-journeys-02.png" target="_blank" rel="noopener noreferrer">
  <img src="/assets/img/jira-workflow/04-journeys-02.png"
       alt="User journeys — E-01 (chunk 2)"
       loading="lazy"
       style="max-width: 1400px; width: 100%; height:auto; border: 1px solid #e5e7eb; border-radius: 8px; display:block; margin: 12px 0;">
</a>

<!-- User journeys chunk 3 -->
<a href="/assets/img/jira-workflow/04-journeys-03.png" target="_blank" rel="noopener noreferrer">
  <img src="/assets/img/jira-workflow/04-journeys-03.png"
       alt="User journeys — E-01 (chunk 3)"
       loading="lazy"
       style="max-width: 1400px; width: 100%; height:auto; border: 1px solid #e5e7eb; border-radius: 8px; display:block; margin: 12px 0;">
</a>

<!-- User journeys chunk 4 -->
<a href="/assets/img/jira-workflow/04-journeys-04.png" target="_blank" rel="noopener noreferrer">
  <img src="/assets/img/jira-workflow/04-journeys-04.png"
       alt="User journeys — E-01 (chunk 4)"
       loading="lazy"
       style="max-width: 1400px; width: 100%; height:auto; border: 1px solid #e5e7eb; border-radius: 8px; display:block; margin: 12px 0;">
</a>

<!-- User journeys chunk 5 -->
<a href="/assets/img/jira-workflow/04-journeys-05.png" target="_blank" rel="noopener noreferrer">
  <img src="/assets/img/jira-workflow/04-journeys-05.png"
       alt="User journeys — E-01 (chunk 5)"
       loading="lazy"
       style="max-width: 1400px; width: 100%; height:auto; border: 1px solid #e5e7eb; border-radius: 8px; display:block; margin: 12px 0;">
</a>

<!-- User journeys chunk 6 -->
<a href="/assets/img/jira-workflow/04-journeys-06.png" target="_blank" rel="noopener noreferrer">
  <img src="/assets/img/jira-workflow/04-journeys-06.png"
       alt="User journeys — E-01 (chunk 6)"
       loading="lazy"
       style="max-width: 1400px; width: 100%; height:auto; border: 1px solid #e5e7eb; border-radius: 8px; display:block; margin: 12px 0;">
</a>

<!-- User journeys chunk 7 -->
<a href="/assets/img/jira-workflow/04-journeys-07.png" target="_blank" rel="noopener noreferrer">
  <img src="/assets/img/jira-workflow/04-journeys-07.png"
       alt="User journeys — E-01 (chunk 7)"
       loading="lazy"
       style="max-width: 1400px; width: 100%; height:auto; border: 1px solid #e5e7eb; border-radius: 8px; display:block; margin: 12px 0;">
</a>

<!-- User journeys chunk 8 -->
<a href="/assets/img/jira-workflow/04-journeys-08.png" target="_blank" rel="noopener noreferrer">
  <img src="/assets/img/jira-workflow/04-journeys-08.png"
       alt="User journeys — E-01 (chunk 8)"
       loading="lazy"
       style="max-width: 1400px; width: 100%; height:auto; border: 1px solid #e5e7eb; border-radius: 8px; display:block; margin: 12px 0;">
</a>

<!-- User journeys chunk 9 -->
<a href="/assets/img/jira-workflow/04-journeys-09.png" target="_blank" rel="noopener noreferrer">
  <img src="/assets/img/jira-workflow/04-journeys-09.png"
       alt="User journeys — E-01 (chunk 9)"
       loading="lazy"
       style="max-width: 1400px; width: 100%; height:auto; border: 1px solid #e5e7eb; border-radius: 8px; display:block; margin: 12px 0;">
</a>

<!-- User journeys chunk 10 -->
<a href="/assets/img/jira-workflow/04-journeys-10.png" target="_blank" rel="noopener noreferrer">
  <img src="/assets/img/jira-workflow/04-journeys-10.png"
       alt="User journeys — E-01 (chunk 10)"
       loading="lazy"
       style="max-width: 1400px; width: 100%; height:auto; border: 1px solid #e5e7eb; border-radius: 8px; display:block; margin: 12px 0;">
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
<a href="/assets/img/jira-workflow/05-figma-01.png" target="_blank" rel="noopener noreferrer">
  <img src="/assets/img/jira-workflow/05-figma-01.png"
       alt="Figma walkthrough — E-01 (chunk 1)"
       loading="lazy"
       style="max-width: 1400px; width: 100%; height:auto; border: 1px solid #e5e7eb; border-radius: 8px; display:block; margin: 12px 0;">
</a>

<!-- Figma walkthrough chunk 2 -->
<a href="/assets/img/jira-workflow/05-figma-02.png" target="_blank" rel="noopener noreferrer">
  <img src="/assets/img/jira-workflow/05-figma-02.png"
       alt="Figma walkthrough — E-01 (chunk 2)"
       loading="lazy"
       style="max-width: 1400px; width: 100%; height:auto; border: 1px solid #e5e7eb; border-radius: 8px; display:block; margin: 12px 0;">
</a>

<!-- Figma walkthrough chunk 3 -->
<a href="/assets/img/jira-workflow/05-figma-03.png" target="_blank" rel="noopener noreferrer">
  <img src="/assets/img/jira-workflow/05-figma-03.png"
       alt="Figma walkthrough — E-01 (chunk 3)"
       loading="lazy"
       style="max-width: 1400px; width: 100%; height:auto; border: 1px solid #e5e7eb; border-radius: 8px; display:block; margin: 12px 0;">
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
<a href="/assets/img/jira-workflow/07-epic-scrum-6-01.png" target="_blank" rel="noopener noreferrer">
  <img src="/assets/img/jira-workflow/07-epic-scrum-6-01.png"
       alt="Epic SCRUM-6 — overview and description (chunk 1)"
       loading="lazy"
       style="max-width: 1400px; width: 100%; height:auto; border: 1px solid #e5e7eb; border-radius: 8px; display:block; margin: 12px 0;">
</a>

<!-- Epic chunk 2 -->
<a href="/assets/img/jira-workflow/07-epic-scrum-6-02.png" target="_blank" rel="noopener noreferrer">
  <img src="/assets/img/jira-workflow/07-epic-scrum-6-02.png"
       alt="Epic SCRUM-6 — child work items list (chunk 2)"
       loading="lazy"
       style="max-width: 1400px; width: 100%; height:auto; border: 1px solid #e5e7eb; border-radius: 8px; display:block; margin: 12px 0;">
</a>

<!-- Epic chunk 3 -->
<a href="/assets/img/jira-workflow/07-epic-scrum-6-03.png" target="_blank" rel="noopener noreferrer">
  <img src="/assets/img/jira-workflow/07-epic-scrum-6-03.png"
       alt="Epic SCRUM-6 — linked work items and details (chunk 3)"
       loading="lazy"
       style="max-width: 1400px; width: 100%; height:auto; border: 1px solid #e5e7eb; border-radius: 8px; display:block; margin: 12px 0;">
</a>

<!-- Epic chunk 4 -->
<a href="/assets/img/jira-workflow/07-epic-scrum-6-04.png" target="_blank" rel="noopener noreferrer">
  <img src="/assets/img/jira-workflow/07-epic-scrum-6-04.png"
       alt="Epic SCRUM-6 — fix version and metadata (chunk 4)"
       loading="lazy"
       style="max-width: 1400px; width: 100%; height:auto; border: 1px solid #e5e7eb; border-radius: 8px; display:block; margin: 12px 0;">
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
<a href="/assets/img/jira-workflow/08-feature-scrum-5-01.png" target="_blank" rel="noopener noreferrer">
  <img src="/assets/img/jira-workflow/08-feature-scrum-5-01.png"
       alt="Feature SCRUM-5 — header and overview (chunk 1)"
       loading="lazy"
       style="max-width: 1400px; width: 100%; height:auto; border: 1px solid #e5e7eb; border-radius: 8px; display:block; margin: 12px 0;">
</a>

<!-- Feature chunk 2 -->
<a href="/assets/img/jira-workflow/08-feature-scrum-5-02.png" target="_blank" rel="noopener noreferrer">
  <img src="/assets/img/jira-workflow/08-feature-scrum-5-02.png"
       alt="Feature SCRUM-5 — parent and details (chunk 2)"
       loading="lazy"
       style="max-width: 1400px; width: 100%; height:auto; border: 1px solid #e5e7eb; border-radius: 8px; display:block; margin: 12px 0;">
</a>

<!-- Feature chunk 3 -->
<a href="/assets/img/jira-workflow/08-feature-scrum-5-03.png" target="_blank" rel="noopener noreferrer">
  <img src="/assets/img/jira-workflow/08-feature-scrum-5-03.png"
       alt="Feature SCRUM-5 — fix version and metadata (chunk 3)"
       loading="lazy"
       style="max-width: 1400px; width: 100%; height:auto; border: 1px solid #e5e7eb; border-radius: 8px; display:block; margin: 12px 0;">
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
  <a href="/assets/img/jira-workflow/06-sprint0-backlog-wide.png" target="_blank" rel="noopener noreferrer">
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
<a href="/assets/img/jira-workflow/06-sprint0-backlog-left.png" target="_blank" rel="noopener noreferrer">
  <img src="/assets/img/jira-workflow/06-sprint0-backlog-left.png"
       alt="Jira backlog — Sprint 0 (close-up: items and summary)"
       loading="lazy"
       style="max-width:1400px; width:100%; border:1px solid #e5e7eb; border-radius:8px; display:block; margin:12px 0;">
</a>

<h4 style="margin-top:18px;">Close-up — status & estimates (right)</h4>
<a href="/assets/img/jira-workflow/06-sprint0-backlog-right.png" target="_blank" rel="noopener noreferrer">
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
<a href="/assets/img/jira-workflow/09-sprint0-scrum-7-01.png" target="_blank" rel="noopener noreferrer">
  <img src="/assets/img/jira-workflow/09-sprint0-scrum-7-01.png"
       alt="Sprint 0 story SCRUM-7 — header and description (chunk 1)"
       loading="lazy"
       style="max-width: 1400px; width: 100%;
              border: 1px solid #e5e7eb; border-radius: 8px;
              display:block; margin: 12px 0;">
</a>

<!-- Chunk 2 -->
<a href="/assets/img/jira-workflow/09-sprint0-scrum-7-02.png" target="_blank" rel="noopener noreferrer">
  <img src="/assets/img/jira-workflow/09-sprint0-scrum-7-02.png"
       alt="Sprint 0 story SCRUM-7 — acceptance criteria (chunk 2)"
       loading="lazy"
       style="max-width: 1400px; width: 100%;
              border: 1px solid #e5e7eb; border-radius: 8px;
              display:block; margin: 12px 0;">
</a>

<!-- Chunk 3 -->
<a href="/assets/img/jira-workflow/09-sprint0-scrum-7-03.png" target="_blank" rel="noopener noreferrer">
  <img src="/assets/img/jira-workflow/09-sprint0-scrum-7-03.png"
       alt="Sprint 0 story SCRUM-7 — subtasks and linked artifacts (chunk 3)"
       loading="lazy"
       style="max-width: 1400px; width: 100%;
              border: 1px solid #e5e7eb; border-radius: 8px;
              display:block; margin: 12px 0;">
</a>

<h4 style="margin-top:18px;">Subtask details</h4>

<!-- Subtask — SCRUM-17 -->
<a id="sprint0-scrum-17"></a>
<h5 style="margin-top:14px;">Subtask — S-01a (SCRUM-17): Scope workshop + in-scope/out-of-scope agreed</h5>

<a href="/assets/img/jira-workflow/09-sprint0-scrum-7-subtask-scrum-17-01.png" target="_blank" rel="noopener noreferrer">
  <img src="/assets/img/jira-workflow/09-sprint0-scrum-7-subtask-scrum-17-01.png"
       alt="Subtask SCRUM-17 — S-01a scope workshop: description and key fields"
       loading="lazy"
       style="max-width: 1400px; width: 100%;
              border: 1px solid #e5e7eb; border-radius: 8px;
              display:block; margin: 12px 0;">
</a>

<!-- Subtask — SCRUM-18 -->
<a id="sprint0-scrum-18"></a>
<h5 style="margin-top:14px;">Subtask — S-01b (SCRUM-18): Draft BRD (business requirements)</h5>

<a href="/assets/img/jira-workflow/09-sprint0-scrum-7-subtask-scrum-18-01.png" target="_blank" rel="noopener noreferrer">
  <img src="/assets/img/jira-workflow/09-sprint0-scrum-7-subtask-scrum-18-01.png"
       alt="Subtask SCRUM-18 — S-01b draft BRD: description, artifact link, and labels"
       loading="lazy"
       style="max-width: 1400px; width: 100%;
              border: 1px solid #e5e7eb; border-radius: 8px;
              display:block; margin: 12px 0;">
</a>

<!-- Subtask — SCRUM-19 -->
<a id="sprint0-scrum-19"></a>
<h5 style="margin-top:14px;">Subtask — S-01c (SCRUM-19): Draft FRD (functional requirements)</h5>

<a href="/assets/img/jira-workflow/09-sprint0-scrum-7-subtask-scrum-19-01.png" target="_blank" rel="noopener noreferrer">
  <img src="/assets/img/jira-workflow/09-sprint0-scrum-7-subtask-scrum-19-01.png"
       alt="Subtask SCRUM-19 — S-01c draft FRD: description, artifact link, and labels"
       loading="lazy"
       style="max-width: 1400px; width: 100%;
              border: 1px solid #e5e7eb; border-radius: 8px;
              display:block; margin: 12px 0;">
</a>

<!-- Subtask — SCRUM-20 -->
<a id="sprint0-scrum-20"></a>
<h5 style="margin-top:14px;">Subtask — S-01d (SCRUM-20): Create initial backlog (MVP vs later)</h5>

<a href="/assets/img/jira-workflow/09-sprint0-scrum-7-subtask-scrum-20-01.png" target="_blank" rel="noopener noreferrer">
  <img src="/assets/img/jira-workflow/09-sprint0-scrum-7-subtask-scrum-20-01.png"
       alt="Subtask SCRUM-20 — S-01d create initial backlog: description and labels (MVP vs later)"
       loading="lazy"
       style="max-width: 1400px; width: 100%;
              border: 1px solid #e5e7eb; border-radius: 8px;
              display:block; margin: 12px 0;">
</a>

<!-- Subtask — SCRUM-21 -->
<a id="sprint0-scrum-21"></a>
<h5 style="margin-top:14px;">Subtask — S-01e (SCRUM-21): Start RAID log (risks/issues/assumptions/decisions)</h5>

<!-- Chunk 1 -->
<a href="/assets/img/jira-workflow/09-sprint0-scrum-7-subtask-scrum-21-01.png" target="_blank" rel="noopener noreferrer">
  <img src="/assets/img/jira-workflow/09-sprint0-scrum-7-subtask-scrum-21-01.png"
       alt="Subtask SCRUM-21 — S-01e Start RAID log: description and artifact link"
       loading="lazy"
       style="max-width: 1400px; width: 100%;
              border: 1px solid #e5e7eb; border-radius: 8px;
              display:block; margin: 12px 0;">
</a>

<!-- Chunk 2 -->
<a href="/assets/img/jira-workflow/09-sprint0-scrum-7-subtask-scrum-21-02.png" target="_blank" rel="noopener noreferrer">
  <img src="/assets/img/jira-workflow/09-sprint0-scrum-7-subtask-scrum-21-02.png"
       alt="Subtask SCRUM-21 — S-01e Start RAID log: linked RAID work items list"
       loading="lazy"
       style="max-width: 1400px; width: 100%;
              border: 1px solid #e5e7eb; border-radius: 8px;
              display:block; margin: 12px 0;">
</a>

<!-- Chunk 3 -->
<a href="/assets/img/jira-workflow/09-sprint0-scrum-7-subtask-scrum-21-03.png" target="_blank" rel="noopener noreferrer">
  <img src="/assets/img/jira-workflow/09-sprint0-scrum-7-subtask-scrum-21-03.png"
       alt="Subtask SCRUM-21 — S-01e Start RAID log: details and labels"
       loading="lazy"
       style="max-width: 1400px; width: 100%;
              border: 1px solid #e5e7eb; border-radius: 8px;
              display:block; margin: 12px 0;">
</a>

<!-- Subtask — SCRUM-22 -->
<a id="sprint0-scrum-22"></a>
<h5 style="margin-top:14px;">Subtask — S-01f (SCRUM-22): Review + sign-off (stakeholder approval recorded)</h5>

<a href="/assets/img/jira-workflow/09-sprint0-scrum-7-subtask-scrum-22-01.png" target="_blank" rel="noopener noreferrer">
  <img src="/assets/img/jira-workflow/09-sprint0-scrum-7-subtask-scrum-22-01.png"
       alt="Subtask SCRUM-22 — S-01f review and sign-off: description and labels"
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
<a href="/assets/img/jira-workflow/09-sprint0-scrum-8-01.png" target="_blank" rel="noopener noreferrer">
  <img src="/assets/img/jira-workflow/09-sprint0-scrum-8-01.png"
       alt="Sprint 0 story SCRUM-8 — header and description (chunk 1)"
       loading="lazy"
       style="max-width: 1400px; width: 100%;
              border: 1px solid #e5e7eb; border-radius: 8px;
              display:block; margin: 12px 0;">
</a>

<!-- Chunk 2 -->
<a href="/assets/img/jira-workflow/09-sprint0-scrum-8-02.png" target="_blank" rel="noopener noreferrer">
  <img src="/assets/img/jira-workflow/09-sprint0-scrum-8-02.png"
       alt="Sprint 0 story SCRUM-8 — acceptance criteria (chunk 2)"
       loading="lazy"
       style="max-width: 1400px; width: 100%;
              border: 1px solid #e5e7eb; border-radius: 8px;
              display:block; margin: 12px 0;">
</a>

<!-- Chunk 3 -->
<a href="/assets/img/jira-workflow/09-sprint0-scrum-8-03.png" target="_blank" rel="noopener noreferrer">
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
<a href="/assets/img/jira-workflow/09-sprint0-scrum-9-01.png" target="_blank" rel="noopener noreferrer">
  <img src="/assets/img/jira-workflow/09-sprint0-scrum-9-01.png"
       alt="Sprint 0 story SCRUM-9 — header and description (chunk 1)"
       loading="lazy"
       style="max-width: 1400px; width: 100%;
              border: 1px solid #e5e7eb; border-radius: 8px;
              display:block; margin: 12px 0;">
</a>

<!-- Chunk 2 -->
<a href="/assets/img/jira-workflow/09-sprint0-scrum-9-02.png" target="_blank" rel="noopener noreferrer">
  <img src="/assets/img/jira-workflow/09-sprint0-scrum-9-02.png"
       alt="Sprint 0 story SCRUM-9 — scope, deliverables, and acceptance criteria (chunk 2)"
       loading="lazy"
       style="max-width: 1400px; width: 100%;
              border: 1px solid #e5e7eb; border-radius: 8px;
              display:block; margin: 12px 0;">
</a>

<!-- Chunk 3 -->
<a href="/assets/img/jira-workflow/09-sprint0-scrum-9-03.png" target="_blank" rel="noopener noreferrer">
  <img src="/assets/img/jira-workflow/09-sprint0-scrum-9-03.png"
       alt="Sprint 0 story SCRUM-9 — definition of done, notes, and subtasks list (chunk 3)"
       loading="lazy"
       style="max-width: 1400px; width: 100%;
              border: 1px solid #e5e7eb; border-radius: 8px;
              display:block; margin: 12px 0;">
</a>

<!-- Chunk 4 -->
<a href="/assets/img/jira-workflow/09-sprint0-scrum-9-04.png" target="_blank" rel="noopener noreferrer">
  <img src="/assets/img/jira-workflow/09-sprint0-scrum-9-04.png"
       alt="Sprint 0 story SCRUM-9 — linked work items and Confluence content (chunk 4)"
       loading="lazy"
       style="max-width: 1400px; width: 100%;
              border: 1px solid #e5e7eb; border-radius: 8px;
              display:block; margin: 12px 0;">
</a>

<!-- Chunk 5 -->
<a href="/assets/img/jira-workflow/09-sprint0-scrum-9-05.png" target="_blank" rel="noopener noreferrer">
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
  <a href="/assets/img/jira-workflow/10-sprint1-backlog-wide.png" target="_blank" rel="noopener noreferrer">
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
<a href="/assets/img/jira-workflow/10-sprint1-backlog-left.png" target="_blank" rel="noopener noreferrer">
  <img src="/assets/img/jira-workflow/10-sprint1-backlog-left.png"
       alt="Jira backlog — Sprint 1 (close-up: work items list)"
       loading="lazy"
       style="max-width:1400px; width:100%; border:1px solid #e5e7eb; border-radius:8px; display:block; margin:12px 0;">
</a>

<h4 style="margin-top:18px;">Close-up — statuses & estimates (right)</h4>
<a href="/assets/img/jira-workflow/10-sprint1-backlog-right.png" target="_blank" rel="noopener noreferrer">
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
<a href="/assets/img/jira-workflow/10-sprint1-scrum-10-01.png" target="_blank" rel="noopener noreferrer">
  <img src="/assets/img/jira-workflow/10-sprint1-scrum-10-01.png"
       alt="Sprint 1 story SCRUM-10 — header, description, scope/notes, and acceptance criteria (chunk 1)"
       loading="lazy"
       style="max-width: 1400px; width: 100%;
              border: 1px solid #e5e7eb; border-radius: 8px;
              display:block; margin: 12px 0;">
</a>

<!-- Chunk 2 -->
<a href="/assets/img/jira-workflow/10-sprint1-scrum-10-02.png" target="_blank" rel="noopener noreferrer">
  <img src="/assets/img/jira-workflow/10-sprint1-scrum-10-02.png"
       alt="Sprint 1 story SCRUM-10 — subtasks list and linked work items (chunk 2)"
       loading="lazy"
       style="max-width: 1400px; width: 100%;
              border: 1px solid #e5e7eb; border-radius: 8px;
              display:block; margin: 12px 0;">
</a>

<!-- Chunk 3 -->
<a href="/assets/img/jira-workflow/10-sprint1-scrum-10-03.png" target="_blank" rel="noopener noreferrer">
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
<a href="/assets/img/jira-workflow/10-sprint1-scrum-11-01.png" target="_blank" rel="noopener noreferrer">
  <img src="/assets/img/jira-workflow/10-sprint1-scrum-11-01.png"
       alt="Sprint 1 story SCRUM-11 — header and description (chunk 1)"
       loading="lazy"
       style="max-width: 1400px; width: 100%;
              border: 1px solid #e5e7eb; border-radius: 8px;
              display:block; margin: 12px 0;">
</a>

<!-- Chunk 2 -->
<a href="/assets/img/jira-workflow/10-sprint1-scrum-11-02.png" target="_blank" rel="noopener noreferrer">
  <img src="/assets/img/jira-workflow/10-sprint1-scrum-11-02.png"
       alt="Sprint 1 story SCRUM-11 — acceptance criteria and notes/evidence (chunk 2)"
       loading="lazy"
       style="max-width: 1400px; width: 100%;
              border: 1px solid #e5e7eb; border-radius: 8px;
              display:block; margin: 12px 0;">
</a>

<!-- Chunk 3 -->
<a href="/assets/img/jira-workflow/10-sprint1-scrum-11-03.png" target="_blank" rel="noopener noreferrer">
  <img src="/assets/img/jira-workflow/10-sprint1-scrum-11-03.png"
       alt="Sprint 1 story SCRUM-11 — subtasks list (chunk 3)"
       loading="lazy"
       style="max-width: 1400px; width: 100%;
              border: 1px solid #e5e7eb; border-radius: 8px;
              display:block; margin: 12px 0;">
</a>

<!-- Chunk 4 -->
<a href="/assets/img/jira-workflow/10-sprint1-scrum-11-04.png" target="_blank" rel="noopener noreferrer">
  <img src="/assets/img/jira-workflow/10-sprint1-scrum-11-04.png"
       alt="Sprint 1 story SCRUM-11 — blocked-by link, linked work items, and Confluence content (chunk 4)"
       loading="lazy"
       style="max-width: 1400px; width: 100%;
              border: 1px solid #e5e7eb; border-radius: 8px;
              display:block; margin: 12px 0;">
</a>

<!-- Chunk 5 -->
<a href="/assets/img/jira-workflow/10-sprint1-scrum-11-05.png" target="_blank" rel="noopener noreferrer">
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
<a href="/assets/img/jira-workflow/10-sprint1-scrum-12-01.png" target="_blank" rel="noopener noreferrer">
  <img src="/assets/img/jira-workflow/10-sprint1-scrum-12-01.png"
       alt="Sprint 1 story SCRUM-12 — header, description, acceptance criteria, and notes/evidence (chunk 1)"
       loading="lazy"
       style="max-width: 1400px; width: 100%;
              border: 1px solid #e5e7eb; border-radius: 8px;
              display:block; margin: 12px 0;">
</a>

<!-- Chunk 2 -->
<a href="/assets/img/jira-workflow/10-sprint1-scrum-12-02.png" target="_blank" rel="noopener noreferrer">
  <img src="/assets/img/jira-workflow/10-sprint1-scrum-12-02.png"
       alt="Sprint 1 story SCRUM-12 — subtasks list (chunk 2)"
       loading="lazy"
       style="max-width: 1400px; width: 100%;
              border: 1px solid #e5e7eb; border-radius: 8px;
              display:block; margin: 12px 0;">
</a>

<!-- Chunk 3 -->
<a href="/assets/img/jira-workflow/10-sprint1-scrum-12-03.png" target="_blank" rel="noopener noreferrer">
  <img src="/assets/img/jira-workflow/10-sprint1-scrum-12-03.png"
       alt="Sprint 1 story SCRUM-12 — linked work items and Confluence content (chunk 3)"
       loading="lazy"
       style="max-width: 1400px; width: 100%;
              border: 1px solid #e5e7eb; border-radius: 8px;
              display:block; margin: 12px 0;">
</a>

<!-- Chunk 4 -->
<a href="/assets/img/jira-workflow/10-sprint1-scrum-12-04.png" target="_blank" rel="noopener noreferrer">
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
<a href="/assets/img/jira-workflow/10-sprint1-scrum-13-01.png" target="_blank" rel="noopener noreferrer">
  <img src="/assets/img/jira-workflow/10-sprint1-scrum-13-01.png"
       alt="Sprint 1 story SCRUM-13 — header, description, and acceptance criteria (chunk 1)"
       loading="lazy"
       style="max-width: 1400px; width: 100%;
              border: 1px solid #e5e7eb; border-radius: 8px;
              display:block; margin: 12px 0;">
</a>

<!-- Chunk 2 -->
<a href="/assets/img/jira-workflow/10-sprint1-scrum-13-02.png" target="_blank" rel="noopener noreferrer">
  <img src="/assets/img/jira-workflow/10-sprint1-scrum-13-02.png"
       alt="Sprint 1 story SCRUM-13 — subtasks list (chunk 2)"
       loading="lazy"
       style="max-width: 1400px; width: 100%;
              border: 1px solid #e5e7eb; border-radius: 8px;
              display:block; margin: 12px 0;">
</a>

<!-- Chunk 3 -->
<a href="/assets/img/jira-workflow/10-sprint1-scrum-13-03.png" target="_blank" rel="noopener noreferrer">
  <img src="/assets/img/jira-workflow/10-sprint1-scrum-13-03.png"
       alt="Sprint 1 story SCRUM-13 — linked work items and Confluence content (chunk 3)"
       loading="lazy"
       style="max-width: 1400px; width: 100%;
              border: 1px solid #e5e7eb; border-radius: 8px;
              display:block; margin: 12px 0;">
</a>

<!-- Chunk 4 -->
<a href="/assets/img/jira-workflow/10-sprint1-scrum-13-04.png" target="_blank" rel="noopener noreferrer">
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
<a href="/assets/img/jira-workflow/10-sprint1-scrum-14-01.png" target="_blank" rel="noopener noreferrer">
  <img src="/assets/img/jira-workflow/10-sprint1-scrum-14-01.png"
       alt="Sprint 1 story SCRUM-14 — header and description (chunk 1)"
       loading="lazy"
       style="max-width: 1400px; width: 100%;
              border: 1px solid #e5e7eb; border-radius: 8px;
              display:block; margin: 12px 0;">
</a>

<!-- Chunk 2 -->
<a href="/assets/img/jira-workflow/10-sprint1-scrum-14-02.png" target="_blank" rel="noopener noreferrer">
  <img src="/assets/img/jira-workflow/10-sprint1-scrum-14-02.png"
       alt="Sprint 1 story SCRUM-14 — acceptance criteria continuation (chunk 2)"
       loading="lazy"
       style="max-width: 1400px; width: 100%;
              border: 1px solid #e5e7eb; border-radius: 8px;
              display:block; margin: 12px 0;">
</a>

<!-- Chunk 3 -->
<a href="/assets/img/jira-workflow/10-sprint1-scrum-14-03.png" target="_blank" rel="noopener noreferrer">
  <img src="/assets/img/jira-workflow/10-sprint1-scrum-14-03.png"
       alt="Sprint 1 story SCRUM-14 — subtasks list (chunk 3)"
       loading="lazy"
       style="max-width: 1400px; width: 100%;
              border: 1px solid #e5e7eb; border-radius: 8px;
              display:block; margin: 12px 0;">
</a>

<!-- Chunk 4 -->
<a href="/assets/img/jira-workflow/10-sprint1-scrum-14-04.png" target="_blank" rel="noopener noreferrer">
  <img src="/assets/img/jira-workflow/10-sprint1-scrum-14-04.png"
       alt="Sprint 1 story SCRUM-14 — linked work items and pinned fields (chunk 4)"
       loading="lazy"
       style="max-width: 1400px; width: 100%;
              border: 1px solid #e5e7eb; border-radius: 8px;
              display:block; margin: 12px 0;">
</a>

<!-- Chunk 5 -->
<a href="/assets/img/jira-workflow/10-sprint1-scrum-14-05.png" target="_blank" rel="noopener noreferrer">
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
<a href="/assets/img/jira-workflow/10-sprint1-scrum-15-01.png" target="_blank" rel="noopener noreferrer">
  <img src="/assets/img/jira-workflow/10-sprint1-scrum-15-01.png"
       alt="Sprint 1 story SCRUM-15 — header, description, and acceptance criteria (chunk 1)"
       loading="lazy"
       style="max-width: 1400px; width: 100%;
              border: 1px solid #e5e7eb; border-radius: 8px;
              display:block; margin: 12px 0;">
</a>

<!-- Chunk 2 -->
<a href="/assets/img/jira-workflow/10-sprint1-scrum-15-02.png" target="_blank" rel="noopener noreferrer">
  <img src="/assets/img/jira-workflow/10-sprint1-scrum-15-02.png"
       alt="Sprint 1 story SCRUM-15 — notes and scope boundaries (chunk 2)"
       loading="lazy"
       style="max-width: 1400px; width: 100%;
              border: 1px solid #e5e7eb; border-radius: 8px;
              display:block; margin: 12px 0;">
</a>

<!-- Chunk 3 -->
<a href="/assets/img/jira-workflow/10-sprint1-scrum-15-03.png" target="_blank" rel="noopener noreferrer">
  <img src="/assets/img/jira-workflow/10-sprint1-scrum-15-03.png"
       alt="Sprint 1 story SCRUM-15 — subtasks list (chunk 3)"
       loading="lazy"
       style="max-width: 1400px; width: 100%;
              border: 1px solid #e5e7eb; border-radius: 8px;
              display:block; margin: 12px 0;">
</a>

<!-- Chunk 4 -->
<a href="/assets/img/jira-workflow/10-sprint1-scrum-15-04.png" target="_blank" rel="noopener noreferrer">
  <img src="/assets/img/jira-workflow/10-sprint1-scrum-15-04.png"
       alt="Sprint 1 story SCRUM-15 — linked work items and pinned fields (chunk 4)"
       loading="lazy"
       style="max-width: 1400px; width: 100%;
              border: 1px solid #e5e7eb; border-radius: 8px;
              display:block; margin: 12px 0;">
</a>

<!-- Chunk 5 -->
<a href="/assets/img/jira-workflow/10-sprint1-scrum-15-05.png" target="_blank" rel="noopener noreferrer">
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
<a href="/assets/img/jira-workflow/10-sprint1-scrum-16-01.png" target="_blank" rel="noopener noreferrer">
  <img src="/assets/img/jira-workflow/10-sprint1-scrum-16-01.png"
       alt="Sprint 1 story SCRUM-16 — header and description (chunk 1)"
       loading="lazy"
       style="max-width: 1400px; width: 100%;
              border: 1px solid #e5e7eb; border-radius: 8px;
              display:block; margin: 12px 0;">
</a>

<!-- Chunk 2 -->
<a href="/assets/img/jira-workflow/10-sprint1-scrum-16-02.png" target="_blank" rel="noopener noreferrer">
  <img src="/assets/img/jira-workflow/10-sprint1-scrum-16-02.png"
       alt="Sprint 1 story SCRUM-16 — acceptance criteria continuation and definition of done (chunk 2)"
       loading="lazy"
       style="max-width: 1400px; width: 100%;
              border: 1px solid #e5e7eb; border-radius: 8px;
              display:block; margin: 12px 0;">
</a>

<!-- Chunk 3 -->
<a href="/assets/img/jira-workflow/10-sprint1-scrum-16-03.png" target="_blank" rel="noopener noreferrer">
  <img src="/assets/img/jira-workflow/10-sprint1-scrum-16-03.png"
       alt="Sprint 1 story SCRUM-16 — subtasks list (chunk 3)"
       loading="lazy"
       style="max-width: 1400px; width: 100%;
              border: 1px solid #e5e7eb; border-radius: 8px;
              display:block; margin: 12px 0;">
</a>

<!-- Chunk 4 -->
<a href="/assets/img/jira-workflow/10-sprint1-scrum-16-04.png" target="_blank" rel="noopener noreferrer">
  <img src="/assets/img/jira-workflow/10-sprint1-scrum-16-04.png"
       alt="Sprint 1 story SCRUM-16 — linked work items and Confluence content (chunk 4)"
       loading="lazy"
       style="max-width: 1400px; width: 100%;
              border: 1px solid #e5e7eb; border-radius: 8px;
              display:block; margin: 12px 0;">
</a>

<!-- Chunk 5 -->
<a href="/assets/img/jira-workflow/10-sprint1-scrum-16-05.png" target="_blank" rel="noopener noreferrer">
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

<a id="sprint1-scrum-109"></a>
### Sprint 1 — BUG-01 (SCRUM-109): Android BLE reconnection unstable after background/resume (screenshots)

<!-- Chunk 1 -->
<a href="/assets/img/jira-workflow/10-sprint1-scrum-109-01.png" target="_blank" rel="noopener noreferrer">
  <img src="/assets/img/jira-workflow/10-sprint1-scrum-109-01.png"
       alt="Sprint 1 bug SCRUM-109 — header and description (steps, expected vs actual, impact) (chunk 1)"
       loading="lazy"
       style="max-width: 1400px; width: 100%;
              border: 1px solid #e5e7eb; border-radius: 8px;
              display:block; margin: 12px 0;">
</a>

<!-- Chunk 2 -->
<a href="/assets/img/jira-workflow/10-sprint1-scrum-109-02.png" target="_blank" rel="noopener noreferrer">
  <img src="/assets/img/jira-workflow/10-sprint1-scrum-109-02.png"
       alt="Sprint 1 bug SCRUM-109 — linked work items and priority (chunk 2)"
       loading="lazy"
       style="max-width: 1400px; width: 100%;
              border: 1px solid #e5e7eb; border-radius: 8px;
              display:block; margin: 12px 0;">
</a>

<!-- Chunk 3 -->
<a href="/assets/img/jira-workflow/10-sprint1-scrum-109-03.png" target="_blank" rel="noopener noreferrer">
  <img src="/assets/img/jira-workflow/10-sprint1-scrum-109-03.png"
       alt="Sprint 1 bug SCRUM-109 — details, labels, sprint, and fix version (chunk 3)"
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

<a id="sprint1-scrum-110"></a>
### Sprint 1 — BUG-02 (SCRUM-110): History API returns 500 when optional field missing (screenshots)

<!-- Chunk 1 -->
<a href="/assets/img/jira-workflow/10-sprint1-scrum-110-01.png" target="_blank" rel="noopener noreferrer">
  <img src="/assets/img/jira-workflow/10-sprint1-scrum-110-01.png"
       alt="Sprint 1 bug SCRUM-110 — header and description (where, steps, expected vs actual, acceptance) (chunk 1)"
       loading="lazy"
       style="max-width: 1400px; width: 100%;
              border: 1px solid #e5e7eb; border-radius: 8px;
              display:block; margin: 12px 0;">
</a>

<!-- Chunk 2 -->
<a href="/assets/img/jira-workflow/10-sprint1-scrum-110-02.png" target="_blank" rel="noopener noreferrer">
  <img src="/assets/img/jira-workflow/10-sprint1-scrum-110-02.png"
       alt="Sprint 1 bug SCRUM-110 — linked work items and priority (chunk 2)"
       loading="lazy"
       style="max-width: 1400px; width: 100%;
              border: 1px solid #e5e7eb; border-radius: 8px;
              display:block; margin: 12px 0;">
</a>

<!-- Chunk 3 -->
<a href="/assets/img/jira-workflow/10-sprint1-scrum-110-03.png" target="_blank" rel="noopener noreferrer">
  <img src="/assets/img/jira-workflow/10-sprint1-scrum-110-03.png"
       alt="Sprint 1 bug SCRUM-110 — details, labels, sprint, and fix version (chunk 3)"
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

<a id="backlog-scrum-23"></a>
### Backlog — RAID R-01 (SCRUM-23): Bluetooth compatibility (supported device list + test matrix) (screenshots)

<!-- Chunk 1 -->
<a href="/assets/img/jira-workflow/11-backlog-scrum-23-01.png" target="_blank" rel="noopener noreferrer">
  <img src="/assets/img/jira-workflow/11-backlog-scrum-23-01.png"
       alt="Backlog RAID item SCRUM-23 — header, description, and linked work items (chunk 1)"
       loading="lazy"
       style="max-width: 1400px; width: 100%;
              border: 1px solid #e5e7eb; border-radius: 8px;
              display:block; margin: 12px 0;">
</a>

<!-- Chunk 2 -->
<a href="/assets/img/jira-workflow/11-backlog-scrum-23-02.png" target="_blank" rel="noopener noreferrer">
  <img src="/assets/img/jira-workflow/11-backlog-scrum-23-02.png"
       alt="Backlog RAID item SCRUM-23 — pinned fields and details (chunk 2)"
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

<a id="backlog-scrum-24"></a>
### Backlog — RAID R-02 (SCRUM-24): On-device AI may fail (“cannot estimate” + user guidance) (screenshots)

<!-- Chunk 1 -->
<a href="/assets/img/jira-workflow/11-backlog-scrum-24-01.png" target="_blank" rel="noopener noreferrer">
  <img src="/assets/img/jira-workflow/11-backlog-scrum-24-01.png"
       alt="Backlog RAID task SCRUM-24 — header and description (risk, outcome, next actions) (chunk 1)"
       loading="lazy"
       style="max-width: 1400px; width: 100%;
              border: 1px solid #e5e7eb; border-radius: 8px;
              display:block; margin: 12px 0;">
</a>

<!-- Chunk 2 -->
<a href="/assets/img/jira-workflow/11-backlog-scrum-24-02.png" target="_blank" rel="noopener noreferrer">
  <img src="/assets/img/jira-workflow/11-backlog-scrum-24-02.png"
       alt="Backlog RAID task SCRUM-24 — linked work items and pinned fields (chunk 2)"
       loading="lazy"
       style="max-width: 1400px; width: 100%;
              border: 1px solid #e5e7eb; border-radius: 8px;
              display:block; margin: 12px 0;">
</a>

<!-- Chunk 3 -->
<a href="/assets/img/jira-workflow/11-backlog-scrum-24-03.png" target="_blank" rel="noopener noreferrer">
  <img src="/assets/img/jira-workflow/11-backlog-scrum-24-03.png"
       alt="Backlog RAID task SCRUM-24 — details, labels, and metadata (chunk 3)"
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

<a id="backlog-scrum-25"></a>
### Backlog — RAID R-03 (SCRUM-25): Privacy risk (accidental logging/storage of camera media or identifiers) (screenshots)

<!-- Chunk 1 -->
<a href="/assets/img/jira-workflow/11-backlog-scrum-25-01.png" target="_blank" rel="noopener noreferrer">
  <img src="/assets/img/jira-workflow/11-backlog-scrum-25-01.png"
       alt="Backlog RAID task SCRUM-25 — header and description (risk, outcome, next actions) (chunk 1)"
       loading="lazy"
       style="max-width: 1400px; width: 100%;
              border: 1px solid #e5e7eb; border-radius: 8px;
              display:block; margin: 12px 0;">
</a>

<!-- Chunk 2 -->
<a href="/assets/img/jira-workflow/11-backlog-scrum-25-02.png" target="_blank" rel="noopener noreferrer">
  <img src="/assets/img/jira-workflow/11-backlog-scrum-25-02.png"
       alt="Backlog RAID task SCRUM-25 — linked work items and priority (chunk 2)"
       loading="lazy"
       style="max-width: 1400px; width: 100%;
              border: 1px solid #e5e7eb; border-radius: 8px;
              display:block; margin: 12px 0;">
</a>

<!-- Chunk 3 -->
<a href="/assets/img/jira-workflow/11-backlog-scrum-25-03.png" target="_blank" rel="noopener noreferrer">
  <img src="/assets/img/jira-workflow/11-backlog-scrum-25-03.png"
       alt="Backlog RAID task SCRUM-25 — details, labels, and metadata (chunk 3)"
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

<a id="backlog-scrum-26"></a>
### Backlog — RAID R-04 (SCRUM-26): Backend performance degradation under peak usage (teleconsult/chat/uploads) (screenshots)

<!-- Chunk 1 -->
<a href="/assets/img/jira-workflow/11-backlog-scrum-26-01.png" target="_blank" rel="noopener noreferrer">
  <img src="/assets/img/jira-workflow/11-backlog-scrum-26-01.png"
       alt="Backlog RAID SCRUM-26 — header and description (risk, outcome, next actions) (chunk 1)"
       loading="lazy"
       style="max-width: 1400px; width: 100%;
              border: 1px solid #e5e7eb; border-radius: 8px;
              display:block; margin: 12px 0;">
</a>

<!-- Chunk 2 -->
<a href="/assets/img/jira-workflow/11-backlog-scrum-26-02.png" target="_blank" rel="noopener noreferrer">
  <img src="/assets/img/jira-workflow/11-backlog-scrum-26-02.png"
       alt="Backlog RAID SCRUM-26 — pinned fields and details (labels, parent, etc.) (chunk 2)"
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

<a id="backlog-scrum-27"></a>
### Backlog — RAID I-01 (SCRUM-27): Android Bluetooth reconnection unstable after background/resume (screenshots)

<!-- Chunk 1 -->
<a href="/assets/img/jira-workflow/11-backlog-scrum-27-01.png" target="_blank" rel="noopener noreferrer">
  <img src="/assets/img/jira-workflow/11-backlog-scrum-27-01.png"
       alt="Backlog RAID item SCRUM-27 — header and description (issue, impact, repro notes, next actions) (chunk 1)"
       loading="lazy"
       style="max-width: 1400px; width: 100%;
              border: 1px solid #e5e7eb; border-radius: 8px;
              display:block; margin: 12px 0;">
</a>

<!-- Chunk 2 -->
<a href="/assets/img/jira-workflow/11-backlog-scrum-27-02.png" target="_blank" rel="noopener noreferrer">
  <img src="/assets/img/jira-workflow/11-backlog-scrum-27-02.png"
       alt="Backlog RAID item SCRUM-27 — linked work items and pinned fields (chunk 2)"
       loading="lazy"
       style="max-width: 1400px; width: 100%;
              border: 1px solid #e5e7eb; border-radius: 8px;
              display:block; margin: 12px 0;">
</a>

<!-- Chunk 3 -->
<a href="/assets/img/jira-workflow/11-backlog-scrum-27-03.png" target="_blank" rel="noopener noreferrer">
  <img src="/assets/img/jira-workflow/11-backlog-scrum-27-03.png"
       alt="Backlog RAID item SCRUM-27 — details, labels, and metadata (chunk 3)"
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

<a id="backlog-scrum-28"></a>
### Backlog — RAID D-02 (SCRUM-28): Use provenance labels (AI / Device / Manual) everywhere (screenshots)

<!-- Chunk 1 -->
<a href="/assets/img/jira-workflow/11-backlog-scrum-28-01.png" target="_blank" rel="noopener noreferrer">
  <img src="/assets/img/jira-workflow/11-backlog-scrum-28-01.png"
       alt="Backlog RAID SCRUM-28 — header and description (decision/reason/next action) (chunk 1)"
       loading="lazy"
       style="max-width: 1400px; width: 100%;
              border: 1px solid #e5e7eb; border-radius: 8px;
              display:block; margin: 12px 0;">
</a>

<!-- Chunk 2 -->
<a href="/assets/img/jira-workflow/11-backlog-scrum-28-02.png" target="_blank" rel="noopener noreferrer">
  <img src="/assets/img/jira-workflow/11-backlog-scrum-28-02.png"
       alt="Backlog RAID SCRUM-28 — linked work items and pinned fields (chunk 2)"
       loading="lazy"
       style="max-width: 1400px; width: 100%;
              border: 1px solid #e5e7eb; border-radius: 8px;
              display:block; margin: 12px 0;">
</a>

<!-- Chunk 3 -->
<a href="/assets/img/jira-workflow/11-backlog-scrum-28-03.png" target="_blank" rel="noopener noreferrer">
  <img src="/assets/img/jira-workflow/11-backlog-scrum-28-03.png"
       alt="Backlog RAID SCRUM-28 — details (labels, parent, etc.) (chunk 3)"
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
