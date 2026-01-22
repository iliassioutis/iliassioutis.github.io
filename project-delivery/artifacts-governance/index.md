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
  - **Availability:** how consistently the service should be reachable for users  
    - **Uptime target:** the percentage of time it should be “up” and usable (for example, “available 99.9% of the time”).  
    - **Acceptable downtime:** what interruptions are tolerated and when (for example, a short maintenance window at night).  
    - **Resilience:** how well the system continues to work when something goes wrong (for example, if one server/service is slow or down, the rest of the app should still function).  
    - **Recovery expectations:** how quickly service should be restored after an outage (for example, “restore core functions within X minutes”).  
    - **User impact rules:** what the user should experience during partial outages (for example, “read-only mode” or “show a clear message and retry automatically”).  
  - **Reliability:** consistent behavior over time (error rates, retries, data consistency, **graceful degradation — key functions still work in a reduced mode when a dependency fails**, clear fallback behavior)  
  - **Auditability:** evidence-ready logs and traceability (who did what, when, and why; change history)  
  - **Observability:** monitoring/alerting and diagnostics (metrics, logs, traces) to detect and troubleshoot issues  
  - **Usability:** user experience expectations (clarity, accessibility, helpful error messages, and how easy core tasks are to complete)  
    - Includes minimizing **unnecessary steps and confusion** in the most important user flows (for example: sign-up/login, onboarding, completing a measurement, pairing a device, starting a teleconsultation, or uploading a file).

How this shows up in my work (example patterns):
- Turning “feature requests” into **testable acceptance criteria** (including security/privacy constraints, not just UI behavior).
- Capturing platform constraints and behavior differences (e.g., mobile platform retention, provenance labeling rules, device compatibility boundaries).

---

### 2) Solution notes and decision records
These make architecture decisions explicit and traceable (especially important when integrations, data flows, or regulated constraints exist).

- **Solution notes / Architecture decision records (ADRs)**  
  Why a decision was taken, alternatives considered, risks, and impacts.
- **Integration notes**  
  API contracts, message schemas, edge cases, retries/timeouts, failure modes, and **run ownership** (who monitors the integration, who responds to incidents, and who maintains keys/configuration, deployments, and support procedures).
- **Data flow notes**  
  What data is collected, where it is processed, what is stored, retention/deletion rules, and access controls.

How this shows up in my work (example patterns):
- Documenting **on-device AI processing boundaries** (what is processed on-device, what is not uploaded/stored).
- Defining end-to-end data handling rules for **Bluetooth device integrations** (device → app → backend → clinician view), including integrity checks and traceability.

---

### 3) Testing strategy and evidence plan
This is how I make quality measurable and defensible (not just “we tested it”).

- **Test strategy**  
  A clear, shared plan for *how* we will prove the solution works before release: what will be tested (and what won’t), the test levels (unit → integration → system), who is responsible for each activity, which environments and test data we will use, the entry/exit criteria for each phase, and what “evidence” we will capture (test cases, results, defects, and sign-offs) for go/no-go decisions.
- **System Integration Testing (SIT)** plan  
  Cross-component validation of the full system working together (client apps, backend services, third-party services, and external integrations) — focusing on end-to-end journeys, data integrity across boundaries, security/permission behavior, and failure handling.  
  Defines scope and environments, required test data/accounts, responsibilities, test scenarios (including edge and failure cases), evidence to capture, and clear entry/exit criteria (e.g., environments stable, integrations reachable, critical journeys pass, defect thresholds met, and agreed sign-offs completed).
- **User Acceptance Testing (UAT)** plan  
  Structured validation that the solution meets real user and business needs in realistic workflows (end-to-end scenarios, including exceptions), using clear acceptance criteria and agreed sign-off rules.  
  Defines who participates (business users, clinicians, operations), what is in/out of scope, the test environment and data setup, how issues are logged and triaged, pass/fail thresholds, and the final approval process (including any required evidence or documentation).
- **Test evidence** (when appropriate)  
  What is captured and where (test cases, results, defect logs, screenshots/logs, summaries).

How this shows up in my work (example patterns):
- Structuring testing so it progresses from **unit → component → integration → system**, then SIT/UAT readiness.
- Creating a reproducible evidence trail for sensitive features (security controls, retention/deletion behavior, provenance labeling).

---

### 4) Release plan and operational readiness
These artifacts reduce production risk and make go-live predictable.

- **Release plan**  
  How we move changes safely into production: target environments (development / test / staging / production), the deployment sequence and responsibilities, **post-deployment validation steps** (a short set of checks to confirm the release is working as intended), and a clear rollback plan if something goes wrong.  
  *Post-deployment validation typically includes:* service/app availability, key user flows working, integrations responding, monitoring/alerts green, and any critical data or background jobs behaving normally.
