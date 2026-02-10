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
- [Contracts, statements of work, and SLAs](#contracts-slas)
- [Delivery governance (cadences, reporting, decisions)](#delivery-governance)
- [Release & change management](#release-change)
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

*Example (evaluation questions):*
- “How do you handle releases and rollbacks?”
- “What is your incident response process and response time?”
- “How do you ensure code quality (reviews, testing, CI/CD)?”
- “How do you manage breaking changes and versioning?”

### 2) Onboarding (how we set vendors up to succeed)
I align vendors on **non-negotiables** early:
- Definition of done (what “complete” means),
- documentation standards,
- security/privacy expectations,
- test evidence expectations,
- release process (how we ship safely),
- and escalation paths (who to contact when blocked).

### 3) Delivery governance (how vendor work is controlled)
- **Single delivery plan:** milestones, owners, dependencies, and acceptance criteria.
- **Regular cadences:** weekly delivery check, daily sync during critical periods.
- **Transparent performance signals:** progress, defect rate, rework, missed commitments.

### 4) Performance management (how we improve or correct)
When performance deviates, I do:
- **Fact-based gap analysis:** what is failing (schedule, quality, responsiveness).
- **Corrective action plan:** specific actions, owners, dates, measurable outcomes.
- **Escalation rules:** if X happens by Y date, we trigger Z (e.g., add internal engineering support, reduce scope, replace vendor team members, or activate exit plan).

### 5) Renewal or exit (planned, not panic)
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
