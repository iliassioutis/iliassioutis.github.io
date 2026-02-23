---
layout: default
title: Agile & Scrum
---

<blockquote>
🏠 <a href="/">Back to homepage</a> · <a href="/project-delivery/">Project Delivery & Methods</a>
</blockquote>

I use **Agile and Scrum** as an execution system that delivers working increments fast, keeps stakeholders aligned through evidence, and maintains delivery control when risk is real (for example, regulated constraints, vendor dependencies, and integration-heavy releases).

The page is intentionally practical: it shows the checklists, templates, and rules I actually use so a reader can understand **exactly** how the system runs.

---

## How Scrum runs end-to-end (the operating loop) {#how-scrum-runs}

If you have never worked in Scrum before, this is the simplest accurate description of how the system runs from request → backlog → sprint → release.

To make it concrete, I use one running example throughout.

### Running example used in every step
A stakeholder requests:  
‘Customer support agents need to see the latest payment status for an order, because customers keep calling and agents cannot confirm whether payment succeeded.’

Assume:
- Payment status is provided by a vendor API.
- The support team uses a web dashboard.
- We deploy to production only during approved release windows.

### Step 0 — Agree the product goal and constraints (so we do not build “random work”)
Before we start sprints, the Product Owner aligns stakeholders on:
- the goal (what outcome matters and why),
- the constraints (for example, security, privacy, regulatory approvals, vendor lead times, release windows),
- and the success measures (what metric or signal proves we achieved the goal).

This creates direction so the backlog does not become a pile of unrelated requests.

**Example (Step 0 outputs)**
- **Goal:** Reduce customer support escalations by enabling agents to confirm payment status from the dashboard.
- **Success measures:**  
  - Reduce “payment status unknown” tickets by 50% within 2 weeks after release.  
  - Achieve 95%+ successful status lookups for orders in the last 30 days.
- **Constraints:**  
  - Vendor API rate limit is 100 requests/minute.  
  - Access to the vendor API requires an API key, and our Security team must approve using and storing that key before we can proceed.  
  - Release window is Wednesday 18:00–20:00.  
  - We must not display full payment card data (privacy/security constraint).

### Step 1 — Capture requests into an intake (so we do not lose context)
When a stakeholder asks for something, we do not immediately “turn it into a sprint.”  
We first capture it as a backlog candidate with:
- the problem and who is affected,
- the desired outcome and why it matters now,
- the success measure (what will change when it is done),
- the deadline driver (what external event forces a date),
- dependencies (teams, vendors, access approvals, environments),
- and constraints (security, privacy, compliance, operational requirements).

**Example (Step 1 intake write-up)**
- **Problem:** Support agents cannot confirm payment status; customers call repeatedly; escalations increase.
- **Who is affected:** Support team + customers waiting for confirmation.
- **Outcome:** Agent can view current payment status for an order from the dashboard.
- **Why now:** Ticket volume spiked after a new payment provider integration.
- **Success measure:** 95%+ status retrieval success; 50% reduction in “unknown status” tickets.
- **Deadline driver:** Support leadership wants this live before next billing cycle (2 weeks).
- **Dependencies:** Vendor API documentation + API key; internal dashboard team; QA; Security approval.
- **Constraints:** No sensitive payment data displayed; rate limiting; release window Wednesday.

### Step 2 — Convert the request into backlog items (so it becomes deliverable work)
We break the request into small backlog items that can be delivered and verified:
- We write user stories (or tasks) that describe a specific outcome.
- We add testable acceptance criteria so “done” is unambiguous.
- We split large items until each item fits a sprint and does not hide unknown dependencies.

**Example (Step 2 backlog breakdown)**
- **Story A:** As a support agent, I can see payment status in the order view.
  **Draft acceptance criteria (testable):**
  - When an agent opens an order, the dashboard shows one of: PAID / FAILED / PENDING / UNKNOWN.
  - The dashboard shows “Last updated at” timestamp for the status.
  - If the vendor status cannot be refreshed, the dashboard shows the last known status and displays “Status may be stale.”
- **Story B:** As a system, we fetch status from the vendor API and store the latest result.
- **Story C:** As a support agent, I see a clear fallback when the vendor is down (stale data + warning).
- **Task D:** Add rate limiting and caching so our system stays within the vendor API quota and avoids throttling or blocking during peak usage.
- **Task E:** Add logs and metrics so we can monitor success rate and failures.
- **Task F:** Add security controls (store API key safely; least-privilege access).
- **Task G:** Create test cases + evidence pack for release readiness.

This split makes the work deliverable in increments, not as one “big story that hides unknowns.”

### Step 3 — Refine and make items Ready (so sprint planning is predictable)
Backlog Refinement is the preparation step.
The team improves clarity and reduces risk until the best candidates meet the Definition of Ready (DoR).
At any time, we aim to keep the next 1–2 sprints worth of work in a Ready state.

