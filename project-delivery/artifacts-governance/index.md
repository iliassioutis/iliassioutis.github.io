---
layout: default
title: Artifacts & governance
---

<blockquote>
🏠 <a href="/">Back to homepage</a> · <a href="/project-delivery/">Project Delivery & Methods</a>
</blockquote>

This page explains the practical artifacts and governance controls I use to keep delivery aligned, transparent, and audit-ready — across both iterative (Agile) and stage-gate delivery.  
It focuses on **what I produce**, **how I use it**, and **how it reduces risk** (scope, quality, security/privacy, and release readiness).

---

## What you will find here

- A clear view of the **core artifacts** I use to run delivery end-to-end
- The **governance controls** that keep decisions, risks, and changes visible
- How I run **testing and release governance** (SIT/UAT, readiness, go-live, hypercare)
- How I handle **privacy, security, and AI governance** when the product includes sensitive data and on-device AI

---

## Core delivery artifacts

### 1) Requirements and specifications
These artifacts ensure everyone agrees on *what we are building*, *why*, and *how success is measured*.

- **Business Requirements Document (BRD)**  
  The business goals, scope boundaries, stakeholders, success criteria, and constraints (time/cost/risk/regulatory).
- **Functional Requirements Document (FRD)** (or equivalent specification)  
  What the system must do: workflows, screens, integrations, data handling rules, error handling, and business rules.
- **User stories / use cases + acceptance criteria**  
  “What good looks like” in a testable way — covering the normal (“happy path”) flow *and* realistic “non-happy path” scenarios (invalid inputs, permission denied, offline/timeout, device disconnect, integration errors), plus key edge cases.
- **Non-functional requirements (NFRs)**  
  The “how well it must work” requirements — beyond features:  
  - **Security & privacy:** encryption, access control, data minimization, retention/deletion, consent handling  
  - **Performance:** response times, throughput, and acceptable latency under expected load  
  - **Availability:** target uptime and resilience (e.g., planned downtime windows, failover expectations)  
  - **Reliability:** consistent behavior over time (error rates, retries, data consistency, **graceful degradation — key functions still work in a reduced mode when a dependency fails**, clear fallback behavior)  
  - **Auditability:** evidence-ready logs and traceability (who did what, when, and why; change history)  
  - **Observability:** monitoring/alerting and diagnostics (metrics, logs, traces) to detect and troubleshoot issues  
  - **Usability:** user experience expectations (clarity, accessibility, error messaging, friction in key journeys)

How this shows up in my work (example patterns):
- Turning “feature requests” into **testable acceptance criteria** (including security/privacy constraints, not just UI behavior).
- Capturing platform constraints and behavior differences (e.g., mobile platform retention, provenance labeling rules, device compatibility boundaries).

---

### 2) Solution notes and decision records
These make architecture decisions explicit and traceable (especially important when integrations, data flows, or regulated constraints exist).

- **Solution notes / Architecture decision records (ADRs)**  
  Why a decision was taken, alternatives considered, risks, and impacts.
- **Integration notes**  
  API contracts, message schemas, edge cases, retries/timeouts, failure modes, and operational responsibilities.
- **Data flow notes**  
  What data is collected, where it is processed, what is stored, retention/deletion rules, and access controls.

How this shows up in my work (example patterns):
- Documenting **on-device AI processing boundaries** (what is processed on-device, what is not uploaded/stored).
- Defining end-to-end data handling rules for **Bluetooth device integrations** (device → app → backend → clinician view), including integrity checks and traceability.

---

### 3) Testing strategy and evidence plan
This is how I make quality measurable and defensible (not just “we tested it”).

- **Test strategy**  
  Scope, approach, responsibilities, environments, data setup, and evidence expectations.
- **System Integration Testing (SIT)** plan  
  Cross-component validation (mobile app + backend + integrations), with entry/exit criteria.
- **User Acceptance Testing (UAT)** plan  
  Business/clinical/user workflows validated with clear acceptance criteria and sign-off rules.
- **Test evidence** (when appropriate)  
  What is captured and where (test cases, results, defect logs, screenshots/logs, summaries).

How this shows up in my work (example patterns):
- Structuring testing so it progresses from **unit → component → integration → system**, then SIT/UAT readiness.
- Creating a reproducible evidence trail for sensitive features (security controls, retention/deletion behavior, provenance labeling).

---

### 4) Release plan and operational readiness
These artifacts reduce production risk and make go-live predictable.

- **Release plan**  
  Environments (development/test/staging/production), deployment steps, verification checklist, and rollback plan.
- **Go-live runbook**  
  Who does what, in what order, with verification steps and decision points.
- **Monitoring and alerting plan**  
  Key signals to watch (availability, error rates, performance, integration failures, data pipeline health).
- **Hypercare plan**  
  Stabilization window, triage process, escalation paths, and success criteria for “steady state”.

How this shows up in my work (example patterns):
- Using a structured **go/no-go release decision** with explicit criteria (feature complete, test complete, risks accepted/mitigated).
- Ensuring operational readiness for real-world usage (incident triage, rollback, and post-release stabilization).

---

## Governance tools I use repeatedly

