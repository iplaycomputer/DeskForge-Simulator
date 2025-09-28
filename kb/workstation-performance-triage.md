# KB: Workstation performance triage (CPU/Disk/Network)

**Related Ticket(s):** /tickets/computer-running-slow-lagging.md  
**Related Lab(s):** /labs/resource-spike-triage.md  
**Related Scenario:** /scenarios/workstation-performance-triage.md  
**Category:** Hardware  
**Environment:** Windows 10/11; corporate network

**Owner:** TBD  
**Last Reviewed:** 2025-09-28  
**Next Review Due:** 2026-03-28

## Resolution Steps
1. Differentiate network vs local: ping internal resource vs external site.  
2. Check Task Manager for CPU/RAM/Disk spikes; identify culprit process.  
3. Remediate: stop runaway task; reschedule AV scans/OneDrive sync; check Windows Update.  
4. Disk health: check SMART, consider SSD upgrade if HDD and recurring.  
5. Verification: CPU/Disk usage normalizes; common actions (open browser/drive) are fast; in lab, top shows normal usage.

## Troubleshooting Notes
- If only company site is slow, escalate to web/app owners.  
- Confirm no VPN tunnel conflicts or DNS issues.  
- Capture before/after metrics if possible for MTTR.

## Linked Incidents
- /tickets/computer-running-slow-lagging.md

## Metrics / References
- MTTR: TBD  
- Recurrence: TBD  
- External reference: Microsoft Docs (Performance troubleshooting), vendor AV scheduling docs
