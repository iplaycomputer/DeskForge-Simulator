<p align="center">
<a href="https://github.com/iplaycomputer/DeskForge-Simulator/commits/main" target="_blank">
<img src="https://img.shields.io/github/last-commit/iplaycomputer/DeskForge-Simulator" alt="Last commit">
</a>
<a href="https://github.com/iplaycomputer/DeskForge-Simulator/graphs/contributors" target="_blank">
<img src="https://img.shields.io/github/contributors/iplaycomputer/DeskForge-Simulator" alt="Contributors">
</a>
<a href="https://github.com/iplaycomputer/DeskForge-Simulator/issues" target="_blank">
<img src="https://img.shields.io/github/issues/iplaycomputer/DeskForge-Simulator" alt="Open issues">
</a>
<a href="https://github.com/iplaycomputer/DeskForge-Simulator/pulls" target="_blank">
<img src="https://img.shields.io/github/issues-pr/iplaycomputer/DeskForge-Simulator" alt="Open pull requests">
</a>
<a href="LICENSE" target="_blank">
<img src="https://img.shields.io/badge/license-%20%20GNU%20GPLv3%20-green?style=plastic" alt="License">
</a>
</p>

# DeskForge-Simulator

**DeskForge-Simulator** is an open-source project that recreates the experience of working on a real IT helpdesk â€” but in a safe, collaborative learning environment.

Itâ€™s designed for **beginners exploring IT support** as well as **experienced contributors who want to practice professional workflows**. By contributing, youâ€™ll gain hands-on experience with the same skills used in real service desk roles:

- ðŸŽ« **Submitting and triaging tickets** â€” learn to capture user issues, categorize problems, and document troubleshooting steps.
- ðŸ“š **Writing and refining knowledge base (KB) articles** â€” transform solved tickets into reusable documentation that helps prevent repeat issues.
- ðŸ§ª **Building troubleshooting labs** â€” create interactive exercises that let others practice resolving common IT incidents.
- ðŸŒ **Practicing escalation paths and IT workflows** â€” follow industry-standard processes like the CompTIA A+ six-step troubleshooting model and learn when to escalate issues.

ðŸ’¡ Think of it as a **helpdesk-in-a-repo**: instead of just reading about IT support, you actively practice it â€” using tickets, KBs, and labs that mirror real-world scenarios.

Whether youâ€™re completely new to IT, sharpening your troubleshooting skills, or mentoring others, DeskForge-Simulator gives you a structured, low-stakes environment to learn, contribute, and grow.

â­ If you find **DeskForge-Simulator** useful, please give this project a **star** on GitHub â€” it helps the community grow and keeps the project alive!

## ðŸ”° Quick Start: Contribute in 5 Minutes

1. **Fork** this repository and clone it to your machine.

   ```bash
   git clone https://github.com/<your-username>/DeskForge-Simulator.git
   cd DeskForge-Simulator
   ```

2. **Create a ticket** using the template in `/tickets/`.
   Save it as a new Markdown file, e.g.:

   ```text
   /tickets/printer-issue.md
   ```

3. **Commit and push** your changes.

   ```bash
   git add tickets/printer-issue.md
   git commit -m "Add sample printer ticket"
   git push origin main
   ```

4. **Open a Pull Request** to share your contribution! ðŸŽ‰

ðŸ‘‰ Thatâ€™s it â€” youâ€™ve added your first simulated helpdesk ticket.
Check out `CONTRIBUTING.md` if you want to go deeper (KB articles, labs, scenarios).

### **Note on Real Troubleshooting**

Youâ€™re welcome to post **real tech support questions** (e.g., â€œmy printer wonâ€™t connectâ€ or â€œWindows update keeps failingâ€) in GitHub Discussions.
*This community will treat them as learning scenarios.*

However:

- This project is for **education only** â€” responses are not official IT support. This means no guarantees of fixes and we are not responsible for people's devices.
- Please **do not share sensitive information** (personal IPs, passwords, or private configs).
- Use advice at your own discretion.

Think of it as a safe space to learn troubleshooting together, not a replacement for your workplace or vendor IT support.

## ðŸš€ Documentation & osTicket

- Follow [lamp-osticket-setup.md](docs/lamp-osticket-setup.md) to set up an optional **local osTicket instance** on Ubuntu 24.04 (for realism).
- Or start contributing right away using **GitHub Discussions** and Markdown files in `/tickets/`, `/kb/`, and `/labs/`.
- See the [CONTRIBUTING.md](CONTRIBUTING.md) guide for templates and workflow details.
- For end-to-end flows, see the `/scenarios/` folder and use the template at `/scenarios/000.scenario-template.md`.
- Browse available labs in the [Labs Catalog](labs/README.md).
- Explore folder guides: [Tickets](tickets/README.md) Â· [KB](kb/README.md) Â· [Scenarios](scenarios/README.md)

## â¤ï¸ Community & Contributions

DeskForge-Simulator is **community-driven**. We welcome:

- ðŸž Bug reports and fixes
- âœ¨ New tickets, KB articles, and labs
- ðŸ“– Documentation improvements
- ðŸ’¡ Ideas for scenarios or learning modules

Check out the [CONTRIBUTING.md](CONTRIBUTING.md) guide and join the conversation in [GitHub Discussions](https://github.com/iplaycomputer/DeskForge-Simulator/discussions).

## ðŸ“« Questions & Support

Use [GitHub Discussions](https://github.com/iplaycomputer/DeskForge-Simulator/discussions) to:

- Post tickets (simulated issues)
- Draft KB articles
- Share lab walkthroughs
- Ask general IT or project-related questions

## ðŸ¤ Found a Bug? Missing a Feature?

- File issues here: [DeskForge-Simulator Issues](https://github.com/iplaycomputer/DeskForge-Simulator/issues)
- Open a pull request if youâ€™ve already got a fix or draft
- See [CONTRIBUTING.md](CONTRIBUTING.md) for coding/writing standards

## âœ… Requirements

- GitHub account (to contribute)
- Text editor (for Markdown tickets, KBs, labs)
- Optional:
  - Ubuntu 24.04 VM (via VirtualBox or Docker)
  - osTicket v1.18.1 (local deployment) for testing tickets & KB workflows
