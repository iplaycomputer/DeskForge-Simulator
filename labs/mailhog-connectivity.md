# Lab: Mail connectivity sanity with MailHog

Use MailHog to practice diagnosing "client disconnected / prompting" symptoms.

**Related Ticket:** /tickets/outlook-disconnected-password-prompts.md
**Related KB:** /kb/outlook-reconnect-after-update.md
**Related Scenario:** /scenarios/outlook-reconnect-after-update.md
**Category:** Software
**Environment:** Docker Desktop (Windows/macOS) or Docker Engine (Linux)

## Objectives

- Stand up a local SMTP sink and web UI
- Simulate disconnect by stopping service / changing port
- Verify send/receive via test message

## Prerequisites

- Docker running
- PowerShell or Bash

## Steps

1) Start MailHog (from repo root)
    - PowerShell

       ```powershell
       docker compose -f .\labs\mailhog-connectivity\assets\compose.yaml up -d
       ```

    - Bash

       ```bash
       docker compose -f ./labs/mailhog-connectivity/assets/compose.yaml up -d
       ```

2) Check status

   ```powershell
   docker compose -f .\labs\mailhog-connectivity\assets\compose.yaml ps
   # UI at <http://localhost:8025>
   ```

3) Send a test message

   ```powershell
   docker exec mailhog bash -lc "echo -e 'HELO test\nMAIL FROM:<tester@example.com>\nRCPT TO:<inbox@example.com>\nDATA\nSubject: hello\n\nmailhog test\n.\nQUIT' | nc 127.0.0.1 1025"
   ```

4) Simulate disconnect and recover

   ```powershell
   docker stop mailhog
   # expect UI down; restart
   docker start mailhog
   ```

5) Verify in UI
   - Browse <http://localhost:8025> and confirm the message is present.

## Verification

```powershell
   Invoke-WebRequest http://localhost:8025 -UseBasicParsing | Select-Object -ExpandProperty StatusCode
   # Expect: 200 (and message visible in UI)
```

## Cleanup

```powershell
docker compose -f .\labs\mailhog-connectivity\assets\compose.yaml down -v
```