**Example (Step 3 refinement result for Story A)**
Story A becomes Ready only when:
- we confirm where the payment status appears on the dashboard,
- we agree what statuses exist (PAID, FAILED, PENDING, UNKNOWN),
- we define fresh as ‘the status was successfully fetched from the vendor API within the last 5 minutes’ (we store a Last updated timestamp and we treat anything older than 5 minutes as stale),
- we define error and fallback behaviour.

**Example acceptance criteria added during refinement**
- The dashboard shows one of: PAID / FAILED / PENDING / UNKNOWN.
- The dashboard shows “Last updated at” timestamp.
- If vendor call fails, the dashboard shows last known status and “Status may be stale.”
- The UI must not display card numbers or sensitive payment details.

**Example dependency captured**
- “Security must approve vendor API key storage method before implementation starts.”

### Step 4 — Order the backlog (prioritization is not random)
The Product Owner orders the backlog using consistent criteria, usually:
- value (how much benefit it brings),
- urgency (what deadline or business driver exists),
- risk reduction (what prevents incidents, failures, or compliance problems),
- dependencies (what unlocks other work),
- and effort (what it costs in time and capacity, based on team estimates).

**Example (Step 4 ordering decision)**  
Because the dashboard display depends on having a reliable status source, we order work so dependencies are delivered first:

1) **Story B (fetch/store status)** because it enables the data source that everything else depends on.  
2) **Task F (security controls)** because we cannot ship vendor integration without secure credential handling and least-privilege access.  
3) **Task E (logs/metrics)** because we need observability to validate reliability and operate safely.  
4) **Story A (show status on dashboard)** because it is the user-visible outcome once the status source exists.  
5) **Story C (fallback/stale warning)** because it prevents incorrect agent guidance during vendor outages.  
6) **Task D (rate limiting/caching)** because we must stay within the vendor’s request limit during peak usage; if our test traffic shows we are comfortably below the limit, we ship without it and schedule it for the next sprint.

If two items compete, the Product Owner makes the scope trade-off and records the decision.

### Step 5 — Sprint Planning (we commit to a goal based on capacity)
At sprint planning:
- the Product Owner proposes a sprint goal (one sentence outcome),
- Developers estimate and select work from the Ready items,
- the team commits to a realistic scope based on capacity and known constraints,
- and we call out sprint risks and sprint dependencies explicitly.

**Example (Step 5 sprint planning outputs)**
- **Sprint goal:** “Support agents can view payment status for an order with safe handling and basic monitoring.”
- **Capacity reality:**  
  - 2 Developers available full-time, 1 Developer is 50% due to on-call, 1 QA available 50%.  
- **Sprint scope chosen (only Ready items):**  
  - Story B (fetch/store status)  
  - Story A (show status + last updated timestamp)  
  - Task F (API key storage + access control)  
  - Task E (basic logs + success/failure metric)
- **Sprint risks:**  
  - Vendor sandbox might be unstable.  
  - Security approval might take 3 days.
- **Dependencies:**  
  - “Security approval by Tuesday 12:00.”  
  - “Vendor provides test credentials by Monday 17:00.”

### Step 6 — Sprint execution (work flows across the board, not by “status meetings”)
During the sprint:
- Developers pull work from “To Do (DoR passed)” into “In Progress.”
- We limit Work In Progress (WIP) so we finish items rather than start many items.
- The Daily Scrum focuses on inspecting progress toward the sprint goal and adapting the plan for the next 24 hours (including surfacing blockers and agreeing who will remove them).
- Work is not considered Done until it meets the Definition of Done (DoD) and evidence is attached.

**Example (Step 6 execution in practice)**

- **Board states:** To Do → In Progress → In Review → In Test → Done  
- **WIP rule:** Maximum 3 items in In Progress for the team (if we hit the limit, we stop starting new work and we finish what is already started).

- **Day 2 blocker:** The vendor sandbox returns inconsistent error responses (for example, the same failure sometimes comes back with different HTTP status codes), so reliable retry/backoff rules are unclear because different HTTP codes imply different client actions (retry, back off, or stop) until the vendor behaviour is stable.  
  - **Action:** we log a blocker on the board and assign an owner. Until the vendor error semantics are clarified, we implement a conservative, safe failure behaviour:
    - we show the last successfully retrieved status (if one exists) so agents can still work,
    - we label it clearly as potentially out of date (“Status may be stale”) so we do not mislead customers,
    - we log each failure with a correlation ID so we can link the user action to the exact vendor call and share precise evidence with the vendor,
    - and we provide a “Retry/Refresh status” button that triggers one new fetch, and we disable it for a short cooldown period (for example, 60 seconds) so repeated clicks do not overload or throttle the vendor API.
    We escalate to the vendor with evidence (timestamps, correlation IDs, sample responses) if the sandbox behaviour is still inconsistent by end of day.

