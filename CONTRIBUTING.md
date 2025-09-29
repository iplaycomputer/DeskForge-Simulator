# Contributing to DeskForge-Simulator (Beginner-Friendly Guide)

Welcome to **DeskForge-Simulator**! This project simulates real-world helpdesk workflows, guiding you through creating tickets, troubleshooting issues, writing knowledge base (KB) articles, and building labs. Whether you’re new to IT or an experienced pro, we’re excited to have you contribute!

This guide provides **guidelines** (not strict rules) for contributing to DeskForge-Simulator. Use your best judgment and suggest improvements via pull requests.

**Note**: Setting up a local osTicket instance is **optional** but recommended to learn how ticketing systems work in real-world IT jobs (see [lamp-osticket-setup.md](docs/lamp-osticket-setup.md)). You can contribute by writing Markdown files directly or sharing real-world tech support issues, KB drafts, or labs via GitHub Discussions.

## What You’ll Need

- A GitHub account to submit contributions (sign up at [github.com](https://github.com)).
- A text editor for writing Markdown files in `/tickets/`, `/kb/`, and `/labs/` (we provide templates!).

- **Optional**: A local osTicket setup to test tickets and KB articles (see [lamp-osticket-setup.md](docs/lamp-osticket-setup.md) for installing osTicket v1.18.1 in a VirtualBox VM with Ubuntu 24.04 Desktop; client portal at `http://<vm-ip>/osticket/`, admin/staff panel at `http://<vm-ip>/osticket/scp`). Replace `<vm-ip>` with your VM’s IP (use `ip addr show` in the terminal). Keep this private—do not share personal IPs in public contributions.

- For labs: A lightweight Linux VM or sandbox (e.g., Ubuntu 24.04 Desktop or Docker container) to test troubleshooting steps, which can be the same VM as osTicket or a separate one.
- Curiosity and a willingness to learn—no IT expertise required!

## Contribution Workflow

To keep contributions organized, use the following channels:

- **GitHub Discussions ([https://github.com/iplaycomputer/DeskForge-Simulator/discussions](https://github.com/iplaycomputer/DeskForge-Simulator/discussions))**:
  - **Tickets**: Share real-world tech support issues, fictional scenarios, or training exercises in the `Tickets` category. Convert these into Markdown files for `/tickets/`.
  - **Knowledge Base**: Share KB drafts or solution ideas in the `Knowledge Base` category. Convert these into Markdown files for `/kb/`.
  - **Labs**: Share lab ideas or troubleshooting exercises in the `Labs` category. Convert these into Markdown files for `/labs/`.
  - **Scenarios & General**: Discuss end-to-end workflows (Ticket → KB → Lab) or general Q&A in the `Scenarios & General` category.
- **GitHub Issues ([https://github.com/iplaycomputer/DeskForge-Simulator/issues](https://github.com/iplaycomputer/DeskForge-Simulator/issues))**:
  - Report project-related problems (e.g., bugs, broken setup instructions in `lamp-osticket-setup.md`, missing dependencies).
- **Pull Requests**: Submit your final Markdown files (`/tickets/`, `/kb/`, `/labs/`, `/scenarios/`) as pull requests for review.

**For Maintainers**: Ensure Discussions has the categories: `Announcements`, `Tickets`, `Knowledge Base`, `Labs`, `Scenarios & General`, and `Polls`. Use `Announcements` for updates and `Polls` for community input.

This keeps Discussions for collaboration and learning, Issues for project fixes, and the repo clean with structured contributions.

## What This Guide Does

This guide will help you:

- Write tickets, KB articles, and labs in Markdown for the DeskForge-Simulator repo.
- Share tickets, KB drafts, or labs via GitHub Discussions or test them in a local osTicket instance.
- Test labs in a Linux VM or sandbox environment without needing osTicket.
- Follow a professional troubleshooting approach based on industry standards.
- Use community resources to ask questions and get help.

## Table of Contents

1. [Code of Conduct](#code-of-conduct)
2. [I Have a Question!](#i-have-a-question)
3. [Troubleshooting Philosophy](#troubleshooting-philosophy)
4. [What Should I Know Before I Get Started?](#what-should-i-know-before-i-get-started)
5. [DeskForge Modules](#deskforge-modules)
6. [How Can I Contribute?](#how-can-i-contribute)
   - [Submitting Tickets](#submitting-tickets)
   - [Creating KB Articles](#creating-kb-articles)
   - [Creating Labs](#creating-labs)
   - [Creating Scenarios](#creating-scenarios)
7. [Roadmap Note](#roadmap-note)

## Code of Conduct

We want DeskForge-Simulator to be a welcoming, respectful, and professional community. By contributing, you agree to follow the **DeskForge Code of Conduct**, which emphasizes:

- Respectful communication.
- Collaboration and inclusivity.
- Professional behavior.

If you encounter unacceptable behavior, report it via GitHub issues or by contacting the maintainers directly.

## I Have a Question

Don’t file a GitHub issue for general questions—you’ll get faster answers in the `Scenarios & General` category of [GitHub Discussions](https://github.com/iplaycomputer/DeskForge-Simulator/discussions). Other resources:

- **[r/helpdesk on Reddit](https://reddit.com/r/helpdesk)**: Share and learn from real-world troubleshooting stories.
- **[Spiceworks Community](https://community.spiceworks.com/)**: Connect with IT pros for tips and best practices.
- **[Microsoft TechNet Forums](https://docs.microsoft.com/en-us/answers/products/)**: Get help with OS, networking, or enterprise issues.
- **[Stack Overflow](https://stackoverflow.com/)**: Ask programming or script-related questions.

## Troubleshooting Philosophy

DeskForge-Simulator follows industry-standard helpdesk practices to ensure contributions are clear, professional, and useful. When writing tickets, KB articles, or labs, align with these principles:

| Principle | Description | Reference |
|-----------|-------------|-----------|
| **Clear communication** | Use simple, step-by-step instructions and plain language in tickets and KB articles. | Blokdyk, 2020 |
| **User focus & empathy** | Include technical details and the user’s experience (e.g., what they see, how it affects them). | Blokdyk, 2020; Art of Service, 2021 |
| **Structured troubleshooting** | Follow the CompTIA A+ six-step diagnostic model: <br>1. Identify the problem <br>2. Establish a theory of probable cause <br>3. Test the theory <br>4. Establish a plan and implement the solution <br>5. Verify functionality <br>6. Document findings, actions, and outcomes | O’Shea, 2025 |
| **Escalation & scope** | Know when an issue needs higher-level support and document the escalation path. | Art of Service, 2021 |
| **Consistency** | Use standard templates for tickets, KB articles, and labs to keep things uniform. | Blokdyk, 2020 |
| **Metrics & improvement** | Track resolution times and root causes to improve the helpdesk process. | Art of Service, 2021 |
| **Knowledge management** | Turn solved tickets into KB articles or labs to prevent repeat issues. | Blokdyk, 2020; Art of Service, 2021 |

### References

- *Help Desk: A Complete Guide – 2020 Edition* (Gerardus Blokdyk, ISBN 978-1867309383)
- *CompTIA A+ Complete Practice Tests, 4th Edition* (Audrey O’Shea, 2025, Print ISBN 978-1394330331; eText ISBN 978-1394330348)
- *IT Service Desk: A Complete Guide, 2021 Edition* (The Art of Service, ISBN 978-1867437223)
- [Atlassian: What Is ITIL? Best Practices for ITSM](https://www.atlassian.com/itsm)

## What Should I Know Before I Get Started?

DeskForge-Simulator mimics a real IT helpdesk, allowing you to contribute tickets, KB articles, and labs in Markdown. Testing tickets and KB articles in a local osTicket instance is optional but recommended to understand how ticketing systems work in real-world IT jobs. Here’s what you need to know:

- **GitHub Basics**: If you’re new to GitHub, check out [Contributing to a Project on GitHub](https://docs.github.com/en/get-started/exploring-projects-on-github/contributing-to-a-project) to learn about forking, branching, committing, and pull requests.
- **Helpdesk Skills**: You don’t need to be an expert! Focus on:
  - Clear communication with non-technical users.
  - Basic troubleshooting (e.g., OS, hardware, network issues).
  - Following templates and asking questions to clarify issues.
- **osTicket Setup (Optional)**: For a hands-on ticketing system experience, set up a local osTicket instance using [lamp-osticket-setup.md](docs/lamp-osticket-setup.md) (client portal at `http://<vm-ip>/osticket/`, admin/staff panel at `http://<vm-ip>/osticket/scp`). Replace `<vm-ip>` with your VM’s IP (use `ip addr show` in the terminal). Keep this private—do not share personal IPs in public contributions.
- **Lab Testing**: Test labs in a local Linux VM or sandbox (e.g., Ubuntu 24.04 Desktop or Docker container), which can be the same VM as osTicket or a separate one. osTicket is not required for labs.
- **Learning by Doing**: The best way to learn is to write tickets, test solutions, and get feedback. Start small and improve with each contribution!

## DeskForge Modules

DeskForge-Simulator is built around four modules that mirror real helpdesk workflows:

| Module | Path | Purpose |
|--------|------|---------|
| **Tickets** | `/tickets/` | User-reported issues: real incidents, training exercises, or fictional scenarios, documented in Markdown and shared via GitHub Discussions or tested in a local osTicket instance. |
| **Knowledge Base (KB)** | `/kb/` | Documentation of solutions and lessons learned, linked to tickets, written in Markdown and shared via GitHub Discussions or tested in a local osTicket instance. |
| **Labs** | `/labs/` | Hands-on troubleshooting exercises, tested in a Linux VM or sandbox, written in Markdown and shared via GitHub Discussions. |
| **Scenarios** | `/scenarios/` | End-to-end workflows combining tickets, KB articles, and labs, written in Markdown. |

Folder guides for quick navigation: [Tickets](tickets/README.md) · [KB](kb/README.md) · [Labs](labs/README.md) · [Scenarios](scenarios/README.md)

Roles (to avoid duplication):

- Labs are the canonical source of exact commands and environment setup. Always put full commands in Labs and include a small "Verification" section.
- KBs contain productized resolution steps with 1–2 verification lines (max). Link to the Lab for full commands.
- Scenarios define the flow and success criteria; they should link to specific sections in the KB (Resolution Steps) and Lab (Verification) rather than restating steps.

### How Modules Work Together

Contributions flow like this: **Ticket → Resolution → KB → Lab → Scenario**.

- **Tickets**: Share a ticket in GitHub Discussions (`Tickets` category) or write a Markdown file in `/tickets/` describing a problem (e.g., “Printer not working”).

Optionally, test it in your local osTicket instance’s client portal (`http://<vm-ip>/osticket/`). Replace `<vm-ip>` with your VM’s IP (use `ip addr show` in the terminal). Keep this private—do not share personal IPs in public contributions.

- **KB Articles**: Share a KB draft in GitHub Discussions (`Knowledge Base` category) or write a Markdown file in `/kb/` formalizing the solution (e.g., “How to restart the Print Spooler”). Optionally, test it in your local osTicket instance’s admin/staff panel (`http://<vm-ip>/osticket/scp`).
- **Labs**: Share a lab idea in GitHub Discussions (`Labs` category) or write a Markdown file in `/labs/` for a hands-on exercise, tested in a Linux VM or sandbox.

- **Scenarios**: Combine tickets, KB articles, and labs into a complete workflow in `/scenarios/`.

## How Can I Contribute?

You can contribute by writing tickets, KB articles, or labs in Markdown, sharing them via GitHub Discussions, or testing tickets/KB articles in a local osTicket instance. Below are the details for each.

### Submitting Tickets

Tickets represent user-reported problems (real, training, or fictional). You can share them in GitHub Discussions, write them directly in Markdown for `/tickets/`, or test them in a local osTicket instance for realism.

- **Option 1: GitHub Discussions**: Post a ticket in the `Tickets` category at [https://github.com/iplaycomputer/DeskForge-Simulator/discussions](https://github.com/iplaycomputer/DeskForge-Simulator/discussions) with details of a real-world tech support issue (e.g., “My laptop won’t connect to Wi-Fi”). Convert the details into the Markdown template and save in `/tickets/`.

- **Option 2: Direct Markdown**: Write a ticket in the Markdown template below and save it in `/tickets/`.

- **Option 3: Local osTicket (Recommended for Learning)**: Access your local client portal (e.g., `http://<vm-ip>/osticket/`), click “Open a New Ticket,” select a help topic (e.g., “Hardware”), and submit. Configure help topics in the admin panel (e.g., `http://<vm-ip>/osticket/scp`, Admin Panel → Manage → Help Topics). Replace `<vm-ip>` with your VM’s IP (use `ip addr show` in the terminal). Keep this private—do not share personal IPs in public contributions. Copy the ticket details into the Markdown template.

- **Example**: For a “Unable to print” issue, post in GitHub Discussions (`Tickets` category) with details, write `/tickets/printer-failure.md` directly, or test it in your local osTicket instance and document it in `/tickets/`.
- **Inspiration**: Browse existing examples in the `/tickets/` folder and the `Tickets` category in Discussions.
- **Roles**: See [docs/ROLES.md](docs/ROLES.md) for tiers and escalation patterns.
- **Metrics**: See [docs/METRICS.md](docs/METRICS.md) for lightweight fields to add to Tickets/KBs.

Template: copy `/tickets/000.ticket-template.md` to `/tickets/<your-title>.md` and fill it out.

Folder guide: see [tickets/README.md](tickets/README.md)

**Tips**:

- Use GitHub Discussions (`Tickets` category) to share real-world tech support issues you’ve encountered.
- Test tickets in your local osTicket instance (if set up) to simulate a real helpdesk.
- Follow the CompTIA A+ six-step model (see “Troubleshooting Philosophy”).
- Submit your ticket as a pull request in the `/tickets/` folder.

### Creating KB Articles

KB articles document solutions from solved tickets. Share them in GitHub Discussions (`Knowledge Base` category) or write them in Markdown for `/kb/`. Optionally, test them in your local osTicket instance’s admin/staff panel.

Template: copy `/kb/000.kb-template.md` to `/kb/<your-title>.md` and complete the fields.

Folder guide: see [kb/README.md](kb/README.md)

**Tips**:

- Share KB drafts in GitHub Discussions (`Knowledge Base` category) for feedback.
- Use your local osTicket admin/staff panel (e.g., `http://<vm-ip>/osticket/scp`) to draft KB articles, if set up. Replace `<vm-ip>` with your VM’s IP (use `ip addr show` in the terminal). Keep this private—do not share personal IPs in public contributions.
- Ensure steps are clear, reproducible, and tested.
- Keep verification concise (1–2 lines). For full commands and environment, link to the related Lab.
- Submit as a pull request in the `/kb/` folder.

### Creating Labs

Labs are standalone troubleshooting exercises in `/labs/`, tested in a Linux VM or sandbox (e.g., Ubuntu 24.04 Desktop or Docker container), not requiring osTicket. Share them in GitHub Discussions (`Labs` category) or write them in Markdown.

**Testing Labs**: Use a local Linux VM or sandbox to simulate issues (e.g., stop a service with `sudo systemctl stop <service>`). Follow [lamp-osticket-setup.md](docs/lamp-osticket-setup.md) to set up a VM, or use a Docker container for simplicity.

Template: copy `/labs/000.lab-template.md` to `/labs/<your-title>.md` and follow the structure.
**Tips**:

- Share lab ideas in GitHub Discussions (`Labs` category) for feedback.
- Test labs in a Linux VM or Docker container, not osTicket.
- Include a dedicated "Verification" section with specific commands/outputs (Labs are the source of truth for commands).
- Submit as a pull request in the `/labs/` folder.

Folder guide: see [labs/README.md](labs/README.md)

### Creating Scenarios

Scenarios stitch together one or more tickets, a KB article, and an optional lab into an end-to-end learning flow. Use them to show how a real incident moves from report → resolution → documentation → practice.

#### When to create a scenario

- You have at least one ticket and a corresponding KB article; a lab is recommended but optional.
- You want a guided narrative that learners can follow front-to-back.

#### How to author

- Start from the template at `/scenarios/000.scenario-template.md`.
- Create a new file under `/scenarios/`, e.g. `/scenarios/printer-outage-end-to-end.md`.
- Fill in:
  - Related Ticket(s): link to one or more tickets, e.g. `/tickets/printer-failure.md`.
  - Related KB: link to your KB, e.g. `/kb/printer-spooler-restart.md`.
  - Related Lab: link if you have one, e.g. `/labs/restart-print-spooler.md`.
  - Overview, Flow (Ticket → KB → Lab), Success Criteria.

#### Submission

- Open a PR with the new scenario file in `/scenarios/`.
- In your PR description, briefly summarize the learning goals and link the related ticket/KB/lab.

Folder guide: see [scenarios/README.md](scenarios/README.md)

### Tips

- Keep links relative so they work in GitHub and downstream clones.
- Be explicit about pass/fail checks so learners can self-verify.
- Prefer deep links to existing sections instead of rewriting steps, e.g.: `/kb/...#resolution-steps` and `/labs/...#verification`.

## Local Lint (Optional)

Before you commit, you can run the Markdown linter locally to catch spacing/format issues early:

- Windows PowerShell:

```powershell
npx -y markdownlint-cli2
```

Optional Git hook (runs locally, does not affect CI):

1. Create a file at `.git/hooks/pre-commit` with the following and make sure it’s executable in your Git environment:

```bash
#!/usr/bin/env bash
set -euo pipefail
npx -y markdownlint-cli2
```

1. Save. The hook will block commits that fail linting. You can always run the linter manually if you prefer.

## Roadmap Note

Public ticket submissions are not yet enabled. If a central osTicket instance is launched, it will likely allow public users to submit tickets via the client portal only, with the admin/staff panel restricted to maintainers.
