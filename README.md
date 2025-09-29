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

**DeskForge-Simulator** is an open-source project that recreates the experience of working on a real IT helpdesk — but in a safe, collaborative learning environment.  

It’s designed for **beginners exploring IT support** as well as **experienced contributors who want to practice professional workflows**. By contributing, you’ll gain hands-on experience with the same skills used in real service desk roles:  

- 🎫 **Submitting and triaging tickets** — learn to capture user issues, categorize problems, and document troubleshooting steps.  
- 📚 **Writing and refining knowledge base (KB) articles** — transform solved tickets into reusable documentation that helps prevent repeat issues.  
- 🧪 **Building troubleshooting labs** — create interactive exercises that let others practice resolving common IT incidents.  
- 🌐 **Practicing escalation paths and IT workflows** — follow industry-standard processes like the CompTIA A+ six-step troubleshooting model and learn when to escalate issues.  

💡 Think of it as a **helpdesk-in-a-repo**: instead of just reading about IT support, you actively practice it — using tickets, KBs, and labs that mirror real-world scenarios.  

Whether you’re completely new to IT, sharpening your troubleshooting skills, or mentoring others, DeskForge-Simulator gives you a structured, low-stakes environment to learn, contribute, and grow.  

⭐ If you find **DeskForge-Simulator** useful, please give this project a **star** on GitHub — it helps the community grow and keeps the project alive!

## 🔰 Quick Start: Contribute in 5 Minutes

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

4. **Open a Pull Request** to share your contribution! 🎉

👉 That’s it — you’ve added your first simulated helpdesk ticket.  
Check out `CONTRIBUTING.md` if you want to go deeper (KB articles, labs, scenarios).

### **Note on Real Troubleshooting**

You’re welcome to post **real tech support questions** (e.g., “my printer won’t connect” or “Windows update keeps failing”) in GitHub Discussions.  
*This community will treat them as learning scenarios.*  

However:  

- This project is for **education only** — responses are not official IT support. This means no guarantees of fixes and we are not responsible for people's devices.
- Please **do not share sensitive information** (personal IPs, passwords, or private configs).  
- Use advice at your own discretion.  

Think of it as a safe space to learn troubleshooting together, not a replacement for your workplace or vendor IT support.  

## 🚀 Documentation & osTicket

- Follow [lamp-osticket-setup.md](docs/lamp-osticket-setup.md) to set up an optional **local osTicket instance** on Ubuntu 24.04 (for realism).  
- Or start contributing right away using **GitHub Discussions** and Markdown files in `/tickets/`, `/kb/`, and `/labs/`.  
- See the [CONTRIBUTING.md](CONTRIBUTING.md) guide for templates and workflow details.  
- For end-to-end flows, see the `/scenarios/` folder and use the template at `/scenarios/000.scenario-template.md`.
- Browse available labs in the [Labs Catalog](labs/README.md).
- Explore folder guides: [Tickets](tickets/README.md) · [KB](kb/README.md) · [Scenarios](scenarios/README.md)

## ❤️ Community & Contributions  

DeskForge-Simulator is **community-driven**. We welcome:  

- 🐞 Bug reports and fixes  
- ✨ New tickets, KB articles, and labs  
- 📖 Documentation improvements  
- 💡 Ideas for scenarios or learning modules  

Check out the [CONTRIBUTING.md](CONTRIBUTING.md) guide and join the conversation in [GitHub Discussions](https://github.com/iplaycomputer/DeskForge-Simulator/discussions).  

## 📫 Questions & Support  

Use [GitHub Discussions](https://github.com/iplaycomputer/DeskForge-Simulator/discussions) to:  

- Post tickets (simulated issues)  
- Draft KB articles  
- Share lab walkthroughs  
- Ask general IT or project-related questions  


## 🤝 Found a Bug? Missing a Feature?  

- File issues here: [DeskForge-Simulator Issues](https://github.com/iplaycomputer/DeskForge-Simulator/issues)  
- Open a pull request if you’ve already got a fix or draft  
- See [CONTRIBUTING.md](CONTRIBUTING.md) for coding/writing standards  


## ✅ Requirements  

- GitHub account (to contribute)  
- Text editor (for Markdown tickets, KBs, labs)  
- Optional:  
  - Ubuntu 24.04 VM (via VirtualBox or Docker)  
  - osTicket v1.18.1 (local deployment) for testing tickets & KB workflows  