- **Day 4 risk:** Security approval for the vendor API key is delayed, and the integration work is now blocked.  
  - **Action:** the Product Owner and Scrum Master escalate and ask for a yes/no decision by a specific time (for example, “approve or reject by today 16:00”). If approval is not granted by that time, we apply the swap rule so the sprint remains honest:
    - we move the blocked integration item out of the sprint backlog,
    - we pull in Ready work of comparable size that still supports the goal (for example, dashboard UI wiring with stub data, test cases, monitoring dashboards, and runbook notes),
    - and we record the trade-off in the sprint notes so stakeholders can see exactly what changed and why.
    We keep the sprint goal unchanged when this re-plan still delivers the same outcome; if the outcome is no longer achievable, we explicitly agree a revised sprint goal and record the decision.

This is the point of Scrum discipline: the board shows reality, and we act early.

### Step 7 — Sprint Review (demo + acceptance decision)

The Sprint Review is where we show working software, confirm whether it meets the agreed acceptance criteria, and adjust priorities based on what we learn.

At the Sprint Review:
- we demo completed items by walking through the acceptance criteria (not slides),
- the Product Owner makes an explicit acceptance decision (accept or reject) based on evidence,
- and any feedback becomes a concrete backlog update (a new item, a changed priority, or updated acceptance criteria).

**Example (Sprint Review for the payment-status feature)**  
- **Demo scenario 1 (happy path):** We open an order in the support dashboard and the status displays `PAID` with a “Last updated at” timestamp.  
- **Demo scenario 2 (vendor failure):** We simulate a vendor timeout and the dashboard shows the last known status with a clear “Status may be stale” warning.  
- **Evidence shown during the demo:** test results (or screenshots), logs for the failing call, and a metric/dashboard view showing success and failure counts.

**Acceptance outcome**
- The Product Owner accepts Story A and Story B because the demo meets the acceptance criteria and evidence is available.
- The Product Owner requests a usability improvement: show the “Retry/Refresh status” button only when the status is stale or the last refresh failed.  
  - We capture this request as a new backlog item and we let the Product Owner decide its priority for the next sprint.

### Step 8 — Sprint Retrospective (process improvement with owned actions)

The Sprint Retrospective is where the team improves the delivery system. We do not treat it as a “talking session.” We treat it as a decision point that produces a small number of concrete changes.

In the Retrospective:
- we identify the main sources of friction from the sprint (for example, where work stalled, what created rework, and what caused delays),
- we choose the top 2–3 improvements that will remove the most friction,
- we assign an owner and a due date for each improvement,
- and we track completion in the next sprint (so improvements do not disappear).

**Example (Retrospective actions from the payment-status sprint)**  
- **Action 1:** Create a vendor readiness checklist that is completed during refinement for every integration story, so we confirm the external inputs and dependencies before we commit the work into a sprint.  
  - **Access and credentials:** we identify the authentication method (API key or OAuth client credentials), we obtain the correct sandbox and production credentials from the vendor, and we store them securely (for example, in a secret vault or secured environment variables). When company policy requires it, we also complete the internal security approval for using and storing the credentials. We document who is responsible for credential lifecycle management (where the credential is stored, who can access it, how it is rotated before expiry, and how it is revoked if it is leaked or no longer needed) so access does not become an unmanaged risk.  
  - **Sandbox usability:** we confirm the sandbox is reachable and usable for development and testing (endpoints respond, example requests work, and behaviour is stable enough to validate our logic).  
  - **Quota and throttling:** we confirm rate limits and quota rules (for example, “100 requests per minute”), plus how throttling is signalled and how the vendor expects clients to behave.  
  - **Error semantics:** we confirm which failures should be retried, which require backoff, and which should not be retried (based on the vendor’s documented and observed HTTP status codes and error responses).  
  - **Escalation path:** we confirm who to contact at the vendor, expected response times, and what escalation route we use if vendor issues block delivery.  
  - **Owner:** Scrum Master  
  - **Due:** by Day 2 of the next sprint  
- **Action 2:** Create a reusable “vendor call policy” template that standardises our runtime behaviour for vendor API calls, so every integration handles failures safely and behaves consistently.  
  - **Timeouts:** we define how long we wait before we treat a call as failed.  
  - **Retry and backoff:** we define when we retry, how many attempts we allow, and how wait time increases between attempts (including longer waits when throttling is detected).  
  - **Fallback behaviour:** we define what the system shows and returns when the vendor call fails (for example, show the last known value when it exists, label it as potentially stale, return a safe default when it does not exist, and avoid misleading UI actions).  
  - **Logging and metrics:** we define what we record and measure so we can diagnose issues and verify stability (for example, failure counts by error type, trace identifiers, and basic success-rate metrics).  
  - **Owner:** Developer  
  - **Due:** by Day 3 of the next sprint

### Step 9 — Release (when shipping is in scope)

If the increment is going to production:
- we complete release readiness checks (tests and evidence, monitoring readiness, rollback plan, and stakeholder communications),
- we deploy in a controlled way (often a staged rollout),
- and we verify service health after release using monitoring signals and key user journeys.

