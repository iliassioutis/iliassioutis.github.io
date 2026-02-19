---
layout: default
title: Data & Analytics Delivery Playbook (how I run it)
---

<blockquote>
🏠 <a href="/">Back to homepage</a> · <a href="/project-delivery/">Project Delivery &amp; Methods</a>
</blockquote>

This page explains how I run **Data Analytics and Artificial Intelligence (AI)** delivery in practice, especially when the organization is still building structure.

I wrote this as a **practical playbook**, not as theory:
- I describe the operating system I put in place (intake, prioritization, planning, reporting, quality, and release readiness).
- I explain each abbreviation the first time I use it, and then I use the abbreviation consistently.

---

## Core principle: the tool matters less than the discipline

I can run predictable delivery in Jira, in monday.com, in Trello, in a spreadsheet, or even in a shared document, as long as the team follows a consistent operating discipline.

A tool helps execution, but the tool does not create clarity by itself. I create clarity by enforcing:
- one intake path for requests,
- one prioritized list that the team actually follows,
- one cadence for weekly planning and weekly reporting,
- one Definition of Done (DoD),
- and one release readiness checklist that is reviewed before each release.

---

## What “good” looks like (the outcome)

When the operating discipline is working, stakeholders stop interrupting the team because they can see progress and they trust delivery.

You will see:
- fewer last-minute changes entering a release,
- fewer surprises late in the week,
- clearer ownership for each item,
- faster decisions because the trade-offs are explicit,
- and higher quality because the team releases only when readiness evidence exists.

---

## The delivery system I put in place

### 1) I create a single source of truth (so everyone reads the same reality)

I keep one shared view that includes:
- a prioritized delivery list (what we will do next, and what we will not do next),
- a RAID log (Risks, Assumptions, Issues, Dependencies),
- and a decision log (what was decided, who approved it, and why).

I create the same structure using:
- a spreadsheet for the prioritized list and the RAID log,
- a shared document for the decision log,
- and a simple dashboard or one-page weekly report for visibility.

### 2) I enforce one intake path (so requests do not arrive “randomly”)

A “clear intake” means that every new request must enter through one structured capture method, so the team can assess it consistently.

I use a short intake template that captures:
- what the requester needs,
- why the requester needs it now,
- what business outcome the requester expects,
- what deadline the requester is asking for (and why that deadline exists),
- what data sources or systems are involved,
- and who will approve the final output.

I use this intake path to prevent “hallway requests” and “last-minute messages” from skipping governance.

### 3) I classify urgency (so “urgent” has rules, not emotions)

I define explicit urgency classes and I explain what each class means in delivery terms.

Example urgency model:
- **Class 1 (Release blocker):** A defect or risk prevents a safe release, and the team must fix it before go-live.
- **Class 2 (Time-critical business deadline):** A deadline exists outside the team (for example, a regulatory date or a plant shutdown), and delay causes direct harm.
- **Class 3 (Important but not time-critical):** The request is valuable, but the team can schedule it into the next delivery window.
- **Class 4 (Nice to have):** The request is useful, but the team should only schedule it when capacity is free.

I define who can label something as Class 1 or Class 2, and I require that person to accept the trade-off explicitly.

### 4) I run a weekly prioritization decision (so priorities change intentionally)

I run a short weekly prioritization meeting where the Data Analytics and Artificial Intelligence (AI) Manager and key business stakeholders decide priorities for the next delivery window.

I do not use vague language like “this week” without definition.
I define a delivery window clearly, such as:
- “Monday 16 February 2026 to Friday 20 February 2026.”

In that meeting, the group makes three explicit decisions:
- The group selects the top priorities for the next delivery window.
- The group states what will not be worked on in the next delivery window.
- The group states what will be paused if an approved urgent request arrives.

After the meeting, I publish a ranked list (for example, the top 5 or top 10 items) with one accountable owner per item.

### 5) I publish a weekly status update (so progress is visible and interruption drops)

I publish a weekly status update to the people who request work and to the people who approve work.
In practice, that audience includes:
- the Data Analytics and Artificial Intelligence (AI) Manager,
- the business owners for the priority items,
- and any dependency owners whose actions block progress.

My weekly update answers six questions:
- What did the team complete in the last delivery window?
- What will the team complete in the next delivery window?
- What is blocked, and who must unblock it?
- What risks threaten the plan, and what mitigation is active?
- What dependencies can delay delivery, and what dates do they have?
- What decisions do stakeholders need to make, and by what date?

I keep the weekly update short, but I keep it specific.

---

## The artifacts I use (and what each artifact is responsible for)

### A) Prioritized delivery list (this is the “what we do next” list)
This list is responsible for making the order of work explicit.

For each item, I capture:
- the title and short description,
- the accountable owner,
- the target delivery window,
- the dependency list if another team or vendor must deliver something first,
- and the acceptance criteria that define success.

### B) RAID log (Risks, Assumptions, Issues, Dependencies)
This log is responsible for preventing surprises.

