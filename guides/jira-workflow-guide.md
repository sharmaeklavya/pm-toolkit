# Jira Workflow Guide

A practical setup for running Scrum in Jira with clean tickets, traceable code and predictable releases. Adjust names to fit your team.

---

## 1. The workflow

```
Backlog → Ready for Sprint → In Progress → In Code Review → In QA → Ready for Release → Done
                                   ↑              │             │
                                   └──── Blocked / Rework ──────┘
```

| Status | Meaning | Who moves it | Exit rule |
|---|---|---|---|
| **Backlog** | Idea or request, not yet refined | Anyone | Refined with acceptance criteria |
| **Ready for Sprint** | Meets the Definition of Ready | Product owner / PM | Pulled into a sprint |
| **In Progress** | Developer is actively working | Developer | Pull request opened |
| **In Code Review** | PR is waiting for or in review | Developer | PR approved and merged to the test branch |
| **In QA** | Being tested against acceptance criteria | QA / developer | All criteria pass |
| **Ready for Release** | Tested, merged and approved to ship | QA / PM | Included in a release |
| **Done** | Deployed and verified in production | Release owner | None |
| **Blocked** | Cannot progress (use the Blocked flag + comment) | Anyone | Blocker removed |

**Rules of the board**
- One assignee per ticket at a time.
- Move tickets forward yourself and keep the status honest. A stale board is worse than no board.
- A blocked ticket needs a comment saying **what** blocks it and **who** can unblock it.
- Set a **work-in-progress limit** on In Progress and In Code Review (for example, no more than two tickets per developer) so work finishes instead of piling up.

## 2. Issue types

| Type | Use for |
|---|---|
| **Epic** | A large goal spanning several sprints |
| **Story** | User-facing value delivered in one sprint |
| **Task** | Technical or operational work with no direct user story |
| **Bug** | Something that worked or should work, but does not |
| **Sub-task** | A small piece of a story, used sparingly |
| **Spike** | Time-boxed research to reduce uncertainty |

## 3. Priority and bug severity

| Priority | Meaning | Target response |
|---|---|---|
| **Highest** | Production down or data at risk | Start immediately, hotfix |
| **High** | Major feature broken, no workaround | Current sprint |
| **Medium** | Important but has a workaround | Next sprint or two |
| **Low** | Minor or cosmetic | Backlog |

## 4. Ticket-to-code alignment

Every piece of work should be traceable from idea to release through the **same ticket key**.

| Where | Convention | Example |
|---|---|---|
| Branch name | `PROJ-123-short-description` | `PROJ-123-invoice-pdf-export` |
| Commit message | `PROJ-123: what changed` | `PROJ-123: add PDF export endpoint` |
| Pull request title | `PROJ-123: title` | `PROJ-123: Add invoice PDF export` |
| Release notes | Ticket key beside each item | `PROJ-123 Download invoices as PDF` |

**Why it matters:** when something breaks in production, you can trace it to a ticket, a PR, and a reviewer in seconds. Connect Jira to GitHub so branches, commits and PRs appear on the ticket automatically.

**Code review discipline**
- Every change goes through a pull request, no direct pushes to the main branch.
- At least one approving review before merge.
- Keep PRs small. Aim for something reviewable in under 30 minutes.
- Reviewers respond within one working day.
- The author fills in the pull request template.

## 5. A good ticket

**Title:** short, specific, action-oriented ("Add PDF download to invoice page", not "PDF").

**Description should include:**
- Context: why this is needed
- Acceptance criteria: testable, ideally Given / When / Then
- Out of scope
- Designs or links
- Dependencies

**Fields to keep filled:** assignee, priority, story points, sprint, epic link, labels, fix version.

## 6. Scrum cadence (two-week sprint example)

| Ceremony | When | Length | Output |
|---|---|---|---|
| **Backlog refinement** | Mid-sprint | 60 min | Stories meet Definition of Ready |
| **Sprint planning** | Day 1 | 60-90 min | Sprint goal and committed scope |
| **Daily stand-up** | Daily | 15 min | Blockers surfaced, work coordinated |
| **Sprint review** | Last day | 45-60 min | Demo to stakeholders, feedback captured |
| **Retrospective** | Last day | 60 min | 1-3 owned improvement actions |

**Stand-up format:** what moved since yesterday, what will move today, what is blocked. Look at the board rather than going person by person.

## 7. Releases in Jira

- Create a **Version** (fix version) for each release, for example `v1.4.2`.
- Assign a fix version to every ticket going out.
- Only tickets in **Ready for Release** may be included.
- After deployment and verification, mark the version as released and move tickets to **Done**.
- Use the [release checklist](../templates/release-checklist.md) for every release.

**Smaller, more frequent releases** lower risk. Many small releases with a checklist are safer than one large release with many changes.

## 8. Useful filters (JQL)

```sql
-- My open work
assignee = currentUser() AND resolution = Unresolved ORDER BY priority DESC

-- Blocked tickets in the active sprint
sprint in openSprints() AND (flagged = Impediment OR status = Blocked)

-- Work stuck in review for more than 2 days
status = "In Code Review" AND status changed to "In Code Review" before -2d

-- Tickets ready for the next release
project = PROJ AND status = "Ready for Release" ORDER BY priority DESC

-- Bugs raised in the last 14 days
project = PROJ AND issuetype = Bug AND created >= -14d ORDER BY created DESC

-- Unestimated stories in the backlog
project = PROJ AND issuetype = Story AND "Story Points" is EMPTY AND sprint is EMPTY
```

## 9. Dashboard: what to show

| Gadget | Purpose |
|---|---|
| Sprint burndown | Are we on track for the sprint goal? |
| Velocity chart | Is the team's throughput stable? |
| Cumulative flow diagram | Where does work pile up? |
| Created vs resolved bugs | Is quality improving? |
| Average cycle time | How quickly does work finish? |
| Release frequency and rollbacks (manual or via labels) | Delivery health |

## 10. Weekly hygiene checklist

- [ ] No ticket sits in one status for more than a few days without a comment
- [ ] Every ticket in the sprint has an assignee and an estimate
- [ ] Blocked tickets have an owner and a next step
- [ ] Stale backlog items are closed or reprioritised
- [ ] Bugs are triaged with a priority within one working day
- [ ] Released tickets are moved to Done

## 11. Common problems and fixes

| Problem | Likely cause | Fix |
|---|---|---|
| Sprint scope keeps changing | New asks bypass planning | Freeze scope, route new items to the backlog |
| Tickets bounce back from QA | Unclear acceptance criteria | Enforce Definition of Ready |
| Releases break production | Large batches, weak review | Smaller releases, PR template, release checklist |
| Work piles up in review | No review expectations | Response-time agreement, smaller PRs, WIP limits |
| Nobody trusts the board | Statuses not updated | Update in stand-up, keep the workflow simple |
| Estimates are always wrong | No shared reference | Calibrate against past stories, review in retro |