**Example (Step 9 release approach)**  
- **Release readiness checks:** test evidence attached; monitoring dashboards and alerts ready; rollback plan written; support team briefed on expected behaviour and known limitations.  
- **Controlled ship:** deploy during the Wednesday release window, but enable the new capability only for a small pilot group of support agents at first (for example, 5 agents) using an access restriction (for example, pilot-only roles/permissions or a configuration switch). We validate using a predefined set of test orders, and we expand access to all agents only after pilot results and monitoring signals are healthy.  
- **Post-release verification:** confirm the status lookup success rate stays above 95% and the vendor-call error rate stays below the agreed threshold; if thresholds are breached, pause the rollout and apply the rollback plan.

<blockquote>
⬆ <a href="#on-this-page">Back to navigation</a>
</blockquote>

---

## On this page {#on-this-page}

- [How Scrum runs end-to-end (the operating loop)](#how-scrum-runs)
- [Operating principles](#principles)
- [Roles and decision rights](#roles)
- [Backlog system](#backlog)
- [Boards (pre-sprint intake and sprint execution)](#boards)
- [Definition of Ready checklist](#dor)
- [User story and acceptance criteria example](#story-example)
- [Scrum events](#events)
- [Sprint planning template](#sprint-planning-template)
- [Mid-sprint intake rule](#mid-sprint-intake)
- [Delivery tracking and signals](#tracking)
- [Definition of Done with release readiness and operational hooks](#dod)
- [How I adapt Scrum in regulated or integration-heavy work](#adapt)
- [Typical artifacts I maintain](#artifacts)

---

## Operating principles {#principles}

I use Scrum as a **delivery control system** that helps a team ship reliable increments, make decisions early, and keep risk visible. I do not treat Scrum as “a set of meetings,” because meetings without outputs do not protect schedule, quality, or stakeholder trust.

- I deliver **small, testable increments** that can be demonstrated end-to-end (even in a test environment), and I use demos to validate direction early (I show working behaviour against acceptance criteria, I confirm that stakeholders accept what they see, and I capture feedback as specific backlog updates rather than informal comments).  
  - *Example:* I demo a feature slice that proves the critical flow works, I show the failure-mode handling (timeout, validation error, retry), and I confirm whether the Product Owner wants adjustments before we build further.

- I keep **one source of truth** for overall scope and priorities (the Product Backlog, ordered by the Product Owner). At Sprint Planning we select a subset of Ready items from the Product Backlog to form the Sprint Backlog (the committed scope for that sprint), and we execute and track that work on a board with explicit states so everyone can see progress and risk clearly and consistently (what is started, what is blocked, what is waiting for review or test, and what is truly Done).  
  - I treat the Product Backlog as the master list of everything that might be done, and I use it to make scope decisions visible (what is in, what is out, what is next).  
  - I treat the Sprint Backlog as the sprint’s committed slice of the Product Backlog, and I use the board to show execution truth during the sprint (what is in progress, what is blocked, and what is completed to the Definition of Done).  
  - *Example board states:* To Do (DoR passed) → In Progress → In Review → In Test → Done (where “Done” means it meets the Definition of Done and includes evidence).

- I protect flow and predictability by limiting **WIP (Work In Progress)** and by removing blockers quickly so the team can keep moving toward the Sprint Goal, because starting more work does not mean we are making progress.  
  - I limit how many items can be “In Progress” at the same time, and I prefer finishing work before starting new work.  
  - I treat blockers as time-sensitive risks (I name the unblocker, I set a deadline, and I escalate when the deadline is at risk).  
  - *Example:* If QA testing is the bottleneck, I stop pulling new development work and I shift effort to fix defects and clear the test queue.

- I keep delivery risk visible using a lightweight **RAID log (Risks, Assumptions, Issues, Dependencies)** when uncertainty or external dependencies are non-trivial (for example, vendor deliverables, access approvals, compliance gates, or integration test windows).  
  - I review RAID regularly (at least weekly), and I keep each entry actionable (owner, impact, mitigation, due date, and escalation trigger).  
  - *Example:* “Dependency: vendor must deliver SDK version 2.3 by Thursday. Owner: vendor delivery lead. Risk: if the SDK arrives late or is unstable, we will not complete integration testing, and the release will slip. Mitigation: require a usable early build by Tuesday so we can start integration and catch incompatibilities early (provide version + package + install instructions, and we run a smoke test in the test environment). Escalation trigger: if no usable build is available by Tuesday 18:00, we de-scope the integration from this release and ship the remaining scope.”

- I make change explicit, because silent change is the main cause of missed commitments. If scope, dates, or cost assumptions change, I record the decision, I confirm who approved it, and I update the plan so everyone sees the new baseline.  
  - I use a simple rule: if urgent work enters a sprint, something of similar size leaves the sprint, and the trade-off is written down.  
  - *Example:* “New urgent security fix is pulled into the sprint. We remove Story X (non-critical improvement). The Product Owner approves the swap. The sprint goal is updated, and the decision is recorded in sprint notes.”

These principles keep delivery predictable because they create a repeatable system: clear priorities, visible work, controlled WIP, explicit risk tracking, and written decisions when reality changes.

<blockquote>
⬆ <a href="#on-this-page">Back to navigation</a>
</blockquote>

---

## Roles and decision rights {#roles}

I use Scrum roles as the default, and I make decision ownership explicit so progress does not depend on hierarchy.

### Standard Scrum accountabilities

- **Product Owner**
  - The Product Owner owns backlog ordering and scope trade-offs.
  - The Product Owner accepts completed work against acceptance criteria.
  - The Product Owner decides what is most valuable next.

- **Scrum Master**
  - The Scrum Master protects the process and improves flow.
  - The Scrum Master removes impediments and coaches the team on Scrum discipline.
  - The Scrum Master ensures that events produce outcomes, not only discussion.

- **Developers**
  - Developers own delivery execution and technical quality.
  - Developers decide how to implement the work and how to break it down.
  - Developers keep the work shippable by meeting the Definition of Done.

### Common real-world additions (when the environment is complex)

When delivery includes external vendors, multiple internal teams, or heavy governance, I may also operate as a **Technical Project Manager** who coordinates cross-team dependencies, release readiness, and stakeholder reporting. I do not replace Scrum roles. I make sure the operating model stays clear by writing down who decides what.

### Decision rules (what prevents endless debates)

- The Product Owner decides **priority and scope**.
- Developers decide **implementation approach and estimates**.
- The Scrum Master decides **process improvements and flow rules**.
- If a decision affects security, privacy, or production risk, I require explicit review and sign-off by the relevant accountable owner using **RACI (Responsible, Accountable, Consulted, Informed)**.

<blockquote>
⬆ <a href="#on-this-page">Back to navigation</a>
</blockquote>

---

## Backlog system {#backlog}

### What goes in the backlog

I keep one backlog that includes:
- features and improvements,
- defects and reliability work,
- operational readiness tasks,
- technical debt,
- risk reduction items (for example, proof-of-concept tasks, performance checks, security improvements).

### How work becomes “real” work (not random requests)

A request becomes a backlog item only after I capture:
- the outcome it enables (what user value or business value it creates),
- the success measure (what observable signal proves it worked),
- the constraints (for example, privacy/security needs, release window constraints, vendor lead time),
- the dependencies (who must provide what, and by when).

### How I keep backlog items small enough to deliver

I split work until each item can be completed in a sprint without hidden dependencies.
If an item cannot be sized confidently, I create a time-boxed “discovery spike” that produces specific outputs (for example, an interface decision, a list of unknowns, and a proposal for next steps).

<blockquote>
⬆ <a href="#on-this-page">Back to navigation</a>
</blockquote>

---

### Boards (how work flows from idea → sprint → Done) {#boards}

Scrum does not require a specific board design, but a board is one of the best ways to make work **transparent** and keep flow **predictable**.  
I use two linked boards, because they solve two different problems:

- The **pre-sprint intake board** prevents unclear work from entering a sprint.
- The **sprint execution board** shows real delivery state during the sprint.

---

#### 1) Pre-sprint intake board (prepare work so sprint planning is fast) {#pre-sprint-board}

This board answers one question: *“Is this work clear enough to plan and deliver?”*  
Items move left-to-right until they are eligible to be pulled into a sprint.

**Typical columns**

- **Draft**  
  The request exists, but it is not ready for planning. I still need clarity on outcome, scope, or constraints.

- **Refinement**  
  The team and Product Owner clarify the item. We split work, identify dependencies, and write acceptance criteria.

- **Ready (DoR passed)**  
  The item satisfies the **Definition of Ready (DoR)** checklist. It is eligible for sprint planning.

- **Selected for Sprint**  
  The Product Owner and team have agreed to include the item in the next sprint based on priority and capacity.

**Flow rule (the key discipline)**  
An item cannot move into **Ready (DoR passed)** unless it meets the DoR checklist (outcome, testable acceptance criteria, dependencies, constraints, and estimate readiness).

**Example flow**
- “New vendor API integration request” starts in **Draft**
- It moves to **Refinement** while we confirm:
  - required endpoints and data fields,
  - security/privacy constraints,
  - environments and credentials,
  - vendor delivery date and version,
  - acceptance criteria and evidence expectations
- It moves to **Ready (DoR passed)** once the DoR checklist is satisfied
- It moves to **Selected for Sprint** when the team confirms it fits the next sprint goal and capacity

---

#### 2) Sprint execution board (deliver work inside the sprint) {#sprint-board}

This board answers a different question: *“What is the real delivery state right now?”*  
The sprint board is where Developers pull work and where I detect bottlenecks early.

**Typical columns**

- **To Do (DoR passed)**  
  Work that is in the sprint scope and is ready for Developers to start. “To Do” is the sprint version of “Ready.”

- **In Progress**  
  Work actively being implemented. I limit **WIP (Work In Progress)** here to protect flow.

- **In Review**  
  Work waiting for code review, peer review, or merge approval.

- **In Test**  
  Work being validated (unit, integration, system checks, or QA verification depending on context).

- **Done (DoD met + evidence linked)**  
  Work that satisfies the **Definition of Done (DoD)** and includes evidence links (tests, screenshots, logs, monitoring, or checklist completion).

**Typical WIP rule (example)**
- I set a maximum number of items allowed in **In Progress** at any time (for example, 2 items per Developer, or a team-wide cap like 5).  
When the cap is reached, the team finishes and unblocks existing items before starting new work.

**Typical blocker rule (example)**
- If an item is blocked for more than 24 hours, we:
  - name the unblocker,
  - set an unblock deadline,
  - and escalate if the deadline threatens the sprint goal.

---

#### 3) How the two boards work together (the simple model)

- The **intake board** protects sprint planning (only Ready items enter a sprint).
- The **sprint board** protects delivery predictability (work moves through explicit states until Done).

In practice:
- Items move **Draft → Refinement → Ready (DoR passed)** before the sprint starts.
- Sprint planning pulls items from **Ready (DoR passed)** into the sprint.
- During the sprint, those items live on the sprint board as **To Do (DoR passed) → In Progress → In Review → In Test → Done (DoD met + evidence linked)**.

This separation prevents the most common failure mode: unclear items entering a sprint and then stalling inside it.

<blockquote>
⬆ <a href="#on-this-page">Back to navigation</a>
</blockquote>

---

## Definition of Ready checklist {#dor}

“Ready” means a backlog item can enter sprint planning without ambiguity, and the team can reasonably forecast delivery.

I use this copy-friendly checklist.

### Definition of Ready (DoR) (copy-friendly) {#dor-checklist}

A backlog item is **Ready** when all required checks below are true.

**1) Outcome and success**
- [ ] The item states the user or business outcome in one sentence.
- [ ] The item states a success measure (for example, a dashboard metric, a pass rate, or a workflow completion rate).
- [ ] The Product Owner confirms the priority and why it matters now.

**2) Scope clarity**
- [ ] The in-scope behaviour is clear.
- [ ] The out-of-scope behaviour is stated so expectations do not drift.
- [ ] Edge cases that could change design are named (for example, offline behaviour, retries, idempotency, concurrency).

**3) Acceptance criteria**
- [ ] Acceptance criteria are written as pass/fail statements.
- [ ] Acceptance criteria cover the happy path and at least the top failure modes.
- [ ] Acceptance criteria reference where evidence will live (for example, test results, screenshots, logs, or a monitoring dashboard).

**4) Dependencies and constraints**
- [ ] Dependencies are listed with owners and expected dates (for example, vendor build, access approval, environment readiness, data availability).
- [ ] Required approvals are known (for example, security review, privacy review, production change approval).
- [ ] Non-functional constraints are stated when they matter (for example, performance, reliability, audit, data retention).

**5) Sizing and plan-ability**
- [ ] Developers can estimate the item.
- [ ] The item is small enough for the sprint, or it has been split into smaller items.
- [ ] The team confirms that the work does not require unknown external lead time inside the sprint.

If any checkbox is not true, I keep the item in refinement and I do not pull it into sprint planning.

<blockquote>
⬆ <a href="#on-this-page">Back to navigation</a>
</blockquote>

---

## User story and acceptance criteria example {#story-example}

Below is a realistic example that shows what “testable” looks like. I use a format that QA and stakeholders can validate without guessing.

### Example user story

**Story**  
As a customer support agent, I want to see the latest payment status for an order, so I can answer customer questions without escalating to engineering.

**Context**
- The order system is internal.
- The payment status comes from a partner API.
- The status must be visible in the support dashboard.

### Example acceptance criteria (Given/When/Then)

1) **Happy path**
- **Given** an order exists and the partner API returns `PAID`, **when** I open the order in the support dashboard, **then** the dashboard shows `PAID` within 3 seconds and it shows the timestamp of the last successful status fetch.

2) **Partner API timeout**
- **Given** the partner API times out, **when** I open the order, **then** the dashboard shows the last known status and it shows a warning message that the status is stale.
- **And** the system logs a timeout event with the order ID and correlation ID.

3) **Partner API error response**
- **Given** the partner API returns a 4xx or 5xx error, **when** I open the order, **then** the dashboard shows the last known status and it shows an error state that instructs the agent to retry in 5 minutes.
- **And** the system records the failure count and raises an alert when failures exceed the threshold defined in the release readiness checklist.

4) **Data consistency**
- **Given** the partner returns a status update that is older than the currently stored timestamp, **when** the system processes the response, **then** the system ignores the older update and it keeps the newest status.

5) **Auditability**
- **Given** a status is updated, **when** the update is saved, **then** the system writes an audit entry that includes the old status, the new status, the timestamp, and the request correlation ID.

This structure makes acceptance objective, and it makes “done” provable through evidence.

<blockquote>
⬆ <a href="#on-this-page">Back to navigation</a>
</blockquote>

---

## Scrum events {#events}

I run Scrum events with explicit inputs and explicit outputs. If an event does not produce outputs, it becomes a status meeting, and I stop it.

### Backlog refinement (continuous activity)

**Purpose**: Make upcoming work Ready by reducing uncertainty before sprint planning.  
**Inputs**: Candidate items, latest constraints, dependency updates, production learnings.  
**Outputs**: Split items, clarified scope, updated acceptance criteria, identified dependencies, updated estimates.

### Sprint planning

**Purpose**: Set a sprint goal and make a realistic commitment based on real capacity.  
**Inputs**: Priority backlog items, DoR checks, capacity and interrupts forecast, known risks.  
**Outputs**: Sprint goal, selected sprint backlog, named owners, identified sprint risks and dependencies.

### Daily Scrum

**Purpose**: Coordinate work and unblock flow within 15 minutes.  
**Inputs**: Board state, blockers, planned work for the next 24 hours.  
**Outputs**: Clear next steps, named unblockers, escalations triggered when needed.

### Sprint review

**Purpose**: Validate outcomes with stakeholders using working increments.  
**Inputs**: Completed items that meet the Definition of Done, demo plan, release notes if shipping.  
**Outputs**: Acceptance decisions, feedback captured as backlog items, priority adjustments.

### Sprint retrospective

**Purpose**: Improve the delivery system and reduce recurring waste.  
**Inputs**: Sprint signals (carryover, blockers, defects, cycle time), team feedback.  
**Outputs**: Two to three improvement actions with owners and due dates, plus a decision on what to stop doing.

<blockquote>
⬆ <a href="#on-this-page">Back to navigation</a>
</blockquote>

---

## Sprint planning template (copy-friendly) {#sprint-planning-template}

I use this structure because it forces clarity on capacity, scope, and risk.

### Sprint planning (template)

**Sprint**
- Sprint number:
- Sprint dates:
- Sprint goal (one sentence outcome):
- Release intent (ship this sprint, ship next sprint, or not yet shipping):

**Capacity and constraints**
- Team members available:
- Planned time off:
- Expected interrupts (support, incidents, meetings):
- Effective delivery capacity (hours or points):

**Candidate items (must be Ready)**
- Item 1:
  - Outcome:
  - Acceptance criteria link:
  - Dependencies:
  - Estimate:
- Item 2:
  - Outcome:
  - Acceptance criteria link:
  - Dependencies:
  - Estimate:

**Commitment**
- Included items:
- Explicitly excluded items:
- What we will de-scope first if risk materialises:

**Risks and dependencies (sprint-level)**
- Risk 1:
  - Mitigation:
  - Owner:
  - Escalation trigger:
- Dependency 1:
  - Owner:
  - Due date:
  - What happens if it slips:

**Definition of Done reminder**
- We only count work as Done when it meets the DoD checklist and evidence is attached.

**End-of-sprint review plan**
- Demo order and stakeholders invited:
- Acceptance criteria to verify during the demo:

<blockquote>
⬆ <a href="#on-this-page">Back to navigation</a>
</blockquote>

---

## Mid-sprint intake rule (urgent work and swaps) {#mid-sprint-intake}

Mid-sprint change is a major cause of invisible scope creep, burnout, and missed commitments. I handle it with one rule set.

### What qualifies as urgent

I treat work as urgent only when it meets at least one condition below:
- The work mitigates an active production incident or prevents a likely incident with clear evidence.
- The work addresses a security vulnerability that requires immediate remediation.
- The work prevents a contractual or regulatory breach with a hard deadline.
- The work unblocks a release-critical dependency that would otherwise slip the committed sprint goal.

If work is “important” but not urgent, it goes into the backlog and it is prioritised normally.

### The swap rule (how we protect the sprint)

If urgent work must enter the sprint, I apply all steps below:

1) The requester states why the work is urgent using one sentence and one evidence link.  
2) The Product Owner approves the urgency classification and agrees what outcome is protected.  
3) Developers estimate the urgent item quickly.  
4) We remove work of similar size from the sprint backlog, and we record what we removed.  
5) We update the sprint goal if the change materially alters the sprint outcome.  
6) We write the decision in the sprint notes so the reason is traceable.

