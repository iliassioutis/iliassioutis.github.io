---
layout: default
title: Jira-style workflow example
---

<blockquote>
🏠 <a href="/">Back to homepage</a> · <a href="/project-delivery/">Project Delivery &amp; Methods</a>
</blockquote>

This page shows a **Jira-style end-to-end delivery workflow** using a **personal sandbox** with **fictitious tickets** (no client data).  
The goal is to demonstrate **how I structure delivery**, how artifacts connect, and how I run **quality and release governance** in a tool most teams recognize.

> **Important note**  
> I’m not claiming Jira administrator expertise. This is a realistic Jira-style example that mirrors how I run delivery across Jira. 

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
