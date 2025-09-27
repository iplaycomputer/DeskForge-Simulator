# Helpdesk Metrics (Lightweight)

Use simple, repeatable fields so contributors can track quality without heavy tooling. Add these to Tickets and KBs when helpful.

## Ticket Metrics
- Reported: YYYY-MM-DD
- Resolved: YYYY-MM-DD (or TBD)
- MTTR (mins): (Resolved - Reported)
- Recurrence: Yes/No (seen before?)
- Affected Users: 1 | few | many

Example block for tickets:
```markdown
**Metrics:**  
- Reported: 2025-09-26  
- Resolved: 2025-09-26  
- MTTR (mins): 12  
- Recurrence: No  
- Affected Users: 1  
```

## KB Metrics
- Verification Date: YYYY-MM-DD
- Verified By: @handle
- Validated Against: OS/App version(s)
- Recurrence Notes: When to apply or retire

Example block for KBs:
```markdown
**Metrics / Verification:**  
- Verification Date: 2025-09-26  
- Verified By: @your-handle  
- Validated Against: Windows 11 23H2, HP LaserJet Pro  
- Recurrence Notes: Common after major Windows updates  
```

## When To Track
- New incident patterns emerge (multiple similar tickets)
- Longer-than-expected MTTR
- Playbooks or KBs need periodic review windows

## Keep It Practical
- No dashboards required—just fill fields in Markdown.
- Prefer consistency over precision.
