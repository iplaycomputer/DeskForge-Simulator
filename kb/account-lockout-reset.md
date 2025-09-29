# KB: Account lockout reset and verification

**Related Ticket(s):** /tickets/account-locked-out.md
**Related Lab(s):** /labs/htpasswd-auth-reset.md
**Related Scenario:** /scenarios/account-lockout-reset.md
**Category:** Account
**Environment:** Windows workstation joined to Active Directory; VPN/Email access

**Owner:** TBD
**Last Reviewed:** 2025-09-28
**Next Review Due:** 2026-03-28

## Resolution Steps

1. Verify identity per policy (secondary info, manager approval if required).
2. In AD Users and Computers: check account state; unlock if locked.
3. If password expired/unknown, reset to a temporary value; require change at next logon.
4. Instruct the user to sign in on a wired network if possible; wait for policy replication if applicable.
5. Verification: user confirms workstation login; for lab parity, Basic Auth to `/secure` returns HTTP 200.

## Troubleshooting Notes

- If repeated lockouts occur, look for stale credentials on other devices (mobile email, mapped services, scheduled tasks).
- Confirm MFA/SSPR state and recent policy changes.
- Check domain controller replication or account lockout policy thresholds.
- Logs: Security Event Log (user lockout), DC lockout status.

## Linked Incidents

- /tickets/account-locked-out.md

## Metrics / References

- MTTR: TBD
- Recurrence: TBD
- External reference: Microsoft Docs (Account lockout troubleshooting)