This approach keeps transparency: stakeholders see the trade-off instead of silently increasing scope.

<blockquote>
⬆ <a href="#on-this-page">Back to navigation</a>
</blockquote>

---

## Delivery tracking and signals {#tracking}

I track a small set of signals that show predictability, flow health, and quality. I do not use metrics as targets that people game.

### The minimum signals I keep visible

- **Planned vs done**: I track what we committed to and what we completed, and I name the drivers when we miss.  
- **Burndown**: I track remaining work to detect slippage early.  
- **Burnup**: I track completed scope against total scope so scope creep is visible.  
- **Cumulative flow**: I detect bottlenecks by seeing where work piles up across workflow stages.  
- **Cycle time**: I track time from “In Progress” to “Done” to reveal waiting and rework.  
- **Defect leakage**: I track defects found after release vs defects found before release.  
- **Change failure rate**: I track how often releases cause incidents, rollbacks, or hotfixes.  
- **MTTR (Mean Time To Restore)**: I track how quickly the service recovers after incidents when I own or influence operations.

### Workflow rules that improve predictability

- I keep a board with explicit states (for example, Ready, In Progress, In Review, In Test, Done).
- I limit WIP so “started work” does not hide “unfinished work.”
- I require evidence links at Done so stakeholders can trust the status.

