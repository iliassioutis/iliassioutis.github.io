---
layout: default
title: Service Delivery & Partner Management (how I run it)
---

<blockquote>
🏠 <a href="/">Back to homepage</a> · <a href="/project-delivery/">Project Delivery & Methods</a>
</blockquote>

This page explains **how I run service delivery and partner/vendor-led technical projects** end-to-end — from initiation and planning through delivery, release, and operational handover.

It is written to be **practical and explicit**:
- I use standard project management terminology (and I explain it in parentheses).
- If I use an abbreviation, I first write the full term and then the abbreviation.
- Each section includes examples of what “good” looks like in real delivery work.

---

## How I work (quick profile) {#how-i-work}

I’m a technical project manager who delivers outcomes across **internal engineering, operations, and external partners** — with a focus on **predictable execution, safe releases, and production readiness**.

In partner-led delivery, the operating model I most often run is:
- **Vendors build components** (code/API/SDK/services),
- **Internal teams integrate and operate** (Continuous Integration / Continuous Delivery (CI/CD), observability, security review, production ownership),
- and I provide the **single delivery system** across both sides: plan, governance, evidence, escalation, and go/no-go readiness.

---

## On this page {#on-this-page}

- [How I work (quick profile)](#how-i-work)
- [What “service delivery” means in practice](#what-is-service-delivery)
- [Operating model (how I run multiple projects at once)](#operating-model)
- [Budget & resource management (forecast vs actual, burn rate, capacity planning)](#budget-resourcing)
- [Project lifecycle (hybrid: Agile + stage-gate)](#project-lifecycle)
- [Delivery leadership & team management (objectives, coaching, leading without authority)](#delivery-leadership)
- [Technology evaluation (fit, risk, Proof-of-Concept (PoC), decision record, rollout plan)](#tech-eval)
- [Partner & vendor management lifecycle](#vendor-lifecycle)
- [Vendor performance management (operating rhythm, QBR, escalation ladder)](#vendor-performance)
- [IT procurement process (RFI/RFP, evaluation, award, onboarding)](#it-procurement)
- [Contracts, statements of work, and SLAs](#contracts-slas)
- [Contract negotiation & contract management (commercial controls)](#contract-negotiation)
- [Delivery governance (cadences, reporting, decisions)](#delivery-governance)
- [Release & change management](#release-change)
- [Release execution (cutover, go/no-go, rollback, hypercare)](#release-execution)
- [24/7 production & peak-period release discipline (freeze windows, staged rollout, observability-first go/no-go)](#high-scale)
- [Service delivery in production (Business-as-Usual (BAU) operations: incidents, problems, service reviews)](#bau-ops)
- [Quality management (testing, evidence, acceptance)](#quality)
- [Risk, dependency, and escalation control](#risk-deps)
- [Delivery metrics and performance signals](#metrics)
- [Glossary (plain-language definitions)](#glossary)

---

## What “service delivery” means in practice {#what-is-service-delivery}

**Service delivery** is the discipline of making sure a technology service (or a partner-delivered component of it):
- is delivered **on time** (schedule),
- within **agreed cost** (budget),
- with **agreed quality** (fit-for-purpose, tested, stable),
- and can be **operated** after go-live (monitoring, support, incident handling).

It is not just “project tracking”. It includes:
- delivery governance (how decisions are made and recorded),
- partner/vendor performance management (how we ensure external teams deliver),
- release discipline (how we ship safely and repeatedly),
- and operational readiness (how the service is supported in production).

**Typical outcomes I am accountable for:**
- predictable delivery (clear plan, clear scope, visible risks),
- reliable releases (go/no-go decisions based on evidence),
- partners aligned to goals and standards (quality, security, ways of working),
- reduced production incidents (because readiness is real, not assumed).

<blockquote>
⬆ <a href="#on-this-page">Back to navigation</a>
</blockquote>

---

## Operating model (how I run multiple projects at once) {#operating-model}

When multiple initiatives run in parallel, I keep one shared plan as the source of truth and run predictable check-ins (e.g., weekly delivery review, monthly vendor scorecard) to keep everyone aligned.

### 1) Intake and prioritization
This is how work becomes an approved initiative (not “random requests”):

- **Intake (request capture):** a short structured form or ticket (what is needed, why now, expected value, deadlines, dependencies).
- **Triage (quick assessment):** size, risk, impact, and which teams are needed.
- **Prioritization (ordering):** decide what is most important now and what can wait (based on value, risk, urgency, and capacity).

*Example (how this looks as a decision statement):*  
“We will deliver A and B in the next release because they reduce operational risk and unblock a key partner dependency. C is valuable but will be moved to the following release due to capacity and test constraints.”

### 2) Portfolio view (lightweight but real)
I keep a visible view of:
- key milestones (what must happen by when),
- owners (who is accountable for each deliverable),
- dependencies (what we are waiting for / what depends on us),
- and top risks (what can derail schedule/quality).

This is not bureaucracy — it prevents surprises.

### 3) Roles and accountability (RACI)
I use **RACI (Responsible, Accountable, Consulted, Informed)** to prevent “everyone thought someone else was doing it”.

- **Responsible:** the person/team doing the work (build/test/operate).
- **Accountable:** the single owner who signs off and is answerable.
- **Consulted:** subject matter experts who provide input before decisions.
- **Informed:** stakeholders who need updates after decisions.

*Example (vendor-delivered API integration — RACI):*
- **Accountable (single owner):** Technical Project Manager / Service Delivery Manager (end-to-end delivery ownership and sign-off coordination)
- **Responsible (do the work):**
  - Vendor engineers (build the component)
  - Internal integration engineers (integrate, configure, and validate the component within internal systems)
  - **Development and Operations (DevOps) team** (set up and maintain build/deploy automation, manage environments and configuration, and support the release execution process)
  - **Site Reliability Engineering (SRE) team** (set up monitoring and alerting, define reliability/performance checks, and ensure incident-response readiness for production)
- **Consulted (must review/advise):**
  - Product Manager / Product Owner (requirements and priorities)
  - Security / Information Security (data protection, access control, risk review)
  - Operations and Support (handover requirements, runbooks, supportability)
- **Informed (kept updated):** Commercial/Procurement owner (contract and budget) + key stakeholders

<blockquote>
⬆ <a href="#on-this-page">Back to navigation</a>
</blockquote>

---

## Budget & resource management (how I keep delivery “within budget” and resourced) {#budget-resourcing}

“Within budget” means I actively manage the **cost baseline** (the agreed cost plan) and keep stakeholders informed about **forecast vs actual** (what we expected to spend vs what we actually spent).  
I treat budget and resourcing as control systems (not afterthoughts): if scope or risk changes, I quantify the impact, propose options, and re-baseline decisions explicitly.

### Budget tracking basics (forecast vs actual, burn rate, variance)

**Core concepts (plain definitions):**
- **Budget baseline (agreed budget):** the approved cost envelope for a project/workstream (internal effort + vendor spend + tools/services where applicable).
- **Actuals (actual spend):** what has been invoiced/recorded to date (or time booked internally).
- **Forecast (expected spend):** what we expect total spend to be by the end, based on current plan and known risks.
- **Variance:** the gap between budget baseline and forecast (or forecast vs actual at a point in time).
  - *Example:* “We are forecasting +€20k over baseline due to additional test cycles and vendor change requests.”
- **Burn rate:** how quickly budget is being consumed per unit of time (e.g., €/week), used to predict when we hit budget limits.
- **Estimate at Completion (EAC):** the latest estimate of total cost when the project completes.
- **Estimate to Complete (ETC):** what is left to spend from now until completion.

**What I track (minimum set):**
- baseline budget (by workstream if needed: build/test/release/support readiness)
- actuals to date
- forecast to complete (EAC)
- variance (EAC – baseline) with a short explanation
- key cost drivers (e.g., vendor days, test cycles, environments/tools)
- upcoming commitments (e.g., milestone payments, renewal dates)

**How I run it (cadence):**
- **Weekly (delivery view):** update forecast assumptions when scope, timeline, or risk changes (especially if dependencies slip or extra testing is required).
- **Monthly (finance/commercial view):** reconcile actuals, confirm invoice status, and validate forecast with stakeholders (so surprises don’t accumulate).

**How I explain variance (so it’s actionable, not defensive):**
- **Driver:** what changed (scope, schedule, risk, or vendor rates).
- **Impact:** quantified € and timeline impact.
- **Options:** at least two paths (reduce scope, move date, add capacity, renegotiate vendor terms).
- **Decision:** recorded (approval + re-baseline if needed).

*Example (simple but real-world):*  
“Baseline €100k. Actuals €40k. Current burn rate €10k/week. With one additional integration test cycle and 2 vendor change requests, EAC becomes €115k (+€15k variance). Options: (A) defer non-critical items, stay within €100k, (B) keep scope, approve +€15k, (C) renegotiate change request scope and cap at +€8k.”

### Resource planning (capacity, allocation, constraints across parallel projects)

**Resource planning** is ensuring we have enough capacity (available people/time) and the right skills at the right time — across internal teams and vendors.

**Core concepts (plain definitions):**
- **Capacity:** how much work a team/person can realistically take on in a period (not theoretical max).
- **Allocation:** how that capacity is split across parallel initiatives (e.g., 40% Project A, 60% Project B).
- **Constraint:** something that limits delivery (e.g., 1 QA engineer, fixed release windows, external dependency).
- **Full-Time Equivalent (FTE):** a planning unit meaning “one full-time person’s capacity” (useful when combining partial allocations).
- **Critical path:** the sequence of tasks that determines the earliest possible finish date (if a critical-path task slips, the project slips).

**How I plan resources in practice:**
- build a simple capacity map per team/role (engineering, QA, DevOps/SRE, security review)
- identify hard constraints early (specialists, approval gates, vendor lead time)
- protect critical activities (integration testing windows, release readiness, operational handover)
- explicitly trade off **scope vs capacity vs date** (so we don’t silently overload teams)

**When multiple projects compete:**
- I keep a portfolio-level view (milestones + owners + dependencies + capacity)
- I escalate early when overall demand exceeds capacity, with clear options:
  - reduce scope on lower-priority work
  - re-sequence work (move non-critical items out of peak windows)
  - add temporary capacity (vendor/internal), with cost impact quantified
  - adjust timeline (re-baseline schedule with stakeholder approval)

**Vendor resourcing clarity (important in partner-led delivery):**
- confirm vendor roles and named resources (who is actually delivering)
- confirm availability assumptions (holidays, on-call coverage, time zones)
- ensure rate cards / day rates / escalation rates are known (so forecast is reliable)
- align “who approves extra effort” to prevent unplanned cost growth

<blockquote>
⬆ <a href="#on-this-page">Back to navigation</a>
</blockquote>

---

## Delivery leadership & team management (how I lead teams and vendors to outcomes) {#delivery-leadership}

In service delivery, “leadership” often means **delivering outcomes through people you don’t directly manage** (internal teams, external vendors, stakeholders).  
I treat leadership as a practical system: clear objectives, clear ownership, predictable cadences, fast feedback, and explicit decision-making.

### Delivery leadership (leading without direct authority)

**Leading without authority** means I influence outcomes through:
- **clear accountability** (RACI — Responsible/Accountable/Consulted/Informed),
- **shared goals** (what success looks like, measurable),
- **cadence and visibility** (weekly checkpoints, risk/issue logs),
- and **fast conflict resolution** (surfacing trade-offs early and recording decisions).

**What I do in practice:**
- set a “single source of truth” (plan, RAID log (Risks/Assumptions/Issues/Dependencies), decision log)
- translate goals into executable work (epics/stories/work packages) with owners and acceptance criteria
- remove blockers (dependency chasing, escalations, decision facilitation)
- protect quality and release discipline (evidence-based go/no-go, rollback readiness)
- keep alignment when priorities change (scope/date/cost trade-offs made explicit, re-baselined)

*Example (delivery leadership statement):*  
“I don’t rely on hierarchy. I rely on clarity: one plan, named owners, weekly commitments, evidence-based readiness, and quick escalation when risk crosses thresholds.”

### Coaching cadence and feedback approach (how I improve performance)

Even without line management, I use lightweight coaching rhythms:
- **Weekly 1:1-style check-ins (delivery-focused):** what’s blocked, what’s at risk, what support is needed.
- **After key events (release/incident):** short retrospectives (what happened, what we learned, what changes).
- **Feedback style:** specific, timely, and behavior-based (not personal).

A simple structure I use for feedback is **SBI (Situation–Behavior–Impact)**:
- **Situation:** when/where it happened
- **Behavior:** what was observed (facts)
- **Impact:** why it matters (delivery risk, quality, stakeholder trust)
- **Next step:** what “good” looks like and how we’ll support it

*Example (SBI-style):*  
“In yesterday’s release prep (situation), the test evidence wasn’t shared before go/no-go (behavior). That increases rollback risk and slows decisions (impact). Next release, we’ll publish the evidence pack 24 hours earlier and confirm readiness in the checklist (next step).”

### People management (when I have formal line-management responsibility)

In many roles I’ve led delivery through cross-functional teams and vendors without formal line authority; where I do have direct reports, I apply the structure below:

**Setting objectives (clear and measurable):**
- I use **SMART goals** (Specific, Measurable, Achievable, Relevant, Time-bound) or team-aligned objectives.
- I connect goals to delivery outcomes (predictability, quality, incident reduction, stakeholder satisfaction).

**Performance expectations and reviews (fair and evidence-based):**
- define expectations upfront (role responsibilities, quality bar, behaviors)
- track progress using observable outcomes (deliverables, quality signals, collaboration)
- run regular check-ins so review time has no surprises

**Development and mentorship (growth plan):**
- identify strengths + gaps (skills and behaviors)
- agree a short development plan (training, shadowing, stretch assignments)
- review progress monthly/quarterly

### Managing vendor teams and internal contributors together (one operating rhythm)

To keep multi-party delivery effective, I standardize:
- **working agreements:** tools, response times, definition of done, escalation path
- **cadences:** weekly delivery checkpoint, monthly scorecard, QBR (Quarterly Business Review)
- **decision rights:** who can approve changes, who can accept deliverables
- **conflict handling:** raise trade-offs early; avoid “silent scope” and “late surprises”

<blockquote>
⬆ <a href="#on-this-page">Back to navigation</a>
</blockquote>

---

## Project lifecycle (hybrid: Agile + stage-gate) {#project-lifecycle}

In practice, many environments are **hybrid**:
- Agile (iterative delivery and fast feedback),
- plus stage-gates (formal checkpoints) when risk, compliance, or release control requires it.  
This fits well with mainstream PM guidance: plan, execute, monitor/control, close — with governance appropriate to risk. 

### Phase 1 — Initiation
- **Project charter (definition):** a short “contract” that defines purpose, scope boundaries, success criteria, key stakeholders, and constraints.
- **High-level plan:** milestones, dependency map, risks, and initial resourcing.

*Example (charter clarity):*  
“Goal: deliver partner integration X with end-to-end flow Y. Out of scope: legacy migration Z. Success: 99%+ transaction success in production for key flow, verified via monitoring dashboard.”

### Phase 2 — Planning
- **Scope baseline:** what we will deliver (and what we explicitly will not deliver).
- **Schedule baseline:** milestones and target dates.
- **Cost baseline:** budget and commercial constraints (where relevant).
- **Quality plan:** testing strategy, acceptance criteria, evidence expectations.
- **Communication plan:** who gets what updates, how often, and via which channel.

### Phase 3 — Execution (delivery)
- **Work breakdown:** epics/features/stories (or work packages) with owners.
- **Delivery cadence:** demos, checkpoints, and integration test windows.
- **Dependency control:** tracked and escalated early.

### Phase 4 — Monitoring & control
This is where delivery stays predictable:
- **Status tracking:** progress vs plan (schedule), spend vs budget (cost), quality signals (defects/incidents).
- **Change control:** scope changes are assessed and approved (not “quietly added”).
- **Risk & issue management:** risks are prevented; issues are resolved with owners and deadlines.

### Phase 5 — Release & closure
- **Go/no-go decision:** release readiness confirmed with evidence.
- **Handover to operations/support:** runbook, monitoring, escalation paths.
- **Post-release review:** lessons learned and improvement backlog.

<blockquote>
⬆ <a href="#on-this-page">Back to navigation</a>
</blockquote>

---

## Technology evaluation (how I assess new technologies before committing) {#tech-eval}

Service delivery roles often require making **technology choices** that balance speed, reliability, cost, and risk.  
When a new tool/platform/pattern is proposed, I evaluate it with a lightweight but disciplined approach so decisions are **traceable** and rollout is **safe in production**.

### When I run a technology evaluation

Typical triggers:
- a new vendor platform or managed service is introduced
- a new integration approach/pattern is proposed (e.g., message bus vs direct API)
- a change is needed for scale/reliability (observability, caching, DR approach)
- security/compliance needs change (data handling, access model, auditability)
- costs are rising and we need a better total cost of ownership (TCO)

### Evaluation criteria (fit, risk, operational impact, cost, security)

I score options against consistent criteria (and adjust weights based on criticality/risk).

**Core criteria I use (plain definitions):**
- **Functional fit:** does it meet requirements (including integrations and edge cases)?
- **Delivery maturity:** how predictable is delivery (tooling maturity, documentation, known pitfalls)?
- **Operational impact (BAU):** how it affects on-call, monitoring, runbooks, incident handling, and support workload.
- **Security & compliance:** access control model, encryption support, auditability/logging, data residency (if relevant), and vendor assurance.
- **Cost / TCO (Total Cost of Ownership):** licenses + infrastructure + support + migration/exit costs (not only the sticker price).
- **Scalability & reliability:** performance under load, availability options, DR/BCP compatibility, failure modes.
- **Maintainability:** team skills required, complexity, upgrade path, and ecosystem/community support.
- **Lock-in / exit risk:** how hard it is to switch later (data portability, proprietary dependencies).

**Good practice:** I document the scoring rationale (evidence-based, not preference-based) and link it to the decision record.

### Lightweight Proof-of-Concept (PoC) (time-boxed risk reduction)

When uncertainty is high, I run a **Proof-of-Concept (PoC)**: a time-boxed experiment to validate the riskiest assumptions.

**Typical PoC structure:**
- **Time-box:** 1–3 weeks (longer only if unavoidable)
- **Success criteria (measurable):**
  - critical integration works end-to-end
  - latency/throughput meets target ranges for expected load
  - failure handling demonstrated (retry, timeout, fallback behavior)
  - monitoring/alerts available (basic observability)
  - security requirements demonstrated (least-privilege access, secrets handling approach)
- **Deliverables:**
  - short demo/prototype
  - PoC notes: what worked, what didn’t, risks found
  - a go/no-go recommendation and next-step plan

### Decision record (traceability: why chosen, trade-offs, rollout plan)

I capture the outcome in a **decision record** (often called an ADR — Architecture Decision Record).  
This makes the decision auditable and prevents repeating debates.

**Decision record template (practical fields):**
- **Context:** what problem we’re solving and why now
- **Options considered:** option A/B/C (including “do nothing” when relevant)
- **Decision:** what we chose
- **Rationale:** the top reasons (linked to evidence/PoC results)
- **Trade-offs:** what we gain and what we accept (cost, complexity, lock-in, ops burden)
- **Risks & mitigations:** what can go wrong and how we reduce impact
- **Rollout plan:** staged rollout steps + monitoring + rollback triggers
- **Owners & dates:** who is accountable and when we review success

### Rollout approach (safe introduction to production)

Even after choosing a technology, the rollout must be controlled:
- **staged rollout:** start small (limited scope/users), expand when stable
- **feature flags / toggles (where applicable):** enable/disable quickly without redeploying
- **observability-first:** dashboards/alerts exist before scaling up usage
- **rollback triggers:** explicit thresholds that trigger rollback or pause
- **operational readiness:** runbooks updated, support team briefed, escalation path confirmed

<blockquote>
⬆ <a href="#on-this-page">Back to navigation</a>
</blockquote>

---

## Partner & vendor management lifecycle {#vendor-lifecycle}

I act as the single accountable point of contact for the partner: alignment, delivery status, risk escalation, and commercial follow-ups.

Vendor management is not only “relationship management”. It is a controlled lifecycle:

### 1) Selection (fit and risk)
- **Requirements definition:** what capability we need (technical, operational, security).
- **Evaluation criteria:** delivery track record, engineering quality, scalability, support model.
- **Due diligence:** references, security posture, and operating model (how they actually deliver).
- **Scorecard-based decision:** I compare vendors using a weighted scorecard and record the rationale in the decision log.

#### Vendor scorecard (weighted evaluation)

To avoid “gut-feel” decisions, I use a **vendor scorecard** (a structured evaluation matrix with **weighted criteria**).  
Each criterion is scored consistently (e.g., **1–5**, where 1 = weak / high risk, 5 = strong / low risk) and multiplied by a **weight** (importance).  
Weights are adjusted based on **criticality** (how business-critical the service is) and **risk profile** (data sensitivity, production impact, regulatory exposure).

**Typical weighted criteria (example):**
- **Capability / functional fit:** can they deliver what we need (scope + domain knowledge)?
- **Engineering quality:** code quality practices, testing depth, documentation quality.
- **Delivery maturity:** planning discipline, predictability, ability to manage changes, transparency.
- **Security posture:** access controls, secure SDLC (Software Development Life Cycle), incident response readiness.
- **Cost / commercial model:** total cost of ownership (TCO), pricing clarity, change-order approach.
- **Scalability & reliability:** performance, availability approach, operational model, support coverage.

**Good practice:** I keep the scorecard, scoring rationale, and final decision in a **decision log** (what we chose, why, trade-offs, and approvals) so the award is traceable and audit-friendly.

**Example scorecard layout (illustrative):**

| Criterion | Weight (%) | Score (1–5) | Evidence used (examples) |
|---|---:|---:|---|
| Capability / fit | 20 |  | Request for Proposal (RFP) response, demo, scope mapping |
| Delivery maturity | 20 |  | Plan quality, cadence, risk management approach |
| Engineering quality | 15 |  | Test strategy, code review practice, sample artifacts |
| Security posture | 20 |  | Security questionnaire, policies, certifications (if available) |
| Cost / TCO | 15 |  | Pricing model, support costs, change order mechanism |
| Scalability / reliability | 10 |  | Reference architecture, Service Level Objectives (SLOs) proposal |

#### Reference checks (validation outside the sales process)

Before signing, I run **reference checks** (structured calls with existing or past customers) to validate delivery reality:
- “Did they hit milestones consistently? If not, what caused slips?”
- “What was the defect/rework rate like near release?”
- “How did they behave under pressure (incident, escalation, major change)?”
- “Was communication transparent (bad news early, clear ownership)?”
- “Would you choose them again — and under what conditions?”

#### Pilot / Proof-of-Concept (PoC) when risk is high

When risk is high (new vendor, new tech stack, critical integration, strict timelines), I propose a **pilot** or **Proof-of-Concept (PoC)** (a time-boxed experiment to reduce uncertainty before full commitment).

**How I run a PoC (example structure):**
- **Time-box:** e.g., 2–4 weeks
- **Success criteria (measurable):** integration works end-to-end, latency under X, error rate under Y, security requirements met, deploy/rollback demonstrated
- **Deliverables:** working prototype, short technical notes, known risks, and a go/no-go recommendation
- **Exit criteria:** if success criteria are not met, we stop early or re-scope before signing a larger SOW (Statement of Work)

#### Due diligence outputs (what I collect before signing)

I treat partner assurance as part of delivery governance, not a separate “compliance exercise”.
It shows up in three places: (1) what I verify before signing (due diligence), (2) what I make enforceable in contract language (auditability, reporting, incident duties), and (3) what I monitor in the operating rhythm (scorecards/QBRs).

“Due diligence” is the evidence pack I gather to confirm the vendor can deliver safely and reliably (not just promise it).  
Typical artifacts I request/collect (as applicable):

- **Scope & delivery artifacts**
  - delivery plan (milestones, dependencies, resourcing)
  - delivery approach (Agile/Waterfall/hybrid), reporting cadence, escalation path
  - draft RACI (Responsible / Accountable / Consulted / Informed)
  - acceptance approach and test evidence expectations

- **Technical & operational artifacts**
  - high-level solution/architecture description (how it fits into our environment)
  - environment assumptions (development/test/production), deployment approach, rollback approach
  - runbook outline (operational procedures) and support model proposal
  - Disaster Recovery / Business Continuity Plan (DR/BCP) if production-critical

- **Security & compliance artifacts**
  - security questionnaire responses and supporting policies (access control, encryption approach, logging)
  - incident response process (severity levels, notification timelines, on-call model)
  - certifications/attestations if available (e.g., ISO 27001; SOC 2 (Service Organization Control 2))
  - sub-processor list (third parties they rely on) and data handling boundaries
  - contract clauses for security, breach notification, and audit rights (as applicable)
  - DPA (Data Processing Agreement) where personal data processing exists

- **Ethics & compliance controls (vendor conduct alignment)**
  - conflict-of-interest declaration (and a rule to disclose changes immediately)
  - gifts & hospitality rules (no cash-equivalents; modest, infrequent, transparent)
  - anti-bribery / anti-corruption commitment (zero-tolerance; vendor controls + training)
  - fair competition assurance (no bid-rigging/price-fixing; no misuse of confidential info)
  - sanctions / Anti-Money Laundering (AML) compliance confirmation where relevant to the vendor’s services and footprint
  - subcontractor “flow-down” requirement (vendor is responsible for ensuring subcontractors comply)
  - confidentiality + “no public announcements” about the relationship without written consent
  - AI-use disclosure (what is used, where, and for what purpose) and an approval path for higher-risk use
 
- **Commercial & contractual artifacts**
  - pricing model and assumptions (what is included vs extra)
  - change-order mechanism (how scope changes are quoted and approved)
  - payment milestones tied to acceptance (not just time)
  - exit/transition obligations (handover, documentation, knowledge transfer)

*Example evaluation questions I ask during due diligence discussions:*
- “How do you handle releases and rollbacks?”
- “What is your incident response process and response time?”
- “How do you ensure code quality (reviews, testing, Continuous Integration / Continuous Delivery (CI/CD))?”
- “How do you manage breaking changes and versioning?”

### 2) IT procurement process (how I select and onboard vendors) {#it-procurement}

When a partner is needed, I follow a structured **IT procurement process** (the end-to-end approach used to select a vendor and contract them safely). The goal is to choose a vendor that fits **technical needs**, **delivery capability**, **security/compliance requirements**, and **commercial constraints** — while keeping the decision traceable and audit-friendly.

- **RFI (Request for Information):** a lightweight information-gathering step used when the market is unclear. I use it to understand vendor capabilities, typical delivery models, references, security posture, and constraints — without committing to a detailed bid.
  - *Example:* “Which integration patterns do you support? What is your release cadence? Do you provide 24/7 support? What security certifications or controls do you have?”

- **RFP (Request for Proposal):** a formal request for a vendor to propose a solution and commercial offer. I include the scope, expected outcomes, timelines, acceptance criteria (how we will confirm success), assumptions/dependencies, and required service levels.
  - *Example RFP inputs:* target architecture/integration needs, environments, test evidence expectations, support model, and reporting cadence.

- **Vendor shortlisting criteria (how I narrow options):** I use a defined set of criteria so selection is not subjective:
  - **Technical fit:** capability match, scalability, integration approach, tooling, documentation quality.
  - **Delivery maturity:** planning discipline, testing approach, release management, incident handling, and how they manage change.
  - **Security & compliance fit:** ability to meet privacy/security controls (e.g., access control, encryption practices, audit logs), and willingness to provide evidence.
  - **Commercial fit:** pricing model, clarity of terms, ability to commit to SLAs (Service Level Agreements).
  - **References / track record:** proven delivery on similar scope and complexity.

- **Commercial + technical evaluation (how I choose the best option):**
  - **Technical evaluation:** solution approach, delivery plan realism, risks/assumptions, test strategy, operational readiness.
  - **Commercial evaluation:** total cost of ownership (not just day rate), payment milestones tied to acceptance, change-order mechanism, support costs, and exit terms.
  - *(Good practice:)* I keep a simple scoring matrix (weighted criteria) and document why the selected vendor is the best fit.

- **Security and compliance assessment (before contracting):** I validate that the vendor can operate safely within our environment:
  - data access boundaries and least-privilege access,
  - secure handling of credentials/keys,
  - logging and audit expectations (what is logged, who can access it),
  - sub-processor visibility (if they use other providers),
  - and any required contractual protections (security clauses, incident notification expectations).

- **Final award + onboarding (making it delivery-ready):** once selected, I convert the decision into an executable delivery setup:
  - confirm contract structure (MSA/SOW/SLA) and acceptance criteria,
  - align ways of working (cadences, tooling, reporting, escalation path),
  - define owners via RACI (Responsible/Accountable/Consulted/Informed),
  - and run a structured kickoff so delivery can start with clear expectations rather than assumptions.

### 3) Onboarding (how we set vendors up to succeed)
I align vendors on **non-negotiables** early:
- Definition of done (what “complete” means),
- documentation standards,
- security/privacy expectations,
- test evidence expectations,
- release process (how we ship safely),
- and escalation paths (who to contact when blocked).

### 4) Delivery governance (how vendor work is controlled)
- **Single delivery plan:** milestones, owners, dependencies, and acceptance criteria.
- **Regular cadences:** weekly delivery check, daily sync during critical periods.
- **Transparent performance signals:** progress, defect rate, rework, missed commitments.

### 5) Performance management (how we improve or correct)
When performance deviates, I do:
- **Fact-based gap analysis:** what is failing (schedule, quality, responsiveness).
- **Corrective action plan:** specific actions, owners, dates, measurable outcomes.
- **Escalation rules:** if X happens by Y date, we trigger Z (e.g., add internal engineering support, reduce scope, replace vendor team members, or activate exit plan).

### 6) Vendor performance management (operating rhythm, scorecards, QBRs, escalation ladder) {#vendor-performance}

Vendor performance management is how I make “good intentions” measurable and continuously improved.  
It combines (a) **service performance** (SLA adherence), (b) **delivery performance** (predictability/quality), and (c) **relationship management** (fast resolution and alignment).

#### Operating rhythm (cadence that keeps performance visible)

**Weekly (delivery focus; more frequent during critical releases)**
- delivery checkpoint: commitments vs actuals, blockers, risks, upcoming milestones
- quality snapshot: open defects by severity, rework items, test evidence status
- dependency tracking: what the vendor needs from us / what we need from them

**Monthly scorecard review (performance management)**
A structured session where we review a **vendor scorecard** (fact-based, trend-driven).  
This is where performance is “run like operations,” not debated.

**Typical monthly scorecard sections (examples):**
- **SLA performance (Service Level Agreement):**
  - SLA breaches (count + severity)
  - response time / restore time performance (e.g., Sev1, Sev2 targets)
  - incident communications compliance (update frequency, completeness)
- **Delivery predictability:**
  - milestone hit rate / commitment reliability
  - carryover rate (planned work that rolled into next sprint/release)
  - dependency-driven slips (and root causes)
- **Quality & stability:**
  - defect trends (new vs closed), severity distribution
  - defect leakage (found after release vs before release)
  - rework rate (items returned due to incomplete/incorrect delivery)
- **Operational readiness & documentation:**
  - runbook completeness, monitoring hooks delivered, handover quality
- **Collaboration health (lightweight but real):**
  - time-to-respond on blockers, clarity of ownership, escalation effectiveness

- **Compliance & trust signals (lightweight but real):**
  - security/data incidents: time-to-notify, time-to-mitigate, post-incident actions closed
  - subcontractor changes disclosed on time (and approved where required)
  - conflicts-of-interest disclosures logged (none outstanding)
  - audit / evidence requests responded to within agreed timelines
  - accurate delivery records maintained (acceptance evidence, change approvals, and reporting traceability)

*Good practice:* I track **trend lines** (last 3–6 months) so we see improvement or deterioration early.

**Monthly outputs (what comes out of the meeting):**
- scorecard snapshot stored (for traceability)
- top 3 improvements agreed (owners + deadlines)
- any contractual actions triggered (e.g., service credits, formal notice), if needed

#### Quarterly Business Review (QBR) (strategic alignment + improvement plan)

A **Quarterly Business Review (QBR)** is a senior-level session (vendor leadership + our leadership) that focuses on:
- roadmap alignment (what’s coming, what needs capacity)
- strategic risks (technology, security, scaling, market changes)
- performance themes (patterns from monthly scorecards)
- improvement plan (what we will change in how we work together)

**QBR agenda template (example):**
- performance summary (SLA + delivery + quality)
- major incidents and lessons learned (and what changed)
- upcoming roadmap + capacity outlook (next quarter)
- risk review (top risks + mitigations)
- decisions needed (scope/date trade-offs, investment needs)
- improvement plan sign-off (specific actions + KPIs)

**QBR outputs:**
- updated joint roadmap assumptions
- agreed improvements (with measurable targets)
- updated escalation expectations (if performance is drifting)

#### Escalation ladder (clear path when performance deviates)

Escalation is a controlled mechanism (not emotion). I define escalation levels upfront so everyone knows what happens next.

**Level 0 — Working level (vendor engineers + internal engineers)**
- resolve blockers quickly; confirm owners and deadlines

**Level 1 — Delivery level (Vendor PM → Internal Technical PM / Service Delivery)**
- trigger when: repeated slips, unclear ownership, missed commitments
- action: corrective plan with milestones, extra reporting cadence, re-baseline

**Level 2 — Leadership level (Vendor leadership → Internal leadership)**
- trigger when: material risk to release date, critical quality issues, repeated SLA breaches
- action: resource changes, scope reduction, “stop the line” decision, formal remediation plan

**Level 3 — Commercial/Legal path (contractual enforcement)**
- trigger when: sustained non-performance, major compliance breach, failure to remediate
- action examples: service credits, formal notice, contract remedies, termination/exit plan activation

*Example escalation rule (explicit):*  
“If we have 2 consecutive months of SLA breach on Sev1 response time, we move to Level 2 escalation and require a remediation plan within 10 business days, with weekly progress reporting until metrics stabilize.”

### 7) Renewal or exit (planned, not panic)
- **Renewal:** if performance is strong and the relationship is healthy.
- **Exit plan:** if risk remains high (knowledge transfer, documentation pack, handover, replacement strategy).

<blockquote>
⬆ <a href="#on-this-page">Back to navigation</a>
</blockquote>

---

## Contracts, statements of work, and SLAs {#contracts-slas}

This is how I make commercial agreements “delivery-safe”.

### Key documents (with definitions)
- **Master Services Agreement (MSA):** the legal umbrella (terms that apply to all work).
- **Statement of Work (SOW):** the specific deliverables, timeline, responsibilities, acceptance criteria, and pricing.
- **Service Level Agreement (SLA):** measurable service commitments (availability, response times, support coverage).

### Contract models (common)
- **Time & Materials (T&M):** pay for effort; needs strong scope control and transparent reporting.
- **Fixed price:** pay for deliverables; requires very clear scope and acceptance criteria.
- **Capped T&M:** T&M but with a ceiling; balances flexibility and cost control.

### What I insist is explicit (to avoid disputes)
- **Acceptance criteria:** how we formally accept deliverables (pass/fail conditions).
- **Change control:** how scope changes are priced and approved (change order process).
- **Quality expectations:** test evidence, documentation, security requirements.
- **Support model:** hours, response times, escalation path.
- **Dependencies:** what the vendor depends on from us (and vice versa).

### Contract negotiation & contract management (how I make it “real-world” and enforceable) {#contract-negotiation}

In practice, contract work is where delivery succeeds or fails. I negotiate and manage contracts so that:
- incentives reward **accepted outcomes** (not just time spent),
- roles and obligations are enforceable (not vague),
- changes are controlled (so scope doesn’t silently expand),
- and exit is planned (so the business is not hostage to the vendor).

#### What I typically negotiate (and why)

- **Payment milestones tied to acceptance (outcome-based payments):**  
  I avoid paying purely for “effort” when possible. Instead, I tie payments to **deliverables that meet acceptance criteria** (formal conditions for sign-off).  
  *Example:* “Milestone 2 is payable only after integration tests pass and the agreed evidence pack is delivered (test report + release notes + runbook draft).”

- **Intellectual Property (IP) (ownership / licensing):**  
  IP (Intellectual Property) terms define who owns the code, designs, documentation, and any reusable components.  
  I make sure we are covered for:
  - **ownership** of bespoke deliverables built for us (or a strong perpetual license),
  - **licensing** clarity for any vendor pre-existing components,
  - reuse restrictions (if any), and
  - rights to modify/maintain the deliverable after handover.  
  *Example:* “Customer owns project-specific deliverables; vendor retains background IP but grants a perpetual, royalty-free license for operation and maintenance.”

- **Confidentiality and data protection clauses (where applicable):**  
  If the vendor will access sensitive or personal data, I ensure obligations are explicit:
  - permitted uses of data,
  - access control and least privilege,
  - breach notification timelines,
  - sub-processor restrictions and disclosure,
  - secure deletion/return of data at contract end.  
  *(If personal data is processed, this typically requires a Data Processing Agreement (DPA) alongside the main contract.)*

- **Change order mechanics (scope-change pricing + approval workflow):**  
  I insist that scope change has a controlled path:
  - request logged (what is changing and why),
  - impact analysis (time/cost/risk),
  - written approval (who can approve),
  - updated baseline plan and revised milestones.  
  *Example approval rule:* “No work starts on a change until the change order is approved in writing by the Accountable owner.”

- **Audit rights and reporting obligations:**  
  I negotiate the right to request evidence that obligations are met (especially for security, service levels, and compliance):
  - regular delivery reporting (milestones, risks, KPIs),
  - service reporting (availability, incidents, SLA performance),
  - the ability to audit (or receive audit outputs) when risk is high.  
  *Example:* “Monthly SLA report + incident postmortems for Severity 1 (Sev1) / Severity 2 (Sev2) + quarterly security posture update.”

- **Code of conduct alignment + auditability (make compliance enforceable):**
  - vendor complies with an agreed code of conduct and all applicable local laws
  - accurate records obligations (no improper alteration/destruction of client-related records)
  - conflicts-of-interest disclosure (and a duty to report changes promptly)
  - gifts & hospitality boundaries (explicitly prohibit cash/cash-equivalents; require transparency)
  - anti-bribery / anti-corruption controls (policies, training, and reporting channels)
  - fair competition language (no anti-competitive conduct; no misuse of confidential information)
  - security/data incident notification timelines + cooperation duties (investigation, mitigation, notifications support)
  - subcontractor controls (visibility/approval where required; obligations flow down)
  - AI-use disclosure clause (no higher-risk AI use without written approval; documentation and evidence on request)
  - “no public announcements” about the relationship without written consent
  - right to request evidence / run compliance reviews and require a remediation plan if gaps are found

- **Termination and exit assistance (planned exit, not panic):**  
  I make sure we can exit safely if performance drops or strategy changes:
  - notice periods and termination triggers,
  - **exit assistance** obligations (knowledge transfer, documentation handover, transition support),
  - handover package definition (source code, build/deploy scripts, runbooks, architecture notes, credentials transition plan),
  - support coverage during transition.  
  *Example:* “On termination, vendor provides 4 weeks transition support, delivers complete documentation pack, and runs handover sessions with internal teams.”

#### How I manage contracts after signature (contract governance)

Signing is not the end. I run a light contract governance loop:
- **obligation tracking:** key obligations and dates (deliverables, reporting, SLA reviews),
- **acceptance log:** what was accepted, when, and based on which evidence,
- **change log:** all change orders and baseline impacts,
- **performance reviews:** regular vendor performance checks against contract + scorecard signals,
- **issue-to-contract linkage:** major delivery issues mapped to contractual obligations (so remediation is enforceable).

### SLAs in practice (what “good” looks like)
An SLA should define:
- **Service hours:** e.g., 24/7 vs business hours.
- **Severity levels:** Sev1 (critical outage), Sev2 (major), etc.
- **Response time:** how quickly the vendor acknowledges and starts handling an incident.
- **Restore time target:** how quickly service is restored (target, not a promise in all cases).
- **Communication cadence:** how often updates are provided during incidents.

*Example (SLA-style wording):*  
“For Sev1 incidents: acknowledge within 15 minutes, provide updates every 30 minutes, and engage engineering immediately until mitigation is in place.”

<blockquote>
⬆ <a href="#on-this-page">Back to navigation</a>
</blockquote>

---

## Delivery governance (cadences, reporting, decisions) {#delivery-governance}

Governance is how I keep delivery **aligned, visible, and fast** (not slow).

### Cadences (examples)
- **Weekly project checkpoint:** progress, risks, dependencies, next milestones.
- **Daily sync during critical windows:** near release, during integration testing, or when blocked.
- **Steering check (as needed):** decision-making forum for scope/date trade-offs.

### Reporting (what I report, consistently)
- **Status:** green/amber/red (with reasons, not vibes).
- **Milestones:** achieved / at risk / slipped.
- **Risks:** top risks, mitigation actions, owners, due dates.
- **Dependencies:** what is blocked and what is needed to unblock.
- **Quality:** key defects, incident trends, test pass rate (as applicable).

### Decision discipline (fast and traceable)
I keep a **decision log**:
- what was decided,
- why,
- options considered,
- who approved,
- and follow-up actions.

This prevents repeating debates and enables accountability.

<blockquote>
⬆ <a href="#on-this-page">Back to navigation</a>
</blockquote>

---

## Release & change management {#release-change}

In high-scale environments, releases must be **repeatable** and **controlled**.

### Release management (what I do)
- **Release plan:** what ships, when, and in what order (including dependencies).
- **Release readiness checklist:** evidence-based go/no-go.
- **Rollback plan:** what we do if production fails (steps, owners, thresholds).
- **Post-release verification:** short, structured checks that confirm the system is healthy.

### Release execution (how I run a safe cutover) {#release-execution}

A good release is not “deploy and hope”. It is a controlled sequence with clear owners, evidence, and rollback readiness.

#### 1) Release scope and dependency lock
- confirm what is in / out (scope baseline for the release)
- confirm upstream/downstream dependencies (partner deliverables, internal integration points, environment readiness)
- freeze late changes unless they meet explicit exception criteria

#### 2) Release readiness evidence pack (what must exist before go/no-go)
- release notes (what changes, what risks, what to watch)
- test evidence summary (key flows passed, known issues, risk acceptance)
- operational readiness (monitoring/dashboard links, alert rules, runbook updated)
- rollback plan (steps + owners + triggers) and “kill switch” / feature-flag plan where applicable
- stakeholder comms plan (who gets updates, cadence during the window)

#### 3) Cutover plan (minute-by-minute for higher-risk changes)
For higher-risk releases, I use a short cutover plan:
- pre-checks (service health baseline, capacity signals, key journey checks)
- deployment steps (order, gating checks, pause points)
- verification steps (post-deploy checks that prove the service works)
- rollback decision points (explicit thresholds, not gut feel)

#### 4) Go/no-go criteria (evidence-based)
I make go/no-go explicit using a checklist:
- critical tests passed and evidence published
- key risks have owners and mitigations
- operational team is ready (on-call coverage confirmed, runbook and comms ready)
- rollback steps are understood and executable within an acceptable time window

#### 5) Post-release verification and hypercare
- validate stability using monitoring signals and key user journey checks
- run a short hypercare window (heightened monitoring + fast response)
- capture lessons learned and convert them into tracked improvement actions

### Change management (definition)
**Change management** is the controlled handling of changes to scope, schedule, or production systems:
- changes are recorded,
- impact is assessed (time/cost/risk),
- approvals are explicit,
- and the baseline is updated.

*Example (good change control):*  
“Partner requested new requirement X. Impact: +2 weeks, +1 QA cycle, additional security review. Options: (A) defer to next release, (B) reduce scope elsewhere, (C) add vendor capacity. Decision recorded and plan re-baselined.”

<blockquote>
⬆ <a href="#on-this-page">Back to navigation</a>
</blockquote>

---

## 24/7 production & peak-period release discipline (high-scale consumer platforms) {#high-scale}

In **high-scale consumer platforms**, production is effectively **24/7**: traffic does not pause, and releases must be safe under load.  
My approach is to reduce release risk with **clear change controls**, **staged rollout**, and **observability-first go/no-go** decisions.

### Production expectations (what “good” looks like in 24/7 services)

- **Always-on mindset:** incidents and releases are handled with defined roles, comms cadence, and on-call readiness.
- **Operational readiness before change:** dashboards, alerts, and rollback steps exist before enabling traffic to new code.
- **No “big bang” changes by default:** progressive delivery is preferred (start small, expand when stable).

### Freeze windows and change calendar (risk control during peak periods)

During peak risk periods (e.g., major campaigns, high-traffic weekends/events), I use **freeze windows**:
- **Change freeze:** only critical fixes allowed (pre-approved criteria)
- **Release windows:** define when changes are allowed (and when they are not)
- **Exception path:** clear approval route for emergency changes (who approves, what evidence is needed)

*Example rule:*  
“During peak window, only Sev1/Sev2 fixes ship; everything else waits for the next safe window.”

### Staged rollout (reduce blast radius)

I prefer a staged rollout strategy so failures are contained:
- **Canary / small-percent rollout:** release to a small slice first, validate, then expand
- **Feature flags / toggles:** enable/disable functionality without redeploying
- **Kill switch:** a fast way to stop a risky flow or integration
- **Rollback readiness:** explicit rollback steps validated in non-prod and rehearsed for critical releases

### Observability-first go/no-go (evidence-based decision)

Go/no-go is driven by **evidence**, not optimism. Before and after rollout, I confirm:
- **Reliability signals:** error rates, crash rates, timeouts, failed transactions
- **Performance signals:** latency (p95/p99 where used), throughput, saturation (CPU/memory/queues)
- **Customer-impact signals:** critical user journey success rate (login, payment, key workflow)
- **SLO/SLA alignment:** whether we are staying within expected service objectives

**Explicit rollback triggers (examples):**
- error rate exceeds X for Y minutes
- latency exceeds target threshold for Y minutes
- critical journey success rate drops below X%
- incident severity threshold reached (Sev1/Sev2)

### Release staffing and comms during high-risk changes

For high-risk releases I align upfront:
- who is on point (release lead + incident commander backup)
- vendor presence if a partner owns part of the stack (on-call engineer available)
- comms channel and update cadence (stakeholders know when to expect updates)
- a short “hypercare” period after release (e.g., 24–48 hours heightened monitoring)

<blockquote>
⬆ <a href="#on-this-page">Back to navigation</a>
</blockquote>

---

## Service delivery in production (Business-as-Usual (BAU) operations) {#bau-ops}

After go-live, “service delivery” continues in **production operations** (keeping the service stable, reliable, and supportable).  
My focus is: predictable **incident response**, disciplined **root cause** resolution, and regular **service health reviews** (so we prevent repeats instead of firefighting).

### Incident management (restore service quickly and safely)

**Incident management** is the controlled process to **restore service** when something breaks or degrades in production (not to assign blame).  
I use severity levels to align urgency, escalation, and communication expectations.

#### Severity model (example)

- **Severity 1 (Sev1):** critical outage or major customer impact (service unavailable, high financial/brand risk).
- **Severity 2 (Sev2):** major degradation (partial outage, key function unstable, significant impact).
- **Severity 3 (Sev3):** limited impact (workaround exists, smaller subset of users).
- **Severity 4 (Sev4):** minor issue (cosmetic/low urgency).

*(The exact definitions vary by organization; the key is that they are agreed, documented, and used consistently.)*

#### Roles during an incident (clear ownership under pressure)

- **Incident Manager / Incident Commander (IM/IC):** runs the process (triage, priorities, comms cadence, decision-making), not the technical fix.
- **Technical Lead:** coordinates engineers doing diagnosis and mitigation.
- **Communications Lead:** manages stakeholder updates (internal + external where applicable).
- **Scribe / Timeline Owner:** captures timestamps, actions, decisions (so post-incident analysis is evidence-based).

#### Incident lifecycle (how I run it)

1) **Detection & triage:** confirm symptoms and scope (what is impacted, how many users, which regions).
2) **Classification:** assign severity (Sev1–Sev4) and open a clear incident record (ticket + shared doc).
3) **Containment / mitigation:** restore service ASAP (feature flag off, rollback, rate-limit, failover, hotfix), with explicit risk calls.
4) **Communication cadence:** frequent, predictable updates (even if “no change”).
   - *Example cadence:* for Sev1, updates every 30 minutes to stakeholders until stable.
5) **Resolution & verification:** confirm recovery using monitoring signals and user journey checks (not only “it looks OK”).
6) **Closure:** close the incident only when monitoring confirms stability and follow-ups are logged.

#### Vendor involvement during incidents (when a partner runs part of the stack)

If a vendor is involved, I align:
- **who leads** the incident (single Incident Manager/Incident Commander),
- **what the vendor must provide** (logs, on-call engineer, mitigation plan),
- **SLA (Service Level Agreement) expectations** for response and updates,
- and **escalation triggers** if response time or mitigation is inadequate (aligned with our escalation ladder).

### Problem management (prevent recurrence, not just “close the ticket”)

**Problem management** is the process for identifying and removing the **root cause** behind incidents (or recurring issues).  
It is usually driven by **Root Cause Analysis (RCA)** and results in **Corrective and Preventive Actions (CAPA)**.

- **Root Cause Analysis (RCA):** structured analysis (e.g., “5 Whys”, fishbone/Ishikawa) to find why it happened.
- **Corrective action:** fixes the underlying cause (e.g., change validation logic, improve retry strategy).
- **Preventive action:** prevents recurrence (e.g., better alerting thresholds, automated rollback, additional test coverage).

**Outputs I insist on (evidence-based):**
- a short RCA summary (what happened, impact, timeline, contributing factors),
- “what we changed” (specific actions, not vague intentions),
- owners and dates for each CAPA item,
- and a verification plan (how we prove the fix worked).

### Service reviews (run the service like a product, not a crisis)

A **service review** is a recurring session to review service health and make improvement decisions using data.

#### Monthly service review (example agenda)

- **Availability & reliability:** uptime, major incidents, repeated patterns.
- **Incident trends:** Sev1/Sev2 counts, Mean Time To Restore (MTTR), recurring failure modes.
- **Capacity & performance:** latency, throughput, saturation, bottlenecks (and forecasts).
- **Change outcomes:** release success rate, change-related incidents, rollback frequency.
- **Planned maintenance:** upcoming maintenance windows and communication plan.
- **Improvement backlog:** top operational risks and prioritized fixes (with owners/dates).

**Good practice:** decisions are recorded (decision log) and actions are tracked like delivery work (owners, due dates, status).

<blockquote>
⬆ <a href="#on-this-page">Back to navigation</a>
</blockquote>

---

## Quality management (testing, evidence, acceptance) {#quality}

Quality is not “QA’s job”. It is a delivery system.

### Testing layers (common structure)
- **Unit testing:** verifies small components.
- **Integration testing:** verifies systems working together.
- **System testing:** end-to-end workflows.
- **User Acceptance Testing (UAT):** validation by business/users against acceptance criteria.

*(UAT = User Acceptance Testing; the business confirms “this meets needs and is acceptable to release”.)*

### Evidence expectations (what I keep)
- executed test cases (pass/fail),
- defects with severity and status,
- sign-offs for UAT (email or formal record),
- release readiness checklist completion.

### Acceptance management (how I prevent “it’s not what we expected”)
- acceptance criteria are written early (testable),
- demos are used to validate direction continuously,
- vendor deliverables are accepted only when criteria are met (not when “delivered”).

<blockquote>
⬆ <a href="#on-this-page">Back to navigation</a>
</blockquote>

---

## Risk, dependency, and escalation control {#risk-deps}

### RAID log (definition)
**RAID** = Risks, Assumptions, Issues, Dependencies.

I keep it “alive” (reviewed regularly), with:
- description,
- owner,
- impact,
- mitigation plan,
- due date,
- escalation rule.

### Escalation (when and how)
Escalation is not drama — it is a controlled response to protect delivery.

I escalate when:
- a dependency threatens milestones,
- quality risk rises near release,
- vendor deliverables slip repeatedly,
- or there is a production stability risk.

*Example (escalation rule):*  
“If no stable vendor build by Thursday 18:00, we defer feature X to next release and ship the remaining committed scope.”

<blockquote>
⬆ <a href="#on-this-page">Back to navigation</a>
</blockquote>

---

## Delivery metrics and performance signals {#metrics}

I use metrics as **signals**, not as vanity numbers. Typical categories:

### Predictability
- **Milestone hit rate:** how often we hit committed dates.
- **Carryover rate:** how much planned work rolls into the next sprint/release (indicates overcommitment or hidden complexity).

### Flow efficiency
- **Cycle time:** time from “started” to “done”.
- **Lead time:** time from “requested” to “delivered”.

### Quality
- **Defect leakage:** issues found after release vs before release.
- **Change failure rate:** how often releases cause incidents/rollbacks.
- **Mean Time To Restore (MTTR):** how quickly service is restored after an incident.

### Vendor performance (examples)
- SLA adherence (response/update times),
- delivery predictability (commitment reliability),
- rework rate (deliveries needing significant fixes),
- documentation completeness (handover quality).

<blockquote>
⬆ <a href="#on-this-page">Back to navigation</a>
</blockquote>

---

## Glossary (plain-language definitions) {#glossary}

<details markdown="1">
<summary><strong>Open glossary</strong></summary>

- **SLA (Service Level Agreement):** measurable service commitments (availability, response times, support coverage).
- **SOW (Statement of Work):** the specific deliverables, timeline, owners, acceptance criteria, and pricing.
- **MSA (Master Services Agreement):** the umbrella legal agreement covering general terms.
- **RACI:** responsibility mapping (Responsible, Accountable, Consulted, Informed).
- **RAID:** tracking log for Risks, Assumptions, Issues, Dependencies.
- **UAT (User Acceptance Testing):** business/user validation and sign-off before release.
- **Go/No-go:** the formal decision to release (go) or hold (no-go), based on evidence and risk acceptance.
- **Rollback:** the planned action to return to a previous stable version if release causes serious issues.
- **MTTR (Mean Time To Restore):** average time to restore service after an incident.
- **TCO (Total Cost of Ownership):** the total cost over time (licenses + infrastructure + support + change + exit), not only the purchase price.
- **ADR (Architecture Decision Record):** a short document that records a technical decision, why it was made, trade-offs, and rollout plan.
- **Conflict of interest:** a situation where a vendor’s other relationships or incentives could bias decisions against the customer’s interests.
- **AML (Anti-Money Laundering):** controls and checks that help prevent illicit funds movement; relevant for certain vendor scopes (e.g., payments, compliance tooling, identity checks).
- **AI Act (EU):** EU rules for AI systems; vendors should disclose AI use and provide documentation/evidence when required, especially for higher-risk use cases.
- **PoC (Proof-of-Concept):** a time-boxed experiment to validate key assumptions before full implementation.
- **Freeze window (change freeze):** a period where non-critical changes are paused to reduce production risk during peak traffic.
- **Canary release:** releasing to a small percentage of traffic first to validate stability before wider rollout.
- **Feature flag:** a switch that enables/disables functionality without redeploying code.
- **Observability:** the ability to understand system health using logs/metrics/traces and dashboards/alerts.
- **SLO (Service Level Objective):** internal reliability/latency targets used to run the service (often stricter than contractual SLAs).
- **p95/p99 latency:** “95th/99th percentile response time” (how slow the worst 5%/1% of requests are).
- **Hypercare:** short period after a release with heightened monitoring and fast response.

</details>

<blockquote>
⬆ <a href="#on-this-page">Back to navigation</a>
</blockquote>

<hr>

<p>
  <strong>Next:</strong>
  🔎 <a href="/project-delivery/artifacts-governance/">Artifacts &amp; governance</a>
  · <a href="/project-delivery/agile-scrum/">Agile &amp; Scrum</a>
  · <a href="/project-delivery/">Back to Project Delivery &amp; Methods</a>
</p>
