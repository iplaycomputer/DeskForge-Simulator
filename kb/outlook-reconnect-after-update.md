# KB: Resolve Outlook disconnect / password prompts

**Related Ticket(s):** /tickets/outlook-disconnected-password-prompts.md
**Related Lab(s):** /labs/mailhog-connectivity.md
**Related Scenario:** /scenarios/outlook-reconnect-after-update.md
**Category:** Software
**Environment:** Windows 10/11; Outlook (Microsoft 365); VPN (if remote)

**Owner:** TBD
**Last Reviewed:** 2025-09-28
**Next Review Due:** 2026-03-28

## Resolution Steps

1. Validate user credentials on another system (SSO/portal) to rule out auth failure.
2. Check VPN/Network connectivity (if remote): ensure stable connection.
3. Toggle Cached Exchange Mode (disable â†’ enable) and restart Outlook.
4. Clear Windows Credential Manager entries for Office/Outlook; restart Outlook.
5. If needed, create a new Outlook profile (Control Panel â†’ Mail â†’ Profiles).
6. Verification: Outlook shows Connected; send/receive works. In lab, MailHog captures a test message at <http://localhost:8025/>.

## Troubleshooting Notes

- After updates, Autodiscover or token cache can cause loops; clearing credentials/profile often resolves.
- If organization-wide, check Exchange/identity provider status and service health.
- Logs: Windows Event Viewer â†’ Application (Outlook), Office logs.

## Linked Incidents

- /tickets/outlook-disconnected-password-prompts.md

## Metrics / References

- MTTR: TBD
- Recurrence: TBD
- External reference: Microsoft Docs (Outlook connectivity, Autodiscover)