<blockquote>
⬆ <a href="#on-this-page">Back to navigation</a>
</blockquote>

---

## Definition of Done with release readiness and operational hooks {#dod}

I treat the **Definition of Done** as the quality gate that keeps increments potentially shippable. Once I expand “Definition of Done” on a page, I refer to it as **DoD**.

Below is the DoD I use for integration-heavy systems and production services. Teams can simplify it for low-risk work, but I keep the intent.

### DoD (copy-friendly checklist) {#dod-checklist}

**1) Functional completion**
- [ ] The implementation meets the acceptance criteria.
- [ ] The key failure modes are handled and tested (for example, timeout, retries, validation errors).

**2) Code quality**
- [ ] Code is merged via review, and review feedback has been addressed.
- [ ] Automated tests pass in the pipeline.
- [ ] Configuration is externalised and documented.

**3) Test evidence**
- [ ] Unit and integration tests exist and pass.
- [ ] If end-to-end testing is needed, evidence is attached or linked.
- [ ] If **SIT (System Integration Testing)** or **UAT (User Acceptance Testing)** is required, the entry criteria are met and the plan is updated.

**4) Security and privacy (when relevant)**
- [ ] Access control is least-privilege and reviewed.
- [ ] Secrets are handled correctly and are not stored in code.
- [ ] If personal data is involved, the required privacy review is completed and recorded, including **DPIA (Data Protection Impact Assessment)**-style risk thinking when risk is non-trivial.

