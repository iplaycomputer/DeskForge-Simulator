# Copilot Instructions for DeskForge-Simulator

This repo simulates real helpdesk workflows using Markdown contributions. Agents should prioritize clarity, reproducibility, and alignment with the troubleshooting standards in `CONTRIBUTING.md`.

## Big Picture
- Four modules map to real workflows:
  - Tickets (`/tickets/`): user-reported issues
  - Knowledge Base (`/kb/`): solution docs derived from tickets
  - Labs (`/labs/`): hands-on practice exercises
  - Scenarios (`/scenarios/`): end-to-end flows linking ticket → KB → lab
- Use templates in each folder (`000.*-template.md`).

## Key Files
- `CONTRIBUTING.md`: Primary standards, workflows, and references (CompTIA A+ model, escalation, templates).
- `docs/lamp-osticket-setup.md`: Optional local osTicket setup to test tickets/KBs.
- `docs/ROLES.md`: Lightweight tiers, escalation cues, and ownership metadata.
- `docs/METRICS.md`: Simple fields for MTTR, recurrence, and verification.
- `README.md`: Project overview and contribution on-ramp.

## Authoring Patterns
- Follow CompTIA A+ 6-step model: Identify → Theory → Test → Plan/Implement → Verify → Document.
- Keep language plain and steps reproducible. Include environment details (OS/version), verification, and escalation path.
- Link artifacts with relative paths (e.g., `/tickets/printer-failure.md` in KB/Lab/Scenario).
- Use checklists for Tier 1/2/3 completion; mark what you actually did.

## Workflows
- Propose in Discussions: draft tickets/KBs/labs in appropriate categories.
- Land changes via PRs adding Markdown under `/tickets`, `/kb`, `/labs`, `/scenarios`.
- Labs should be verifiable on a Linux VM or container; osTicket is optional.

## Examples from Repo
- Templates: `kb/000.kb-template.md`, `labs/000.lab-template.md`, `tickets/000.ticket-template.md`, `scenarios/000.scenario-template.md`.
- osTicket URLs referenced use `http://<vm-ip>/osticket/` and `.../scp` for staff; replace `<vm-ip>` locally and do not share it publicly.

## Conventions
- Filenames: use kebab-case, concise, and descriptive (e.g., `printer-spooler-restart.md`).
- Metadata blocks: include Category, Environment, Owner, Reviewed dates when applicable.
- References: cite external docs in a final section; prefer vendor support links.

## What NOT to do
- Don’t invent infrastructure or public endpoints; this repo is markdown-only.
- Don’t add personal IPs or credentials.

---
Clarifications welcome: if any folder structure or template changes, update this file to match.