I treat each category differently:
- A **risk** is a future threat that might happen, and I assign an owner to reduce the probability or reduce the impact.
- An **assumption** is something the plan relies on, and I convert it into a confirmed fact or a documented risk.
- An **issue** is a problem that is already happening, and I assign an owner to resolve it by a specific date.
- A **dependency** is an external requirement, and I assign an owner to confirm when it will be delivered.

### C) Decision log (this is the “we agreed” record)
This log is responsible for stopping repeated debates and creating accountability.

Each decision entry captures:
- the decision statement,
- the decision owner,
- the options considered,
- the impact on scope, date, or resources,
- and the decision date.

---

## Estimation and forecasting (how I produce credible dates)

### 1) I start with a small discovery time-box when the work is unclear
When requirements are uncertain, I do not guess a full delivery date immediately.
I time-box a short discovery period so discovery converts unknowns into known tasks.

A discovery time-box produces:
- clarified scope boundaries,
- a list of tasks the team can estimate,
- the top risks and dependencies,
- and a first credible forecast for the remaining delivery.

### 2) I estimate small items, not vague items
I break large items into smaller items until the team can estimate them with confidence.

### 3) I track actual time against estimates, and I learn from variance
I track actual effort against the estimate so the team improves forecasting.

When actuals exceed estimates, I do not hide the variance.
I update the forecast, explain the cause, and propose options:
- I can reduce scope, or I can move the date, or I can add capacity, but I require a stakeholder decision.

---

## DoD for data and analytics

I define DoD so “done” means “ready for business use,” not “a developer finished a task.”

A data or analytics deliverable is done when the team completes these responsibilities:

### 1) Data correctness and validation
The team validates:
- that the dataset contains the required fields,
- that the numbers reconcile against known reference totals when a reference exists,
- and that the team documents any known limitations clearly.

### 2) Data quality checks and monitoring
The team implements checks for:
- completeness (the dataset includes all expected records),
- freshness (the dataset updates on the expected schedule),
- duplicates (the dataset does not double-count),
- and outliers (the dataset flags abnormal values that could indicate a pipeline failure).

### 3) Business acceptance
The business owner completes User Acceptance Testing (UAT: User Acceptance Testing) by validating that the output supports the intended decisions.
If the business owner cannot complete UAT before release, the business owner provides written acceptance that states the risk the business owner accepts.

### 4) Operational readiness
The team provides:
- a short runbook that explains how the team monitors the pipeline and how the team responds to failures,
- and a clear owner for ongoing support.

---

## Quality gates and release readiness (how I prevent unsafe releases)

I introduce a lightweight readiness review before release.

The readiness review confirms:
- the deliverable meets the DoD,
- the team completed the validation checks and recorded the evidence,
- the business owner completed UAT or provided written acceptance,
- and the team can roll back or disable the change if production problems occur.

I treat the readiness review as a normal part of delivery, not as an optional ceremony.

---

## How I manage AI and ML work when experimentation is required

Machine Learning (ML) work includes uncertainty, so I manage it differently while keeping governance strong.

### 1) I separate research exploration from production delivery
I ask the team to classify work as:
- exploration work that tests hypotheses, or
- delivery work that produces a production-ready outcome.

### 2) I use stage-based checkpoints with explicit exit criteria
I require the team to define exit criteria such as:
- “The model improves the target metric in the evaluation dataset.”
- “The model meets performance requirements in the target environment.”
- “The model meets privacy and security constraints for production.”

### 3) I treat the model as a product with monitoring
When the team deploys a model, I ensure the team monitors:
- performance drift,
- data drift,
- and operational stability.

---

## Short templates I use (copy-friendly)

### Weekly status update template (one page)
- Reporting period: [start date] to [end date]
- Completed: [3–6 bullet items]
- Planned next: [3–6 bullet items]
- Blockers: [blocker] — [unblocker name] — [expected unblock date]
- Top risks: [risk] — [owner] — [mitigation action] — [review date]
- Decisions needed: [decision] — [decision owner] — [due date] — [impact if late]

### Intake template (short)
- Request title:
- Business outcome:
- Why now:
- Deadline and reason:
- Data sources and systems involved:
- Stakeholders and approver:
- Security or compliance constraints:
- Acceptance criteria:

---

## Glossary (plain definitions)

- **SDLC (Software Development Life Cycle):** the delivery lifecycle from requirements through build, test, release, and support.
- **SIT (System Integration Testing):** testing that verifies multiple components work together end-to-end.
- **UAT (User Acceptance Testing):** business validation that the output meets needs before release.
- **RAID (Risks, Assumptions, Issues, Dependencies):** the structured log that tracks delivery threats and blockers.
- **RACI (Responsible, Accountable, Consulted, Informed):** the responsibility model that prevents ownership confusion.
- **MES (Manufacturing Execution System):** the factory system that tracks and controls production processes and production data.