**5) Operational hooks (production readiness)**
- [ ] Logs include correlation IDs and meaningful error context.
- [ ] Metrics exist for the critical path (success rate, latency, error rate).
- [ ] Alerts exist for the top failure modes, and alert ownership is clear.
- [ ] A basic runbook section exists (how to check health, how to mitigate common failures).

**6) Release readiness (when shipping is in scope)**
- [ ] Release notes describe what changed and what to watch.
- [ ] A rollback path is defined, and rollback triggers are stated.
- [ ] If feature flags are used, the enable and disable plan is documented.
- [ ] Post-release verification steps are written and owned.

**7) Documentation**
- [ ] User-facing or operational documentation is updated.
- [ ] Interface changes are documented with versioning and compatibility notes.

If any checkbox is not true, the item is not Done. It may be “nearly done,” but it is not Done.

<blockquote>
⬆ <a href="#on-this-page">Back to navigation</a>
</blockquote>

---

## How I adapt Scrum in regulated or integration-heavy work {#adapt}

Scrum works best when governance scales with risk rather than becoming permanent bureaucracy.

- In regulated or high-risk delivery, I add explicit gates for security, privacy, and release readiness, and I define who approves each gate using RACI.
- In vendor-dependent delivery, I add integration milestones, explicit dependency due dates, and escalation triggers so the sprint does not fail silently.
- In multi-stakeholder environments, I keep decisions written down (what we decided, why, and who approved) so scope and priorities do not reset every week.
- In production services, I treat operational readiness as part of DoD, not as a post-release afterthought.

<blockquote>
⬆ <a href="#on-this-page">Back to navigation</a>
</blockquote>

---

## Typical artifacts I maintain {#artifacts}

- Product Backlog and sprint backlog (with acceptance criteria and evidence links)
- DoR checklist and DoD checklist
- Board workflow definition and WIP limits
- RAID log when risk and dependencies are non-trivial
- Release readiness checklist and evidence pack for higher-risk releases
- Sprint notes that capture decisions, trade-offs, and improvement actions

<hr>

<p>
  <strong>Next:</strong>
  🔎 <a href="/project-delivery/waterfall-stage-gate/">Waterfall / stage-gate</a>
  · <a href="/project-delivery/artifacts-governance/">Artifacts &amp; governance</a>
  · <a href="/project-delivery/sdlc/">SDLC in practice</a>
  · <a href="/project-delivery/">Back to Project Delivery &amp; Methods</a>
</p>
