# KB: Clear stuck print queue (client/server)

**Related Ticket(s):** /tickets/cannot-print-to-shared-printer.md  
**Related Lab(s):** /labs/print-queue-stuck.md  
**Related Scenario:** /scenarios/printer-queue-clearing.md  
**Category:** Hardware  
**Environment:** Windows clients; server-hosted printer (e.g., HP LaserJet series)

**Owner:** TBD  
**Last Reviewed:** 2025-09-28  
**Next Review Due:** 2026-03-28

## Resolution Steps
 
1. Confirm scope: multiple users affected implies server-side issue.  
2. On server: open Print Management; check the queue; cancel the oldest/large stuck job.  
3. Restart the Print Spooler service (Services.msc or `net stop spooler` / `net start spooler`).  
4. On a client: clear local queue if needed and print a test page.  
5. Verification: new test job prints; in lab, remaining job is processed and queue shows steady state.

## Troubleshooting Notes
 
- Ensure correct driver model on server (Type 3/4) and clients.  
- Watch for mis-sized PDFs or offline ports.  
- If department-wide and persistent, check network path to printer, SNMP status, or firmware.

## Linked Incidents
 
- /tickets/cannot-print-to-shared-printer.md

## Metrics / References
 
- MTTR: TBD  
- Recurrence: TBD  
- External reference: Microsoft Docs (Print Management); Vendor printer admin guide
