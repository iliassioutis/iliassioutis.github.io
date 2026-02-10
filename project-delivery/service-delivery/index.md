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

## On this page {#on-this-page}

- [What “service delivery” means in practice](#what-is-service-delivery)
- [Operating model (how I run multiple projects at once)](#operating-model)
- [Project lifecycle (hybrid: Agile + stage-gate)](#project-lifecycle)
- [Partner & vendor management lifecycle](#vendor-lifecycle)
- [Vendor performance management (operating rhythm, QBR, escalation ladder)](#vendor-performance)
- [IT procurement process (RFI/RFP, evaluation, award, onboarding)](#it-procurement)
- [Contracts, statements of work, and SLAs](#contracts-slas)
- [Contract negotiation & contract management (commercial controls)](#contract-negotiation)
- [Delivery governance (cadences, reporting, decisions)](#delivery-governance)
- [Release & change management](#release-change)
- [Service delivery in production (BAU operations: incidents, problems, service reviews)](#bau-ops)
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

When multiple initiatives run in parallel, I use a simple operating model with **one “source of truth”** and **repeatable cadences**.

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

*Example:* For a vendor-delivered API integration:
- Accountable: Service Delivery / Technical PM
- Responsible: Vendor engineering + internal integration engineer
- Consulted: Security, Ops/SRE, Product
- Informed: Commercial owner, Support lead

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

## Partner & vendor management lifecycle {#vendor-lifecycle}

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

**Level 1 — Delivery level (Vendor PM → Internal TPM/Service Delivery)**
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
