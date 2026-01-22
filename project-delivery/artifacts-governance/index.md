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
  - **External services & APIs:** third-party endpoints, rate limits, authentication flows (login/token exchange), **service commitments (SLA — Service Level Agreement, e.g., uptime and support response expectations: how often the service is available and how quickly support responds when something breaks)**, and change-notification channels (how we learn about breaking changes).  
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
  A simple responsibility map that makes ownership explicit and prevents “everyone thought someone else was doing it”:  
  - **Responsible (R):** the person/team doing the work (builds, writes, executes, fixes).  
  - **Accountable (A):** the single owner who signs off and is answerable for the outcome (one “A” per deliverable).  
  - **Consulted (C):** subject-matter experts who provide input before decisions are finalized (two-way communication).  
  - **Informed (I):** stakeholders who need updates after decisions or milestones (one-way communication).  
  - **Where I use it most:** requirements sign-off; solution design/architecture decisions; security & privacy reviews; test ownership (SIT/UAT); release readiness and go-live approvals; third-party **vendor deliverables**; and **support handover**.

    - **Third-party vendor deliverables**  
      The concrete inputs we need from external providers so we can build, test, and release confidently:  
      - **Documentation:** API specifications, software development kit (SDK) integration guides, configuration instructions, known limitations.  
      - **Access:** sandbox/test environments, test accounts, credentials/keys/certificates (and how they are rotated/replaced).  
      - **Technical artifacts:** required SDK/library versions, device firmware ranges, reference implementations or sample payloads where available.  
      - **Operational inputs:** support and incident contacts, incident handling process, maintenance windows, and change-notification channels (how we learn about breaking changes).  
      - **Fixes & compatibility updates:** agreed bug fixes/patches, compatibility updates, release notes, and committed timelines.

    - **Support handover**  
      The structured transition from “build mode” to “run mode”, so the service can be supported reliably after go-live:  
      - **Ownership model:** who supports what (product/app team vs operations/support vs vendors), primary/backup owners, and escalation paths (including on-call where applicable).  
      - **Operational playbooks (runbooks):** common issues, troubleshooting steps, restart/retry procedures, and “what to do first” checklists.  
      - **Monitoring & alerts:** what is monitored, alert thresholds, who receives alerts, and the expected response steps.  
      - **Access & permissions:** who can access logs, dashboards, admin consoles, and production support tools (and how access is granted/revoked).  
      - **Incidents & hotfixes:** triage flow, severity levels, communication steps, how fixes are deployed safely, and post-incident review (what happened and what we change).  
      - **Knowledge transfer:** walkthrough sessions and Q&A, plus links to the latest documentation so support can operate without the delivery team.  
  - **How it helps in practice:**  
    - avoids duplicated effort (two teams doing the same thing)  
    - avoids gaps (no one assigned to a critical task)  
    - speeds decisions (clear approver)  
    - clarifies cross-team dependencies (who must be involved, and when)  
  - **Example deliverables to map (illustrative):**  
    The idea is to make it clear *what we need*, *who provides it*, *when it’s due*, and *how we know it’s “done”*. Typical items include:

    - **Requirements / specification (what we are building):**  
      A clear description of the problem, scope, and expected behavior — e.g., user flows, key rules, constraints, and acceptance criteria (what must be true for this to be considered complete).

    - **Integration contract (how systems talk to each other):**  
      The “agreement” between systems — e.g., API endpoints, request/response formats, authentication method, error codes, timeouts, retry rules, and versioning (what happens if one side changes).

    - **Test plan and test evidence (how we prove it works):**  
      What will be tested, by whom, in which environment, using which data — plus proof of results (test cases executed, screenshots/logs, defect list, retest confirmation, and sign-off where required).

    - **Release readiness checklist (how we know we’re safe to launch):**  
      A short go-live checklist confirming prerequisites are met — e.g., deployments prepared, monitoring in place, known risks accepted, rollback plan ready, support contacts confirmed, and approvals completed.

    - **Go-live runbook (the step-by-step launch playbook):**  
      A practical “do this in this order” guide — who performs each step, exact deployment actions, verification checks after each step, decision points (go/stop), and who to call if something fails.

    - **Post-release hypercare ownership (who supports after launch):**  
      Clear ownership during the stabilization period — who monitors, who triages issues, response expectations, escalation paths (including vendors), daily check-ins if needed, and criteria for declaring the system “stable” and moving to normal operations.

