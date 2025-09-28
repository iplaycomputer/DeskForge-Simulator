# Scenario: Account lockout and password reset

- Related Ticket: /tickets/account-locked-out.md
- Related KB: /kb/account-lockout-reset.md#resolution-steps
- Related Lab: /labs/htpasswd-auth-reset.md#verification

## Flow
1. User reports lockout; verify identity and account status.
2. Reset password; instruct user to retry on wired login.
3. In lab, reset htpasswd password and verify 200 OK with Basic Auth header.

## Success Criteria
- Access restored in lab (HTTP 200) and, in real workflow, user confirms workstation login.
- Ticket updated with steps, and (when created) KB drafted referencing the lab.
