# User Story Template

Use this to write stories that developers can build and testers can verify without guessing.

---

## Template

**Ticket:** PROJ-[number]
**Title:** [Short, action-oriented title]

### Story

> **As a** [type of user],
> **I want** [capability],
> **so that** [benefit or outcome].

### Context

[Why this matters. Link the business goal, research, or earlier discussion. Two to four sentences.]

### Acceptance criteria

Write each criterion so it can be answered with pass or fail.

**Scenario 1: [name]**
- **Given** [starting condition]
- **When** [action]
- **Then** [expected result]

**Scenario 2: [name]**
- **Given** 
- **When** 
- **Then** 

**Scenario 3: edge case or error state**
- **Given** 
- **When** 
- **Then** 

### Out of scope

- [Things this story deliberately does not include]

### Design and technical notes

- Design link: [link]
- API or data changes: [notes]
- Dependencies: [tickets, teams, third parties]

### Estimate and priority

| Story points | Priority | Sprint |
|---|---|---|
| | | |

---

## Definition of Ready

A story enters a sprint only when all of these are true.

- [ ] The story has a clear user, need and benefit
- [ ] Acceptance criteria are written and agreed with the product owner
- [ ] Dependencies are identified and not blocking
- [ ] Designs or mockups are attached where relevant
- [ ] The team has estimated it
- [ ] It is small enough to finish within one sprint
- [ ] Test approach is understood

## Definition of Done

A story is done only when all of these are true.

- [ ] Code is written and merged through a reviewed pull request
- [ ] Acceptance criteria are verified
- [ ] Automated tests are added or updated and passing
- [ ] No known critical or high-severity bugs remain
- [ ] Documentation or release notes are updated where needed
- [ ] Deployed to the target environment and verified
- [ ] Product owner has accepted it

---

## Example

**Ticket:** PROJ-214
**Title:** Download invoice as PDF

> **As a** sales executive,
> **I want** to download a finished invoice as a PDF,
> **so that** I can send it to my client without retyping it.

**Context:** Clients expect a printable copy. Today users copy details into a separate document, which causes errors.

**Scenario 1: successful download**
- **Given** I am viewing a saved invoice
- **When** I select "Download PDF"
- **Then** a PDF downloads containing the client name, line items, totals and payment terms

**Scenario 2: access by role**
- **Given** I am logged in with any role
- **When** I open an invoice I can view
- **Then** the "Download PDF" option is available

**Scenario 3: error state**
- **Given** the PDF cannot be generated
- **When** I select "Download PDF"
- **Then** I see a clear error message and can retry without losing my data

**Out of scope:** emailing the PDF directly, custom invoice branding.

## Splitting large stories

If a story cannot fit in a sprint, split it by:
- **Workflow step** (create, then edit, then delete)
- **User role** (admin first, other roles later)
- **Happy path first**, edge cases second
- **Data variation** (one format first, more later)

Avoid splitting by technical layer (front end story, back end story). Each story should deliver something a user can see.