- **Decision paths**  
  How decisions are made and recorded, so the team can move fast without confusion — and so approvals are clear when governance is required:  
  - **What kinds of decisions we make (and why they matter):**  
    - **Scope and priority:** what we will deliver now vs later (and what we will *not* deliver), to keep timelines and expectations realistic.  
    - **Solution and integration approach:** how systems connect and behave end-to-end (interfaces, data flows, error handling), to avoid late surprises during testing and rollout.  
    - **Security and privacy checkpoints:** what data is processed, who can access it, how it is protected (encryption, retention/deletion), and whether extra safeguards are required before go-live.  
    - **Release readiness:** whether we are safe to launch (evidence complete, risks understood, rollback plan ready, support on standby) and who gives the final go/no-go.  
    - **Live-incident actions:** what we do when something breaks in production (triage, temporary mitigations, disabling a feature, rollback/hotfix) and who is authorized to trigger each action.  
  - **Who can decide:**  
    Named owners for each decision type, so responsibility is explicit (and decisions don’t stall):  
    - **Product Owner:** scope and priority (what ships now vs later).  
    - **Technical Lead / Architect:** solution and integration choices (how it works end-to-end).  
    - **Security / Privacy owner:** security controls and privacy gates (what data is processed, how it’s protected, retention/deletion).  
    - **Delivery Lead:** decision orchestration for release readiness (ensures inputs are complete, brings the right people together, runs the go/no-go).  
    - **Operations / Support lead (when relevant):** production readiness and incident actions (runbooks, monitoring, escalation, hotfix/rollback coordination).

  - **How decisions are made:**  
    A consistent process so choices are defensible and repeatable:  
    - **Decision criteria:** value vs effort, delivery impact (time/cost), risk level, and compliance/regulatory implications.  
    - **Required inputs:** impact analysis (what changes and who is affected), options and trade-offs, test evidence/results where applicable, and any security/privacy assessment needed.  
    - **Decision timing:** a clear expectation for how quickly a decision is made once inputs are complete — e.g., **same-day for routine backlog changes** such as re-ordering tickets (what to do first/next), swapping one similar-effort item because a dependency is blocked, or moving a low-priority item to a later sprint/release; and longer lead time for higher-risk decisions that require reviews/approvals (e.g., integration changes, security/privacy gates or go/no-go).

  - **How decisions are documented:**  
    A lightweight decision log so the “why” is not lost:  
    - **Record:** what was decided, why, alternatives considered, date/time, decision owner(s), and any constraints/assumptions.  
    - **Actions:** follow-up tasks, owners, due dates, and where the evidence lives (links to tickets/docs/test results).  
    - **Visibility:** stored in a shared place the team actually uses (project wiki, ticketing system, or a single decision-log page).
  - **When escalation is triggered:**  
    - changes that affect timeline/cost materially, or introduce new dependencies  
    - anything with privacy/security impact (sensitive data, permissions, retention, access control)  
    - **regulated or safety-relevant claims (especially with AI):** any feature, wording, chart, or workflow that could be interpreted as *medical/clinical advice, diagnosis, treatment guidance, or risk scoring* — or that could change how a user acts (e.g., “high blood pressure”, “arrhythmia detected”, “stress level is clinically high”). This includes:  
      - adding/updating **AI-derived outputs** (new metrics, thresholds, labels, or “normal/abnormal” ranges)  
      - changing **how results are presented** (language, icons/colors, alerts, recommendations, call-to-action)  
      - any **marketing/app-store copy** that strengthens claims (“validated”, “clinically proven”, “detects”, “diagnoses”)  
      - changes that affect **provenance and transparency** (AI vs device vs manual), or could confuse the source of a measurement  
      - anything that may require **additional evidence/validation, review, or sign-off** (e.g., clinical validation dossier updates, legal/compliance review)  
    - repeated test failures, high-severity defects, or integration instability near release  
    - unclear ownership, blocked teams, or vendor delays that threaten milestones  
  - **Escalation path:** who is notified first, who must approve next, and what “stop / proceed” rules apply (e.g., pause release until risks are accepted or mitigations are in place).

