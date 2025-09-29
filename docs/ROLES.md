# Roles and Escalation

Keep contributions simple and consistent. Use these lightweight roles and tiers to signal ownership and when to escalate.

## Project Roles

- Contributor: Anyone adding or improving tickets, KBs, labs, or scenarios.
- Reviewer: Anyone giving peer feedback in Discussions or PRs.
- Maintainer: Approves PRs, curates templates, and organizes Discussions categories.

Tip: In KBs and Labs, use metadata fields like Owner, Last Reviewed, Next Review Due to show stewardship.

## Support Tiers (Scope and Actions)

- Tier 1 (Frontline)
  - Scope: Single-user issues, basic checks, standard fixes.
  - Typical actions: Verify problem, collect environment, reproduce, apply known fixes.
  - Timebox: 10–20 minutes before escalating.
- Tier 2 (Specialist)
  - Scope: Drivers, services, complex app configs, small network issues.
  - Typical actions: Logs review, driver/config changes, targeted scripts.
- Tier 3 (Deep)
  - Scope: OS-level faults, hardware failures, infrastructure dependencies.
  - Typical actions: Advanced diagnostics, vendor docs, replacement decisions.

## Escalation Signals

- Safety or data risk detected.
- Permissions or tooling required beyond your access.
- Timebox exceeded with no progress.
- Systemic/recurring incident (affects multiple users).

## How To Mark Tiers in Tickets

Include this block (edit as you go):

```markdown
## Escalation Path:
- [x] Tier 1 complete (basic troubleshooting done)
- [ ] Escalated to Tier 2 (e.g., driver or service-level change)
- [ ] Escalated to Tier 3 (e.g., OS/hardware/vendor)
```

## KB/Lab Ownership Example

Add to the metadata block:

```markdown
**Owner:** @your-handle
**Last Reviewed:** 2025-09-26
**Next Review Due:** 2026-03-26
```
