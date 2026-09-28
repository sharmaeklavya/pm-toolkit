# Release Checklist

Copy this file for each release. Fill the header, then work through each phase in order.

| | |
|---|---|
| **Release name / version** | [e.g. v1.4.2] |
| **Release date and time** | [date, time, timezone] |
| **Release owner** | [name] |
| **Deploy engineer** | [name] |
| **QA sign-off** | [name] |
| **Environment** | [production] |

---

## 1. Scope

- [ ] All tickets in this release are listed below and are in **Ready for Release**
- [ ] No unreviewed or unmerged work is included
- [ ] Every ticket links to its merged pull request

| Ticket | Summary | PR | Risk (Low / Med / High) |
|---|---|---|---|
| PROJ-101 | | | |
| PROJ-102 | | | |

## 2. Pre-release (day before, or at least a few hours ahead)

**Code and quality**
- [ ] Release branch or tag created from the agreed base
- [ ] Automated tests and CI pipeline pass
- [ ] Code review completed on every pull request
- [ ] Regression test on staging passed
- [ ] Acceptance criteria verified for each ticket
- [ ] Known issues documented and accepted by the product owner

**Technical readiness**
- [ ] Database migrations reviewed, tested on staging and reversible
- [ ] Environment variables and config changes prepared
- [ ] Third-party dependencies and integrations checked
- [ ] Performance-sensitive changes load tested where relevant

**People and communication**
- [ ] Stakeholders notified of release time and expected impact
- [ ] Support team briefed on what is changing
- [ ] Release owner and deploy engineer available for the whole window
- [ ] Avoided release windows: Friday evenings, public holidays, peak traffic

## 3. Go / No-Go

Hold a short check-in before deploying.

| Question | Yes / No |
|---|---|
| Are all checklist items above complete? | |
| Is the rollback plan ready and tested? | |
| Are the right people available right now? | |
| Are there any open high-severity bugs? | |

**Decision:** Go / No-Go &nbsp;&nbsp; **Decided by:** [name] &nbsp;&nbsp; **Time:** [time]

## 4. Release execution

- [ ] Take a backup or snapshot where applicable
- [ ] Announce the start in the team channel
- [ ] Deploy to production
- [ ] Run database migrations
- [ ] Apply config changes
- [ ] Confirm deployment completed without errors

## 5. Post-release verification (first 30-60 minutes)

- [ ] Smoke test the critical user journeys
- [ ] Verify each shipped ticket in production
- [ ] Check error logs and monitoring dashboards for new errors
- [ ] Check performance metrics against normal baseline
- [ ] Verify queues, background jobs and integrations are processing
- [ ] Confirm reporting and data pipelines still run correctly
- [ ] Announce completion to stakeholders

**Monitor closely for 24 hours.** Assign an owner: [name]

## 6. Rollback plan

Decide this **before** releasing, not during an incident.

| Item | Detail |
|---|---|
| **Rollback trigger** | [e.g. critical journey broken, error rate above X%, data corruption] |
| **Rollback decision owner** | [name] |
| **Method** | [redeploy previous tag / revert commit / feature flag off] |
| **Previous stable version** | [version or commit] |
| **Database rollback** | [down migration / restore from backup / not required] |
| **Estimated rollback time** | [minutes] |
| **Who to notify** | [names or channel] |

## 7. Release notes

**Release [version], [date]**

**New**
- 

**Improved**
- 

**Fixed**
- 

**Known issues**
- 

## 8. After the release

- [ ] Move all tickets to **Done** and close the release in Jira
- [ ] Record outcome below
- [ ] If a rollback or incident happened, run a short blameless review and log actions

| Outcome | |
|---|---|
| **Result** | Success / Success with issues / Rolled back |
| **Issues found** | |
| **Actions and owners** | |
