## Summary

Briefly describe what this PR adds or changes.

## Linked Artifacts (relative paths)

- Ticket(s): /tickets/[file].md
- KB: /kb/[file].md
- Lab: /labs/[file].md (optional)
- Scenario: /scenarios/[file].md (optional)

## Checklists

- Content
  - [ ] Uses the correct template (copied from 000.*-template.md)
  - [ ] Clear, reproducible steps and plain language
  - [ ] Relative links resolve inside the repo
  - [ ] Avoid duplication across modules (KB = productized steps; Lab = full commands + Verification; Scenario = flow/success, links only)
  - [ ] Deep link to sections where applicable (KB → #resolution-steps, Lab → #verification)
- Metadata
  - [ ] Owner set; Last Reviewed and Next Review Due (KB/Lab)
  - [ ] Escalation Path filled (Ticket)
  - [ ] Metrics block added if useful (see docs/METRICS.md)
- Quality
  - [ ] Verification steps included (expected outputs / pass-fail)
  - [ ] Anchors exist and resolve (KB “Resolution Steps”, Lab “Verification”)
  - [ ] Scenario (if present) ties Ticket → KB → Lab and defines success criteria

### Labs (if included)

- [ ] Dedicated “Verification” section with expected outputs
- [ ] Images pinned if using containers; HTTP services include a simple healthcheck when applicable
- [ ] Assets stored under `labs/<lab>/assets/`

### KBs (if included)

- [ ] Brief (1–2 lines) verification; link to related Lab for full commands

### Scenarios (if included)

- [ ] Uses deep links to KB “Resolution Steps” and Lab “Verification” (no step duplication)

## Notes

Add screenshots, logs, or context as needed.

## How to Verify (for reviewers)

- Click Related KB/Lab links and confirm they jump to the correct anchors.
- If a Lab changed, run the Verification steps and confirm expected outputs.
- Check that no personal IPs or credentials are included; use `<vm-ip>` placeholders.