---

### Change control

Change control is how I keep delivery predictable when new requests appear, priorities shift, or constraints change. The goal is not to “block” change — it is to make change **visible**, **assessed**, and **agreed**, so scope, timeline, cost, and quality stay aligned.

- **What triggers change control (typical cases)**  
  - New feature requests or “small” additions that accumulate into scope creep  
  - Changes to integrations (new third-party API requirements, SDK version changes, new device models)  
  - Security/privacy changes (new data collected, new permissions, retention/deletion changes)  
  - Quality-driven changes (fixing a defect properly vs applying a quick workaround)  
  - Delivery constraints (timeline pressure, blocked prerequisites — e.g., a third-party API/SDK or device firmware update arriving late, a test environment not ready, or a vendor sandbox being unavailable — plus app-store review findings)

- **Change request (the “what” and “why”)**  
  A short, structured record that makes the change unambiguous:  
  - **What is changing:** feature/functionality, workflow, requirement, integration, UI/UX, data handling, or operational process  
  - **Why now:** business value, user impact, compliance requirement, defect/incident response, or a **dependency constraint** (e.g., a third-party provider is deprecating an API on a fixed date, a device/SDK update is required to support a new OS release, or an app-store policy change forces an update before the next submission window)  
  - **Who requested it:** requestor + accountable owner  
  - **Priority and timing:** what is **non-negotiable** vs what can **wait** (must-have vs should-have), and any **hard external dates** we must align to (e.g., an agreed release window, an app-store review timeline, or a partner/vendor go-live date when their side is ready)  
  - **Scope boundaries:** what is included **and what is explicitly not included** (to avoid “hidden extras”)  
  - **Acceptance criteria:** how we will confirm the change is done and correct (including edge cases/non-happy paths)

- **Impact assessment (the “so what”)**  
  A lightweight but complete review of consequences, so decisions are informed:  
  - **Schedule impact:** what moves, what slips, what can be parallelized; effect on milestones/release date  
  - **Cost/effort impact:** engineering effort, testing effort, vendor effort, and any extra tools/licenses  
  - **Dependency impact:** new/changed dependencies (vendors, APIs, SDKs, devices, app-store review, environments)  
  - **Quality impact:** additional test coverage needed; **regression risk (the chance that a change breaks something that previously worked — often in related flows, shared components, or integrations)**; and any effect on the **Definition of Done** (what “complete” means, including required quality checks and evidence)  
  - **Operational impact:** monitoring/alerts, runbooks, support load, on-call/escalation readiness  
  - **Security & privacy impact (when applicable):** permissions, data classification, encryption, access controls, retention/deletion, and **sub-processors (third-party service providers we rely on to process data on our behalf — e.g., hosting, analytics, notifications — which must be assessed and controlled via contracts, access boundaries, and data-transfer safeguards)**  
  - **Risk assessment:** what can go wrong, likelihood/impact, mitigation plan, and **residual risk (the risk that remains even after mitigations are in place)**  
    - *Example:* We add retries, timeouts, and monitoring for an external API, but there is still residual risk of provider downtime during peak hours that could delay workflows.  
    - *Example:* We tighten input validation and add test coverage, but there is residual risk of an edge-case bug in a rarely used workflow that may only appear in real-world usage.  
  - **Options and trade-offs:** present a few realistic choices, and for each one explain the benefits, downsides, risks, and impact on timeline/quality — for example:  
    - **Defer to next release:** keeps the current release plan stable and lowers near-term risk, but delays user value and may require extra coordination later.  
    - **Phased rollout (gradual release):** deliver the change in controlled steps (e.g., enable for internal testers → a small pilot group → a percentage of users → everyone), so issues are detected early and can be contained or rolled back without affecting all users at once.  
    - **Limited-scope version (“minimum viable” slice):** ship only the essential part now (core workflow + safety checks), and postpone non-critical enhancements to a later iteration to meet deadlines with lower risk.

