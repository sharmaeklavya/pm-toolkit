# Risk Register

Review this in every sprint planning or weekly delivery sync. A risk that is written down and owned is far less dangerous than one everyone quietly worries about.

| | |
|---|---|
| **Project / release** | [name] |
| **Owner** | [name] |
| **Last reviewed** | [date] |

---

## Scoring guide

**Probability**

| Score | Meaning |
|---|---|
| 1 | Rare, unlikely to happen |
| 2 | Possible |
| 3 | Likely |
| 4 | Almost certain |

**Impact**

| Score | Meaning |
|---|---|
| 1 | Minor, absorbed within the sprint |
| 2 | Moderate, sprint goal or a release slips slightly |
| 3 | Major, milestone or customer commitment at risk |
| 4 | Severe, project outcome or trust at risk |

**Risk score = Probability × Impact**

| Score | Level | Response |
|---|---|---|
| 1-4 | 🟢 Low | Monitor |
| 5-8 | 🟡 Medium | Plan a mitigation and assign an owner |
| 9-16 | 🔴 High | Escalate to stakeholders and act now |

## Response types

- **Avoid:** change the plan so the risk cannot occur
- **Mitigate:** reduce the probability or the impact
- **Transfer:** move it to someone better placed to handle it (vendor, insurance, another team)
- **Accept:** consciously live with it, with a contingency ready

---

## Register

| ID | Risk (cause → event → effect) | Category | Prob. | Impact | Score | Response | Mitigation / contingency | Owner | Status | Review date |
|---|---|---|---|---|---|---|---|---|---|---|
| R1 | | | | | | | | | Open | |
| R2 | | | | | | | | | Open | |
| R3 | | | | | | | | | Open | |

**Status values:** Open · Mitigating · Realised · Closed

## Example entries

| ID | Risk | Category | Prob. | Impact | Score | Response | Mitigation / contingency | Owner | Status |
|---|---|---|---|---|---|---|---|---|---|
| R1 | Requirements keep changing mid-sprint → stories are reworked → sprint goal missed | Scope | 3 | 3 | 9 🔴 | Mitigate | Enforce Definition of Ready, freeze sprint scope, route new asks to backlog | Project manager | Mitigating |
| R2 | Only one developer knows the payments module → they are unavailable → release blocked | Resource | 2 | 4 | 8 🟡 | Mitigate | Pair on the next two stories, document the module, cross-train a second developer | Tech lead | Open |
| R3 | Third-party API changes without notice → integration breaks → feature fails in production | Dependency | 2 | 3 | 6 🟡 | Mitigate | Add integration monitoring and alerts, agree a change notification channel with the vendor | Backend lead | Open |
| R4 | Releases bundle too many changes → a bug appears → hard to find cause, rollback needed | Delivery | 3 | 3 | 9 🔴 | Mitigate | Smaller, more frequent releases, mandatory release checklist and rollback plan | Release owner | Mitigating |

## Common risk categories

Scope · Schedule · Resource · Technical · Dependency · Quality · Security · Stakeholder · Budget

## Writing a good risk

Use the pattern **cause → event → effect**.

- Weak: "Testing might be a problem."
- Strong: "QA has no staging data for the new module → tests cannot cover key scenarios → defects escape to production."

## Habits that keep the register useful

- Keep it short. If it has 40 open risks, nobody reads it.
- Every risk has **one** named owner, not a team.
- Close risks explicitly when they are resolved or realised.
- When a risk becomes real, convert it to an issue and log lessons in the retro.
