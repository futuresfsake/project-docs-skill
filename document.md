# Project Documentation Guide (v2)

This guide maps the documentation set you have actually written. Purposes are inferred from file names only, so check each description against the file's contents and correct any that are wrong. Folder names for some groups are not visible in the screenshots, so the groups below follow apparent purpose.

## 1. Vision and Planning

| File | Apparent purpose |
|---|---|
| `README.md` | Entry point for this area: what the project is and where to start |
| `vision.md` | Why the product exists and where it is going |
| `limits-and-roadmap.md` | What the project will not do, and what comes next |
| `open-decisions.md` | Decisions still pending |
| `decision-log.md` | Record of decisions already made, with dates |
| `features.md` | Feature list |
| `milestones.md` | Milestones and what each one delivers |
| `user-stories.md` | Stories written from the user's point of view |
| `slash-commands.md` | Commands the product or tooling exposes to users or agents |

## 2. Architecture and Design

| File | Apparent purpose |
|---|---|
| `README.md` | Index of the architecture area |
| `high-level-design.md` | System components, stack, and key flows |
| `low-level-design.md` | Detailed internal design of components |
| `api-versioning.md` | How the API changes over time without breaking clients |
| `asyncapi.yaml` | Machine-readable spec for event-driven or asynchronous messages |
| `validation-zod.md` | How input is validated, using the Zod library |
| `matchmaking.md` | Design of the matching feature |
| `adr/` (folder) | Architecture decision records, one numbered file per decision |

## 3. Security, Privacy, and Safety

| File | Apparent purpose |
|---|---|
| `README.md` | Index of the security area |
| `security-overview.md` | Summary of security approach |
| `security-checklist.md` | Checks to run before a change is merged or released |
| `threat-model.md` | Assets, attackers, threats, and mitigations |
| `authentication-authorization.md` | Who users are and what they may do |
| `e2ee.md` | End-to-end encryption design |
| `privacy-and-sessions.md` | Handling of personal data and user sessions |
| `trust-and-safety.md` | Protection of users from abuse and harmful content |

## 4. Testing

| File | Apparent purpose |
|---|---|
| `README.md` | Index of the testing area |
| `testing-strategy.md` | What gets tested, at which levels, and why |
| `testing-requirements.md` | Coverage and quality targets that testing must meet |
| `tdd/` (folder) | Test-driven development material, such as test designs or examples |

## 5. Delivery and Automation

| File | Apparent purpose |
|---|---|
| `README.md` | Index of the delivery area |
| `ci-cd.md` | Continuous integration and deployment setup |
| `automation.md` | Automated tasks and scripts |
| `workflows.md` | Automated workflow definitions (for example, GitHub Actions) |
| `security-tooling.md` | Security scanners and checks run in automation |
| `pipeline/` (folder) | Pipeline definitions or stage-by-stage configuration |
| `templates/` (folder) | Reusable templates, such as for issues, pull requests, or documents |

## 6. Process and Workflow

| File | Apparent purpose |
|---|---|
| `README.md` | Index of the process area |
| `workflow.md` | The overall development workflow |
| `story-lifecycle.md` | Stages a story passes through, from idea to done |
| `story-classification.md` | How stories are sized, typed, or prioritized |
| `definition-of-ready.md` | Conditions a story must meet before work starts |
| `definition-of-done.md` | Conditions a story must meet before it is complete |
| `merge-strategy.md` | How branches are merged |
| `commit-audit.md` | Rules and checks for commit history |
| `milestone-pipeline.md` | Steps for taking a milestone from plan to release |
| `hotfix-pipeline.md` | Fast path for urgent production fixes |
| `skill-plan.md` | Skills or capabilities the team needs and how to build them |
| `agent-definitions.md` | Roles and responsibilities of AI agents or automated actors |

## 7. Development and Demo

| File | Apparent purpose |
|---|---|
| `README.md` | Index of this area |
| `local-development.md` | How to set up and run the project on your machine |
| `demo.md` | How to run a demonstration of the product |

## Overlaps to Resolve

Each overlap below should have one governing document, and the others should link to it.

- **`workflow.md` and `workflows.md`:** the names differ by one letter, which is easy to confuse. One covers the human process and the other covers automation. Rename one to make the difference obvious, such as `dev-workflow.md` and `ci-workflows.md`.
- **`decision-log.md`, `open-decisions.md`, and `adr/`:** three places hold decisions. Use `adr/` for significant architectural decisions, `decision-log.md` for dated history, and `open-decisions.md` for pending items. Make sure a decision is never recorded as both open and closed.
- **`security-overview.md`, `security-checklist.md`, and `threat-model.md`:** the overview should link to the other two rather than restate them.
- **`testing-strategy.md` and `testing-requirements.md`:** strategy describes the approach, and requirements describe the targets. Keep the numbers in requirements only.
- **`ci-cd.md`, `workflows.md`, `pipeline/`, `milestone-pipeline.md`, and `hotfix-pipeline.md`:** five files describe delivery. Decide which one defines the normal release path, and make the milestone and hotfix files describe only their differences from it.
- **`high-level-design.md` and `low-level-design.md`:** check that each stays at its own level of detail.
- **`features.md`, `user-stories.md`, and `milestones.md`:** a feature should appear in one place as its definition, with stories and milestones linking to it.
- **README files:** every folder has one, which is good. Each should only index its folder, never repeat its contents.

## Gaps Worth Filling

- **`CONTRIBUTING.md`:** `local-development.md` covers setup, but contributors also need the rules for submitting work. Your `rules.md`-style content may cover this, so check before adding a new file.
- **`CHANGELOG.md`:** a record of what each release changed.
- **`requirements.md` with stable IDs:** if `user-stories.md` is where scope lives, give each story a permanent ID so other documents can cite it.
- **`schema.md` or a data model section:** the data structures should be documented somewhere. If they are inside `high-level-design.md` or `low-level-design.md`, link to them from a short index.
- **`runbook.md`:** what to do when production breaks. `hotfix-pipeline.md` covers part of this, but a runbook covers diagnosis and recovery too.
- **Glossary:** a single list of domain terms, so every document uses the same words.

## Suggested Precedence Rules

When two documents disagree, one must win. A reasonable default:

1. Decisions recorded in `adr/` override everything else on architecture.
2. `threat-model.md` and `security-checklist.md` override informal guidance on security.
3. `definition-of-done.md` decides whether a story is complete, regardless of what a plan says.
4. Record any disagreement in `open-decisions.md` instead of quietly choosing one side.

## Key Takeaways

- Your set already covers most areas a software project needs: vision, architecture, security, testing, delivery, and process.
- The main risks are overlap and near-identical names, not missing content.
- Each folder's README should index that folder, and each topic should have one owner.

## Common Mistakes

- Two files with similar names that readers confuse, such as `workflow.md` and `workflows.md`.
- Recording the same decision in several places, which lets them drift apart.
- Writing a document once and never updating it. Each file needs an owner who keeps it current.

## What a Senior Engineer Would Think About

A senior engineer would open this set as a new teammate and ask: where do I start, and can I find the answer to my question in one place? The current structure is strong. The next step is to make each document declare what it owns, link to the others instead of repeating them, and remove or merge any document no one updates.