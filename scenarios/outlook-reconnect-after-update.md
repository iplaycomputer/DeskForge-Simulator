# Scenario: Outlook reconnect after update

- Related Ticket: /tickets/outlook-disconnected-password-prompts.md
- Related KB: /kb/outlook-reconnect-after-update.md#resolution-steps
- Related Lab: /labs/mailhog-connectivity.md#verification

## Flow

1. Validate credentials on another system; check VPN if remote.
2. Confirm connectivity; recreate profile or clear cached credentials as needed.
3. In lab, use MailHog to verify SMTP is reachable and a test message is captured.

## Success Criteria

- MailHog shows the test message; service reachable.
- Ticket notes profile/cache actions; KB drafted with steps.
