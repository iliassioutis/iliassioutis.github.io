---
layout: default
title: Data & Analytics Delivery Playbook (how I run it)
---

<blockquote>
🏠 <a href="/">Back to homepage</a> · <a href="/project-delivery/">Project Delivery &amp; Methods</a>
</blockquote>

This page is a practical playbook for running **Data & Analytics** delivery (including **AI (Artificial Intelligence)** and **ML (Machine Learning)** work) in a way that stays predictable even when the organization is still building structure.

It is written for a visitor who wants to understand:
- how work enters the team,
- how priorities are decided,
- how delivery stays stable when urgency appears,
- how quality is protected before release,
- and how forecasts become credible over time.

<a id="contents"></a>
## Contents
- [At a glance](#at-a-glance)
- [Who this system is for](#who-this-system-is-for)
- [The operating loop](#the-operating-loop)
- [Key artifacts](#key-artifacts)
- [Intake](#intake)
- [Triage and urgency rules](#triage)
- [Prioritization cadence](#prioritization)
- [Execution and WIP control](#execution-wip)
- [Visibility and reporting](#visibility-reporting)
- [Multi-project control](#multi-project-control)
- [Estimation and forecasting](#estimation-forecasting)
- [Definition of Done](#definition-of-done)
- [Quality gates and release readiness](#quality-gates-release-readiness)
- [AI/ML delivery](#ai-ml-delivery)
- [Data integration and validation](#data-integration-validation)
- [Data quality issues](#data-quality-issues)
- [Templates](#templates)
- [Glossary](#glossary)

---

<a id="at-a-glance"></a>
## At a glance

If you only read one section, read this.

I make delivery predictable by putting a lightweight operating system in place:

- **One intake path** so requests do not arrive through side channels.
- **One shared backlog** so everyone sees the same priority order.
- **Clear triage rules** so “urgent” has criteria, not emotion.
- **A weekly decision cadence** so priorities change intentionally, not randomly.
- **A simple execution window** so the team can finish work without constant context switching.
- **A Definition of Done (DoD)** so “done” means “ready for business use.”
- **A release readiness review** so changes go live only when evidence exists.
- **A feedback loop** so estimation and forecasting improve using real delivery data.

The tool does not matter as much as the discipline. The structure works in a ticket tool, a work management platform, or even a spreadsheet, as long as the team follows the same rules.

[↑ Back to contents](#contents)

---

<a id="who-this-system-is-for"></a>
## Who this system is for

This operating model works best when:
- multiple stakeholders submit requests with competing priorities,
- requirements often start vague and need discovery,
- delivery runs across multiple systems and data sources,
- production stability matters (pipelines, reports, dashboards, integrations),
- and multiple projects run in parallel with shared teams and shared dependencies.

[↑ Back to contents](#contents)

---

<a id="the-operating-loop"></a>
## The operating loop

This is the repeating loop I run every week. Each step is designed to reduce interruptions and increase trust.

1) **Intake** (capture requests consistently)  
2) **Triage** (classify urgency using explicit rules)  
3) **Prioritization** (make tradeoffs and publish the ranked list)  
4) **Execution** (protect a delivery window; manage work in progress)  
5) **Quality & release** (validate, accept, and deploy with readiness evidence)  
6) **Learn & improve** (track plan vs actual and fix the root causes of variance)

[↑ Back to contents](#contents)

---

<a id="key-artifacts"></a>
## Key artifacts

This operating model stays lightweight because it relies on a small set of artifacts that are easy to keep current.

- **Shared backlog (single source of truth):** the ranked list of requested work, approved work, in-progress work, and deferred work, with owners and acceptance criteria.
- **Intake template:** the minimum information required to accept a request into planning or discovery.
- **RAID log:** the list that prevents surprises by making threats and blockers visible, owned, and time-bound.
- **Decision log:** the record of what was decided, who decided it, when it was decided, and what tradeoff the decision implies.
- **Weekly status update (one page):** what changed, what is next, what is blocked, and what decision is needed (with an owner and due date).
- **Release readiness checklist:** the evidence-based gate that confirms testing, validation, acceptance, monitoring, and rollback readiness before go-live.

If the organization has no tooling, these artifacts can live in a shared document and a spreadsheet. The discipline matters more than the platform.

[↑ Back to contents](#contents)

---

<a id="intake"></a>
## 1) Intake: a single entry point for new requests

A “single entry point” means every request enters through one visible path so the team can assess it consistently.

A request can be captured through:
- a simple form,
- a shared email alias,
- a structured message template in a team channel,
- or a ticket tool.

The specific tool is less important than the rule: **requests do not bypass intake**.

### Minimum intake information (so the team can start responsibly)

A request must include enough information to support estimation and a first delivery plan:

- **Business goal:** what decision or outcome this work supports.
- **Requester and owner:** who is asking and who can approve the final output.
- **Deadline and deadline driver:** what event depends on the date.
- **Scope boundaries:** what is in scope and what is explicitly out of scope (even if preliminary).
- **Data sources and systems:** what inputs are involved (or what is currently unknown).
- **Dependencies:** other teams, vendors, approvals, or access needs.
- **Acceptance criteria:** what must be true for the owner to say “this is successful.”
- **Risk and compliance needs:** constraints such as privacy, security, or audit requirements.

If key information is missing, I do not force the team to guess. I move the request into a short discovery step.

[↑ Back to contents](#contents)

---

<a id="triage"></a>
## 2) Triage: urgency rules that reduce chaos

Many teams become chaotic because “urgent” is undefined. I define an urgency filter with a small number of categories.

A request can enter the current execution window only if it matches one of these criteria:

- **Production incident:** a critical report, pipeline, or integration is broken or blocking users.
- **Compliance or audit deadline:** a fixed deadline exists and missing it creates exposure.
- **Fixed executive decision event:** a decision meeting or business event depends on a specific output date.

Within a production incident, I still classify severity (user impact and time sensitivity) so the team expedites only true service blockers.

If a request does not match those criteria, it goes into the backlog and is prioritized in the next prioritization decision.

### A “one in, one out” rule for mid-window changes

An expedite requires approval from the delivery sponsor (accountable for outcomes) and the business owner for the request, and the approvers must also name the item that will be paused.
If someone insists on a mid-window change, I require an explicit tradeoff:

- a decision maker approves the expedite, and
- a planned item is paused to make room.

This prevents the pattern where new work is added without removing work.

[↑ Back to contents](#contents)

---

<a id="prioritization"></a>
## 3) Prioritization: a predictable decision cadence

I run a short, scheduled prioritization decision (weekly, or twice weekly when intake volume is high).

The point of the meeting is not discussion. The point is decision.

The outputs are explicit:

- **Top priorities:** the ranked list for the next delivery window.
- **Not in scope:** what will not be started in that window.
- **Tradeoff plan:** what will be paused if an expedite is approved.

After the meeting, I publish the ranked list in a place everyone can access.

### What changes when trust is high vs low

When trust is high:
- stakeholders escalate priorities through the agreed process,
- forecasts are accepted because they have been accurate,
- decisions are made faster because impacts are visible,
- and interruptions drop because visibility replaces “checking in.”

When trust is low:
- stakeholders push side-channel requests,
- priorities thrash mid-week,
- and delivery feels chaotic even if the team is working hard.

This operating system is designed to raise trust by making tradeoffs visible and keeping promises realistic.

[↑ Back to contents](#contents)

---

<a id="execution-wip"></a>
## 4) Execution: protect delivery with a stable window and limited WIP

Once priorities are set, I protect execution so the team can finish work.

### A protected execution window

A protected execution window means:
- the team executes the agreed priority list during the window,
- new requests are captured immediately,
- but new requests do not enter active work until the next prioritization decision unless they meet the urgency rules.

### WIP: limiting work in progress to reduce context switching

I limit **WIP (Work In Progress)** so too many items are not started at once.

A simple rule works:
- the team works on a small set of active items,
- and the team does not start the next item until one active item finishes.

I set the WIP limit to match real team capacity, so we reduce context switching and improve cycle time.
This is one of the fastest ways to reduce cycle time and improve throughput.

[↑ Back to contents](#contents)

---

<a id="visibility-reporting"></a>
## 5) Visibility: the minimum reporting that actually reduces interruptions

I use two levels of visibility: one for stakeholders and one for the delivery team.

### Stakeholder visibility (outcome and decision focused)

Stakeholders need:
- what was completed,
- what is planned next,
- what is blocked and who must act,
- top risks and active mitigation,
- dependencies and required dates,
- and decisions needed, with owners and deadlines.

This is usually a one-page weekly update.

### Team visibility (execution and blockers focused)

The team needs:
- the items planned for the current delivery window,
- clear owners,
- current blockers and named unblockers,
- dependencies with dates,
- and links to acceptance criteria and DoD checks.

[↑ Back to contents](#contents)

---

<a id="multi-project-control"></a>
## 6) Multi-project control: how I run parallel work without losing control

Multi-project delivery fails when each project has its own private reality. I prevent that by managing across the portfolio.

### One master view across all active work

I maintain a single portfolio view that shows, for each active initiative:
- objective (one sentence),
- business owner,
- delivery lead,
- next milestone and date,
- status (green / yellow / red),
- top risks and blockers,
- and key dependencies.

This prevents “hidden” project risk and makes tradeoffs possible.

### Explicit dependency management

I treat dependencies as first-class items with:
- a dependency owner,
- a required-by date,
- and escalation rules when the date is at risk.

### Separate run work from change work

Operational support can silently consume delivery capacity, so I keep it visible.

I separate:
- **run work** (incidents, production support, urgent fixes),
- from **change work** (planned improvements and new deliverables).

I reserve a defined percentage of capacity for run work so project plans remain realistic.

[↑ Back to contents](#contents)

---

<a id="estimation-forecasting"></a>
## 7) Estimation and forecasting: how dates become credible

Credible forecasting comes from turning unknowns into knowns, then planning against capacity and real throughput.

### When requirements are unclear: use time-boxed discovery

If a request is vague, I do not promise a single date immediately.
I schedule a short discovery time-box (often 2–5 working days) to answer the questions that make estimates possible:

- what decision the deliverable supports,
- who will use it and how,
- what data sources are involved and whether access exists,
- what the **MVP (Minimum Viable Product)** should be,
- what risks and dependencies exist,
- and what “done” means (acceptance criteria).

Discovery output:
- clearer scope boundaries,
- a task list the team can estimate,
- key dependencies and risks,
- and an initial forecast based on evidence rather than guesswork.

### Use ranges before discovery, then refine after discovery

I treat every forecast as conditional on a small set of visible assumptions (for example: access is approved by a specific date, a dependency delivers by a specific date, and scope stays within the agreed acceptance criteria). If an assumption breaks, I update the forecast immediately and present options (reduce scope, move the date, or add capacity) so a stakeholder decision is explicit.

Before discovery: I communicate a range with assumptions.  
After discovery: I replace the range with a refined plan and updated forecast.

### Forecasting signals I rely on

I use a small set of practical metrics:
- milestone plan vs actual,
- work remaining vs team capacity,
- throughput (items completed per week),
- cycle time (start to finish time for similar items),
- blocker aging (how long blockers remain unresolved),
- and estimate variance trends (whether estimates are improving).

### Track variance and act on it

I record:
- estimated effort,
- actual effort,
- variance,
- and a short reason code (access delays, data quality, scope change, incidents, vendor delay, underestimated complexity).

Then I act on the pattern:
- I start access approvals earlier if access delays repeat,
- I add early profiling and validation if data issues repeat,
- I tighten intake and acceptance criteria if scope churn repeats,
- and I reserve capacity if incidents are consistently interrupting delivery.

[↑ Back to contents](#contents)

---

<a id="definition-of-done"></a>
## 8) Definition of Done: what "done" means for data and analytics

In data and analytics, “done” must mean “ready for business use,” not “someone finished building something.”

### DoD for a dashboard or report

A dashboard/report is done when:
- the business purpose is confirmed,
- metric definitions are agreed and recorded,
- data sources and refresh expectations are confirmed,
- data quality checks exist and pass (missing values, duplicates, freshness, outliers),
- calculations are validated against an agreed reference when available,
- access and security are correct,
- the business owner completes **UAT (User Acceptance Testing)** or provides written acceptance with stated risk,
- the go-live message includes the production link, access guidance, and a support path.

### DoD for a dataset or pipeline

A dataset/pipeline is done when:
- source-to-target mapping is documented (what each field means and how it is transformed),
- an end-to-end run succeeds reliably,
- validation checks exist and pass (schema, row counts, duplicates, integrity rules),
- monitoring and alerting are configured,
- security controls are verified (least privilege, secure secrets),
- the output is reconciled and accepted by the business owner,
- and operational ownership is clear (runbook and escalation path).

[↑ Back to contents](#contents)

---

<a id="quality-gates-release-readiness"></a>
## 9) Quality gates and release readiness: how I prevent unsafe releases

I use lightweight quality gates that happen at the right time.

### Gates at the start of work (prevent avoidable waste)
Before build starts, I confirm:
- acceptance criteria exist and the owner agrees,
- data access is planned and owned,
- and key dependencies are identified.

### Gates before release (prove readiness)
Before production release, a short readiness review confirms:
- testing evidence exists for the scope being released,
- validation checks passed and evidence is recorded,
- business acceptance exists (UAT or written acceptance),
- monitoring and an escalation path exist,
- and rollback or mitigation steps are ready.

Evidence can be links to test runs, validation outputs, or sign-off notes attached to the work item.
The goal is not bureaucracy. The goal is to avoid preventable production risk and avoid rework after release.

[↑ Back to contents](#contents)

---

<a id="ai-ml-delivery"></a>
## 10) AI/ML delivery: how I keep experimentation controlled

AI/ML work includes uncertainty, so I manage it as a staged process that still keeps governance strong.

### Separate exploration from delivery

- **Exploration** is time-boxed learning to prove feasibility and baseline performance.
- **Delivery** begins only when exploration produces evidence that the use case can work.

### Define success in measurable business terms

I require success criteria that describe business impact, not only model metrics.
I also require a baseline so improvement is measurable.

### Use stage gates with explicit exit criteria

Instead of promising “the model will be great,” I promise staged deliverables:
- data access and data quality confirmed,
- baseline model produced with baseline metrics,
- improved model that beats the baseline,
- pilot rollout in limited scope,
- operationalization with monitoring and controlled expansion.

### Treat the model as a product in production

When a model goes live, it is not “done” at deployment.
I ensure monitoring exists for:
- performance drift,
- data drift,
- and operational stability.

I also ensure ownership exists for responding to issues and deciding retraining cadence.

[↑ Back to contents](#contents)

---

<a id="data-integration-validation"></a>
## 11) Data integration and validation: how I prevent “garbage in, garbage out”

When integrating multiple sources, reliability depends on clarity, ownership, and layered validation.

I do three things:

1) Define the target dataset (what the integrated output must contain and what it must answer).  
2) Document source-to-target mapping and join rules (where each field comes from and how conflicts are handled).  
3) Validate in layers:
   - technical validation (schema, counts, duplicates, freshness),
   - reconciliation against trusted references when available,
   - and written business acceptance.

When numbers do not match, I treat it as a controlled investigation with an owner, not as an endless debate.

[↑ Back to contents](#contents)

---

<a id="data-quality-issues"></a>
## 12) Data quality issues: how I handle them without hiding the work

Data quality problems are a common reason analytics delivery slips, so I manage them explicitly.

I do this:

- make the issue visible and describe the business impact,
- classify the issue (missing values, duplicates, late arrivals, definition changes),
- identify the source owner and assign accountability,
- choose one of three strategies:
  - fix at the source,
  - fix in the pipeline with documented rules,
  - or limit scope temporarily with written acceptance,
- add validation checks and alerting so the same issue is detected automatically next time,
- and re-plan transparently when data quality work affects the forecast.

[↑ Back to contents](#contents)

---

<a id="templates"></a>
## Templates (copy-friendly)

<details>
<summary><strong>Weekly status update template (one page)</strong></summary>

- Reporting period: [start date] to [end date]  
- Overall status: [green / yellow / red]  
- Completed:  
  - [item 1]  
  - [item 2]  
- Planned next:  
  - [item 1]  
  - [item 2]  
- Blockers (with named unblockers):  
  - [blocker] — [unblocker name] — [expected unblock date]  
- Top risks (with mitigation):  
  - [risk] — [owner] — [mitigation action] — [review date]  
- Dependencies:  
  - [dependency] — [owner] — [required-by date]  
- Decisions needed:  
  - [decision question] — [decision owner] — [due date] — [impact if late]  

</details>

<details>
<summary><strong>Intake template (short)</strong></summary>

- Request title:  
- Business goal / decision supported:  
- Requester and approver (name + role):  
- Deadline and deadline driver (what event depends on the date):  
- Scope (what is in / what is out):  
- Data sources and systems involved:  
- Dependencies (teams, vendors, access approvals):  
- Risk / security / compliance constraints:  
- Acceptance criteria (what must be true to call it successful):  

</details>

<details>
<summary><strong>Release readiness checklist (practical)</strong></summary>

- Automated tests passed (where applicable) and evidence is recorded.  
- A successful end-to-end run completed in the pre-release environment.  
- Data validation checks passed (freshness, duplicates, missing values, outliers) and alerts are configured.  
- UAT is complete, or written business acceptance exists with stated risk.  
- Production access is granted to the intended users, and the production link is ready to share.  
- Rollback or mitigation steps exist, and an owner is named for post-release monitoring.  
- Release notes are prepared, and the support contact path is communicated.  

</details>

[↑ Back to contents](#contents)

---

<a id="glossary"></a>
## Glossary

- **AI (Artificial Intelligence):** systems that perform tasks that normally require human intelligence, such as prediction, classification, or decision support.
- **ML (Machine Learning):** a subset of AI where models learn patterns from data to make predictions or classifications.
- **DoD (Definition of Done):** the checklist that must be true before a deliverable is considered complete and ready for business use.
- **UAT (User Acceptance Testing):** business validation that the deliverable meets the agreed acceptance criteria before release.
- **MVP (Minimum Viable Product):** the smallest version of a deliverable that still provides usable business value.
- **WIP (Work In Progress):** active work items currently being executed; limiting WIP reduces context switching and increases throughput.
- **RAID (Risks, Assumptions, Issues, Dependencies):** the structured log used to track threats, blockers, and external dependencies that can affect delivery.

<p style="margin-top: 1rem;"><a href="#contents">↑ Back to contents</a></p>
