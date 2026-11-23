---
name: project-docs
description: Write, review, and maintain project documentation (README, PRD, architecture, design, ADRs, security, testing, delivery, and workflow documents) following a one-owner-per-topic structure. Use when the user asks to create, update, organize, or audit project docs, decision records, specs, plans, or runbooks, or mentions a docs folder, README, or documentation set.
---

# Project Docs

Use this skill to create and maintain a project's Markdown documentation so that each document has one clear purpose and no document repeats another.

## Core rules

1. **One owner per topic.** Every fact lives in exactly one document. Other documents link to it.
2. **Link, don't restate.** If another document already covers a topic, write a short summary and a link.
3. **Record disagreements, don't hide them.** If two documents conflict, name the governing document and add the conflict to `open-decisions.md`.
4. **Stable identifiers.** Give requirements, decisions, stories, and test cases permanent IDs. Never renumber or reuse one.
5. **Separate specification, rules, and status.** What to build goes in specs. How to work goes in rules. Progress goes in plans and status files.
6. **Gaps over guesses.** If the source material does not answer a question, write it as an open item. Do not invent content.
7. **No secrets or personal data.** Strip credentials, private names, and real user data before writing.

## Workflow

1. Ask which document type is needed, unless it is obvious from the request.
2. Check whether a document on that topic already exists. If so, update it instead of creating a new one.
3. Identify the governing document for that topic and link to it.
4. Write the document using the structure for its type (see below).
5. Check for broken links, duplicate IDs, and content that repeats another document.
6. Report what was created or changed, and list any open questions.

## Document types

- **README**: what the project is, how to run it, and where the other docs live.
- **Decision record (ADR)**: context, decision, consequences. Append-only. Superseded decisions are marked, not edited.
- **Requirement**: stable ID, statement, rationale, and who decided it.
- **User story**: story, acceptance criteria, and linked requirement IDs.
- **High-level or low-level design**: components, flows, failure modes, and how the design is verified.
- **Security checklist or threat model entry**: asset, actor, threat, mitigation, and status.
- **Test strategy or test case**: scope, level, input, expected result, and linked requirement.
- **Runbook**: symptom, diagnosis steps, recovery steps, and escalation contact role (not a personal name).
- **Changelog entry**: date, version, and what changed for users.
- **Open item (decision, gap, risk, or assumption)**: ID, description, owner role, and status. Closed items move to a dated history record.

## Output format

- Use headings, tables, and short lists where they aid scanning. Prefer prose for explanations.
- Keep each document focused. If a document covers two topics, split it.
- Use the project's exact domain terms. If a term is not defined, add it to the glossary or raise it as a gap.

## Checks before finishing

- Every link resolves to an existing file.
- No ID appears twice.
- No document restates content owned by another document.
- Open items are listed, not silently assumed.