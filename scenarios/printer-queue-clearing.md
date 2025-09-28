# Scenario: Department-wide printer outage (queue clearing)

- Related Ticket: /tickets/cannot-print-to-shared-printer.md
- Related KB: /kb/printer-queue-clearing.md#resolution-steps
- Related Lab: /labs/print-queue-stuck.md#verification

## Flow

1. Confirm scope (multiple users); check server queue/state.
2. Clear stuck job(s); restart the service.
3. In lab, simulate stuck queue; clear oldest job; restart consumer.

## Success Criteria
 
- Queue shows processed jobs and accepts new test job.
- Ticket documents scope, remediation, and server-side action; KB drafted.
 