- **Decision and approval (the “go / no-go”)**  
  A clear decision path so the team can move fast without confusion:  
  - **Decision owner(s):** who approves (e.g., Product Owner for scope/priority, Tech Lead for architecture, Privacy/Security owner for controls, Delivery Lead for release coordination)  
  - **Decision outcome:** approved / rejected / deferred / approved with conditions (e.g., “only if test evidence is produced”)  
  - **Decision timing:** expected turnaround once inputs are ready (e.g., same-day for routine backlog reshuffles; scheduled review for higher-impact changes)  
  - **Documentation:** record what was decided, why, when, and any follow-up actions

- **Re-baselining (keeping expectations aligned)**  
  Once a change is approved, I update the “single source of truth” so everyone is working to the same plan:  
  - **Update the baseline plan:** scope, milestones, release date, and deliverables  
  - **Update the backlog and roadmap:** reflect the approved change in the plan — re-order what the team works on next, assign items to the right sprint or release, adjust target dates/milestones if needed, and make the new priorities visible to everyone (so delivery, stakeholders, and dependencies stay aligned)  
  - **Update RAID log (Risks, Assumptions, Issues, Dependencies):** new risks/dependencies and mitigations  
  - **Update test and release plans:** what must be re-tested, evidence required, and readiness gates  
  - **Stakeholder communication:** concise summary of what changed, why, and what it means for timeline/scope

- **How I keep it lightweight (so it doesn’t become bureaucracy)**  
  - Small changes: one-page change note + quick impact assessment + recorded decision  
  - Larger changes: require a deeper impact review, explicit sign-offs, an updated baseline plan, and **clear communications** (who needs to know, what is changing, why it’s changing, and what the new dates/scope/risks are)  
  - Always: “If it changes scope/timeline/risk materially, it gets logged and decided — not assumed.”

---

### Quality gates

Quality gates are **planned “pause-and-check” points** that confirm we are genuinely ready to move to the next stage (testing or release).  
They prevent surprises late in delivery by making readiness **explicit, evidence-based, and agreed** — especially important when multiple systems, vendors, or regulated data are involved.

Below are the typical gates I use, what they check, and what “ready” looks like.

- **Requirements readiness (before build or before serious testing starts)**  
  Ensures the team is building the *right* thing and can prove it works.  
  - **What it checks:** scope is clear; workflows are understood; acceptance criteria exist for each key item; edge cases and error behaviour are defined; non-functional expectations are known (security, performance, audit needs).  
  - **What “ready” looks like:** no critical open questions; key decisions recorded; requirements are testable (someone can write test cases directly from them).

- **Security & privacy readiness (before integration testing and before release)**  
  Ensures data handling is correct and safe, and that access and retention rules are implemented.  
  - **What it checks:** what data is collected and why; permissions/consents; encryption in transit/at rest; access control roles; retention and deletion rules; logging/audit needs; third parties/sub-processors are known and approved where applicable.  
  - **What “ready” looks like:** the agreed controls are implemented and reviewed; privacy/security risks are recorded with mitigations; any required approvals are completed.

- **System Integration Testing readiness (SIT readiness) (before SIT begins)**  
  Ensures the integrated “end-to-end” system can be tested without constant blockers.  
  - **What it checks:** stable build(s) available; test environment is working; integrations are reachable; required credentials/certificates are in place; test accounts and test data exist; key dependencies (internal and third-party) are available.  
  - **What “ready” looks like:** the end-to-end flow can be exercised; known dependency constraints are documented; owners are available to support integration testing.

- **User Acceptance Testing readiness (UAT readiness) (before UAT begins)**  
  Ensures UAT is focused, realistic, and produces a clear decision (accept / fix / defer).  
  - **What it checks:** UAT scope and scenarios are defined; who will test is agreed; what evidence is needed is clear (screenshots, logs, test notes); entry/exit criteria are defined; sign-off rules are agreed (who approves and what “pass” means).  
  - **What “ready” looks like:** users/testers can run the intended workflows; defects and feedback can be logged and triaged; acceptance decision criteria are unambiguous.

- **Release readiness (go/no-go) (before production release)**  
  Ensures the system is safe to release and can be supported after release.  
  - **What it checks:** required testing is complete; critical defects are resolved or formally accepted with mitigations; monitoring/alerts are configured; support handover is complete; rollout steps are documented; rollback plan is tested/credible; communications are ready.  
  - **What “ready” looks like:** a structured **go/no-go** decision can be made with confidence, based on evidence and agreed criteria — not guesswork.

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

