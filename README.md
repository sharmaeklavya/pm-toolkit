<h1 align="center">🧰 PM Toolkit</h1>

<p align="center">
  <b>Reusable delivery templates for engineering teams.</b><br/>
  Release governance · Code review discipline · Agile ceremonies · Jira workflows
</p>

<p align="center">
  <img src="https://img.shields.io/badge/Agile-Scrum-00F5FF?style=for-the-badge&labelColor=0f0c29"/>
  <img src="https://img.shields.io/badge/Format-Markdown-302b63?style=for-the-badge"/>
  <img src="https://img.shields.io/badge/License-MIT-0f0c29?style=for-the-badge"/>
</p>

---

## Why this exists

Predictable delivery does not come from tools. It comes from small, consistent habits: tickets that are clear before work starts, pull requests that are easy to review, releases that follow a checklist, and retros that produce actions.

This toolkit collects the templates I use to run delivery for cross-functional software teams. Copy them, adapt them to your team, and keep what works.

## What's inside

| File | Use it when |
|---|---|
| [`.github/PULL_REQUEST_TEMPLATE.md`](.github/PULL_REQUEST_TEMPLATE.md) | Every pull request. GitHub applies it automatically when placed in this folder |
| [`templates/release-checklist.md`](templates/release-checklist.md) | Before, during and after each production release |
| [`templates/sprint-retrospective.md`](templates/sprint-retrospective.md) | Running a sprint retro that ends with owned actions |
| [`templates/user-story-template.md`](templates/user-story-template.md) | Writing stories with clear acceptance criteria |
| [`templates/risk-register.md`](templates/risk-register.md) | Tracking delivery risks and mitigations |
| [`guides/jira-workflow-guide.md`](guides/jira-workflow-guide.md) | Setting up or cleaning up a Jira workflow and ticket hygiene |

## How to use

1. Copy the file you need into your own repo, wiki or Confluence space.
2. Replace anything in `[square brackets]` with your team's details.
3. Delete sections that don't fit. A short checklist that gets used beats a long one that doesn't.
4. Review it every few sprints and adjust based on what your retros tell you.

## Principles behind the templates

- **Clear before started:** work is only pulled into a sprint when it is ready.
- **Small and reviewable:** small pull requests get reviewed faster and break less.
- **Every ticket traceable:** ticket, branch, commit, pull request and release notes all share the same key.
- **Releases are boring:** a repeatable checklist and a rollback plan make releases routine.
- **Retros end in actions:** every action has an owner and a date.

## Metrics worth tracking

| Metric | What it tells you |
|---|---|
| Release frequency | How often value reaches users |
| Rollback rate | Release quality and review discipline |
| Cycle time | How long work takes from start to done |
| Sprint predictability | Committed vs delivered scope |
| Escaped defects | Bugs found in production vs before |

## Author

**Eklavya Sharma**, Technology Project Manager and Full Stack Developer, CSM®
[LinkedIn](https://www.linkedin.com/in/eklavyajs/) · [GitHub](https://github.com/sharmaeklavya)

## Contributing

Suggestions and improvements are welcome. Open an issue or a pull request.

## License

MIT. Use these freely.
