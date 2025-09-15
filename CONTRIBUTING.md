# Contributing to DeskForge-Simulator

This project simulates **real help desk workflows**: tickets → troubleshooting → knowledge base (KB) → labs.  
All skill levels are welcome, whether you are just starting out or have years of IT support experience.  

The following is a set of **guidelines** for contributing to DeskForge-Simulator. These are mostly *guidelines*, not strict rules. Use your best judgment, and feel free to propose improvements through pull requests.



## Table of Contents

- [Code of Conduct](#code-of-conduct)  
- [I Have a Question!](#i-have-a-question)  
- [Troubleshooting Philosophy](#troubleshooting-philosophy)  
- [What Should I Know Before I Get Started?](#what-should-i-know-before-i-get-started)  
- [DeskForge Modules](#deskforge-modules)  
- [How Can I Contribute?](#how-can-i-contribute)  
  - [Submitting Tickets](#submitting-tickets)  
  - [Creating KB Articles](#creating-kb-articles)  




## Code of Conduct

This project and everyone participating in it is governed by the **DeskForge Code of Conduct**.  
By contributing, you agree to help create a welcoming, respectful, and professional environment.  

Please report unacceptable behavior via GitHub issues or by contacting the maintainers directly.



## I Have a Question!

Note: Please don’t file a GitHub issue just to ask a question. You’ll get faster results by using these resources:

### Community & Peer Support
- [Discussions](https://github.com/<org>/DeskForge-Simulator/discussions) – Ask project-specific questions or suggest improvements.  
- [r/helpdesk on Reddit](https://reddit.com/r/helpdesk) – Real-world troubleshooting stories and Q&A.  
- [Spiceworks Community](https://community.spiceworks.com/) – Active IT pros sharing tips and best practices.  
- [Microsoft TechNet Forums](https://docs.microsoft.com/en-us/answers/products/) – OS, networking, and enterprise troubleshooting.  
- [Stack Overflow](https://stackoverflow.com/) – For programming- or script-related questions.

## Troubleshooting Philosophy

This project follows principles drawn from established service desk guides and training resources. When writing tickets, KB articles, or labs, contributors should align with these standards:

| Principle | Description | Reference |
|-----------|-------------|-----------|
| **Clear communication** | Use precise, reproducible steps and plain language in tickets and KB articles. | Blokdyk, 2020 |
| **User focus & empathy** | Capture not only technical details but also the user’s experience and frustration. | Blokdyk, 2020; Art of Service, 2021 |
| **Structured troubleshooting** | Follow the CompTIA A+ six-step diagnostic model:<br>1. Identify the problem<br>2. Establish a theory of probable cause<br>3. Test the theory<br>4. Establish a plan and implement the solution<br>5. Verify functionality<br>6. Document findings, actions, and outcomes | O’Shea, 2025 |
| **Escalation & scope** | Recognize when an issue exceeds Tier 1 capability and document the escalation path. | Art of Service, 2021 |
| **Consistency** | Use standard templates so tickets, KB articles, and labs have a uniform style. | Blokdyk, 2020 |
| **Metrics & improvement** | Track resolution times, recurring incidents, and root causes to support service improvement. | Art of Service, 2021 |
| **Knowledge management** | Transform solved incidents into KB articles or lab exercises to prevent repeat tickets. | Blokdyk, 2020; Art of Service, 2021 |

### References
- *Help Desk: A Complete Guide – 2020 Edition* (Gerardus Blokdyk, ISBN 978-1867309383)  
- *CompTIA A+ Complete Practice Tests, 4th Edition* (Audrey O’Shea, 2025, Print ISBN 978-1394330331; eText ISBN 978-1394330348)  
- *IT Service Desk: A Complete Guide, 2021 Edition* (The Art of Service, ISBN 978-1867437223) 
- [Atlassian: What Is ITIL? Best Practices for ITSM.](https://www.atlassian.com/itsm/itil)  
  


# What Should I Know Before I Get Started?

If you’re new to contributing on GitHub, start with the official guide below. It covers forking, branching, committing, and submitting pull requests:

- [Contributing to a Project on GitHub](https://docs.github.com/en/get-started/exploring-projects-on-github/contributing-to-a-project)

Before contributing, it helps to understand both the technical and
interpersonal foundations of help desk work: strong communication, 
basic diagnostics (OS, hardware, network), the ability to prioritize, 
and a mindset for learning from each ticket.

You don’t need to be an expert to start — many top contributions come 
from ability to follow templates, ask clarifying questions, research 
solutions, and communicate clearly with non-technical users.

Expect to iterate: early tickets will teach you more than any book. 
Learning comes from hands-on troubleshooting, documenting steps, and 
reviewing feedback.

## DeskForge Modules

*DeskForge-Simulator* is modular, designed to mirror real IT service desk workflows.

### Core Modules

| Module | Path | Purpose |
|--------|------|---------|
| **Tickets** | `/tickets/` | User-reported issues: real incidents, training exercises, or fictional scenarios. |
| **Knowledge Base (KB)** | `/kb/` | Documentation of resolutions, fixes, and lessons learned. |
| **Labs** | `/labs/` | Hands-on simulations and walkthroughs for practicing troubleshooting. |
| **Scenarios** | /scenarios/      | End-to-end help desk workflows combining tickets, troubleshooting, and resolution. |

A contribution usually flows like this:  
**Ticket → Resolution → KB → Lab.**

Each module builds on the previous one:
- **Tickets** capture the problem.  
- **KB articles** formalize the solution.  
- **Labs** provide a training environment to reproduce and solve the issue.  
- **Scenarios** connect everything into a real-world workflow. 


## How Can I Contribute?

### Submitting Tickets

Tickets describe problems users face. They can be **real-world issues**, **training exercises**, or **fictional but realistic scenarios**.  

For inspiration and sample scenarios, see [COMMON_TICKET_EXAMPLES.md](COMMON_TICKET_EXAMPLES.md).  
For contributor roles, see [ROLES.md](ROLES.MD)  
For project metrics and feedback loops, see [METRICS.MD](METRICS.MD) 

Use Markdown with this template:

```markdown
# Ticket: [Short title]

**Category:** Hardware | Software | Network | Account | Other  
**Priority:** Low | Medium | High | Critical  
**Impact:** Single user | Department | Organization-wide  
**Urgency:** Low (no workflow impact) | Medium (work slowed) | High (work blocked)  

**Problem:** One-line description  
**Symptoms:** What the user sees  
**Environment:** OS / system / version  

**Troubleshooting Steps Taken:**  
- [ ] Step 1  
- [ ] Step 2  

**Resolution:**  
(If known, give steps. If unknown, write "TBD")  

**Escalation Path:**  
- [ ] Tier 1 complete  
- [ ] Escalated to Tier 2  
- [ ] Escalated to Tier 3  
```

### Creating KB Articles

Every solved ticket should ideally produce a **Knowledge Base (KB) article**.Each KB article must link to its 
originating ticket. Articles should be reviewed periodically to ensure accuracy and retired when obsolete.

```markdown 
# KB: [Short Title]

**Related Ticket(s):** /tickets/[filename].md  
**Category:** Hardware | Software | Network | Account | Other  
**Environment:** OS / system / version  

**Owner:** [Contributor name or team]  
**Last Reviewed:** [YYYY-MM-DD]  
**Next Review Due:** [YYYY-MM-DD]  

## Resolution Steps
1. [Step 1]  
2. [Step 2]  
3. [Step 3]  
4. Verification: [What success looks like]  

## Troubleshooting Notes
- [Escalation guidance]  
- [Known limitations or variations]  
- [Logs, screenshots, or command outputs to capture]  

## Linked Incidents
- /tickets/[incident1].md  
- /tickets/[incident2].md  

## Metrics / References
- Mean Time to Resolution (MTTR): [Optional note if tracked]  
- Recurrence: [Yes/No]  
- External reference: [Vendor docs, URL, or manual]
```
Contributors who create KBs are responsible for updating them if related tickets recur or environments change.

### Creating Labs  
Labs live in `/labs/` and are interactive walkthroughs of KB articles. Purpose: let contributors practice the fix in a safe, repeatable way. Labs should include checkpoints and verification steps that mirror KPIs (e.g., first-contact resolution, mean time to resolution).

**Template:**  

```markdown 
# Lab: [Short Title]  
**Related KB:** /kb/[filename].md  
**Category:** Hardware | Software | Network | Account | Other  
**Environment:** OS / version / system  

**Owner:** [Contributor name or team]  
**Last Reviewed:** [YYYY-MM-DD]  
**Next Review Due:** [YYYY-MM-DD]  

## Objectives  
- State the skill or troubleshooting goal.  
- Example: "Learn to restart and verify the Windows Print Spooler service."  

## Prerequisites  
- Required setup (VM, software, permissions, network access).  
- Accounts or credentials needed.  

## Steps  
1. Restate the KB resolution steps as explicit lab instructions.  
2. Add prompts for the learner to execute commands or verify outcomes.  
3. Use fenced code blocks for commands.

## Verification  
- Define what success looks like.  
- Example: "A test document prints without error."  
- Include acceptance criteria (pass/fail conditions).  

## Escalation Context  
- What to do if the learner cannot complete the lab (e.g., escalate to Tier 2).  

## Metrics / Feedback  
- Estimated time to complete.  
- Common errors observed.  
- Links to related incidents or scenarios.  

## Cleanup  
- Optional: steps to revert or reset the environment.  
- Return system to baseline for next learner.  
```