- **Go-live runbook**  
  A step-by-step “day-of-release” playbook that defines **who does what, in what order**, including timing, communications, and clear **checkpoints** to confirm each stage is working (for example: deployment completed, key services responding, critical user flows pass, integrations healthy, monitoring shows no spikes). It also defines **decision points** (continue / pause / rollback) and who has the authority to make those calls.
- **Monitoring and alerting plan**  
  How we **detect problems early** and **respond quickly** once the system is live. It defines:  
  - **What we watch and why:** the key “health signals” that indicate the service is working as expected.  
  - **What triggers an alert:** clear thresholds and conditions (so alerts are meaningful, not noisy).  
  - **Who is notified and how:** escalation paths and response expectations (who looks first, who owns the fix, when to involve vendors).  
  - **What we do when an alert fires:** a standard response flow (check dashboards → confirm impact → mitigate → root-cause analysis → prevent recurrence).  

  Typical signals include:  
  - **Availability:** can users successfully log in and use the core features right now (service reachable / core journeys working).  
  - **Error rates:** spikes in failures (for example, login failures, API errors, payment failures, device-sync failures).  
  - **Performance:** pages/screens/loading times staying within acceptable limits; slowdowns detected early.  
  - **Integration health:** third-party or internal integrations failing (timeouts, authentication issues, webhook delivery failures, dropped messages).  
  - **Data health (if applicable):** data pipelines/jobs running on schedule, no missing/duplicated data, and key data checks passing.
- **Hypercare plan**  
  A defined post-release **stabilization period** (for example, the first 24–72 hours or first 1–2 weeks) where the team actively watches the system and responds quickly to issues. It specifies:  
  - **What we monitor:** key dashboards/alerts, error rates, performance, and critical user journeys.  
  - **How issues are handled:** a triage process (log → classify severity/impact → assign owner → target fix/mitigation).  
  - **Who gets involved and when:** clear escalation paths (support → engineering → product/operations → vendors) and on-call/availability expectations.  
  - **What “stable” means:** measurable success criteria for reaching “steady state” (e.g., no critical incidents, error rates back to baseline, support tickets within normal levels, and agreed KPIs holding consistently).

How this shows up in my work (example patterns):
- Using a structured **go/no-go release decision** with explicit criteria (feature complete, test complete, risks accepted/mitigated).
- Ensuring operational readiness for real-world usage (incident triage, rollback, and post-release stabilization).

---

## Governance tools I use repeatedly

### Risk and dependency control
- **RAID log (Risks, Assumptions, Issues, Dependencies)**  
  A living log reviewed regularly. For each item, it captures:  
  - **What it is:** the risk/assumption/issue/dependency stated clearly  
  - **Owner:** who is responsible for driving it to resolution  
  - **Current position:** where it stands right now (e.g., newly identified / being investigated / agreed action in progress / resolved)  
  - **Impact if it happens:** what it would affect (scope, timeline, cost, quality, compliance, operations)  
  - **Planned response:** what we will do to reduce likelihood, reduce impact, or remove the blocker (actions + due dates)  
  - **Decision points:** what needs approval/confirmation, and by when
- **Dependency mapping**  
  A clear view of everything the delivery relies on (and what depends on us), so surprises don’t land late in testing or release:  
  - **External services & APIs:** third-party endpoints, rate limits, authentication flows (login/token exchange), **service commitments (SLA — Service Level Agreement, e.g., uptime and support response expectations)**, and change-notification channels (how we learn about breaking changes).  
  - **Vendor components & SDKs:** version constraints, licensing/usage terms, upgrade cadence, and known limitations that affect scope.  
  - **Platform constraints:** mobile operating system (OS) versions, app-store rules, device permissions, and background/foreground behavior.  
  - **Device compatibility boundaries:** supported device models/firmware ranges, Bluetooth profiles, SDK/device pairing steps, and explicit “not supported” cases.  
  - **Data & infrastructure dependencies:** environments (development/test/staging/production), certificates/keys (to secure connections), **feature flags (toggles that turn features on/off per environment or user group without a new release)**, **messaging/queues** (a reliable “inbox” between systems for requests/events that don’t happen instantly, so work can be retried safely and not lost during spikes or temporary outages), and data pipeline readiness (where applicable).  
  - **Integration sequencing:** which integrations must be ready first, **shared test windows (agreed time slots when multiple teams are available to test together)**, and who provides test accounts/data.  
    - *Example:* “Tuesday 10:00–12:00” where the mobile team, backend team, and a third-party provider are all online to validate an end-to-end flow (e.g., create a session → call an external API → receive a callback/webhook → confirm the mobile UI updates).  
  - **Operational dependencies:** support coverage, monitoring/alerting readiness, and escalation contacts for third parties during go-live.  
  - **Release coupling:** anything that must ship together (mobile + backend + web), plus rollout order and backward/forward compatibility assumptions.

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