### Risk and dependency control
- **RAID log (Risks, Assumptions, Issues, Dependencies)**  
  A living log that is reviewed regularly, with owners, status, mitigations, and dates.
- **Dependency mapping**  
  External services, vendor components, mobile OS constraints, device compatibility boundaries, and integration windows.

Practical examples of what I track:
- Integration dependencies (third-party services, identity providers, analytics/crash reporting tools).
- Mobile OS and peripheral constraints (e.g., supported OS versions, device-model limitations).

---

### Ownership and decision-making
- **RACI (Responsible, Accountable, Consulted, Informed)**  
  Clarifies who owns delivery outcomes and who must be consulted or informed.
- **Decision paths**  
  Who decides what (scope changes, security/privacy gates, release approvals), and when escalation is triggered.

---

### Change control
Change control prevents uncontrolled scope creep and protects delivery predictability.

- **Change requests**  
  What changed and why (feature, timeline, scope, risk).
- **Impact assessment**  
  Schedule, cost, dependencies, risks, quality, and operational impacts.
- **Approval / rejection + re-baselining**  
  Documented outcomes so scope and expectations stay aligned.

---

### Quality gates
Quality gates are explicit readiness checks before SIT, UAT, and production release.

Typical gates I use:
- Requirements readiness (clear acceptance criteria and testability)
- Security/privacy readiness (data handling agreed, controls verified)
- SIT readiness (stable builds, integration dependencies available)
- UAT readiness (scope confirmed, evidence expectations defined)
- Release readiness (go/no-go criteria met, rollback plan in place)

---

## Testing & release governance

### SIT and UAT governance (how I keep it controlled)
- Clear **entry/exit criteria** (what must be true before testing starts / ends)
- Defined **roles and responsibilities** (who executes, who signs off, who triages defects)
- Evidence expectations (what is recorded and where)
- Defect triage with agreed **severity definitions** and turnaround expectations

### Release readiness and go-live
- Release readiness checklist (functional + non-functional)
- Explicit risk decisions (accepted / mitigated / deferred)
- Go-live runbook + rollback plan
- Hypercare plan + stabilization checkpoints
- Post-release review (what worked, what didn’t, what to improve)

---

## Traceability: from “why” to evidence
Traceability is what makes delivery defensible — especially when projects are audit-sensitive or regulated.

I aim for a clear line of sight:
- Goals → requirements → design decisions → test cases → test evidence → release notes → production outcomes

Practical examples of what traceability covers:
- A requirement tied to acceptance criteria and test cases
- A high-risk area (privacy/security/AI claims) tied to explicit evidence and decision records
- Release notes tied back to scope and verified outcomes

---

## Privacy & security governance

When delivery involves sensitive data, I treat privacy/security as gates with explicit artifacts — not side notes.

### Privacy controls (what I document and verify)
- Data categories and data minimization (what is collected and why)
- Retention and deletion rules (including user-level deletion flows)
- Consent handling (what requires consent, how it is captured and managed)
- Sub-processor / vendor considerations (what services are involved and what data they touch)

### Security controls (what I document and verify)
- Access control model (role-based access control; least privilege / need-to-know)
- Encryption approach (in transit and at rest)
- Secure environments and deployment practices
- Operational security (logging, monitoring, incident response expectations)

### DPIA-style risk thinking (Data Protection Impact Assessment)
Where appropriate, I use a DPIA-style approach:
- Identify high-risk processing early
- Define controls and mitigations
- Verify implementation and evidence
- Ensure responsibilities and escalation paths are clear

---

## AI governance (when AI is involved)

When AI is part of the product, governance is about *claims*, *transparency*, *boundaries*, and *evidence*.

### 1) Claims boundaries and user-facing clarity
- Define what the AI feature does and does not do
- Ensure user-facing text and outputs stay within validated claims
- Include appropriate disclaimers when needed (e.g., not diagnostic / not medical advice)

### 2) Provenance and transparency
- Make it clear what produced each output (e.g., AI estimate vs device reading vs manual entry)
- Where relevant, preserve provenance in history and audits (source labels and device metadata)

### 3) Human oversight and escalation paths
- Define who reviews issues, what triggers escalation, and how decisions are made
- Ensure edge cases and risk scenarios have clear handling (including user support flows)

### 4) Validation and evidence artifacts
- Maintain validation artifacts appropriate to the domain and claims
- Keep analysis reproducible where possible (scripts, datasets structure, methods summaries)
- Document limitations and known constraints (performance boundaries, device/OS constraints)

### 5) Monitoring and drift awareness
- Track stability and quality signals (error rates, failure modes, data quality issues)
- Where applicable, define what “drift” looks like and how it is detected/responded to

---

## What strong delivery governance looks like in practice

- Predictable cadence and reporting
- Clear ownership of decisions
- Transparent risks and dependencies (kept current)
- Controlled scope and change management
- Traceability from requirements to verified outcomes
- Release discipline (readiness, rollback, monitoring, stabilization)

---

Next: 🔎 <a href="/project-delivery/sdlc/">SDLC in practice</a> · <a href="/project-delivery/agile-scrum/">Agile &amp; Scrum</a> · <a href="/project-delivery/waterfall-stage-gate/">Waterfall / stage-gate</a>

