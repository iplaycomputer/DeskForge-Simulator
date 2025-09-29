# Lab: Basic auth reset verification (htpasswd + Nginx)

Simulate a credential reset and prove the fix with a protected endpoint.

**Related Ticket:** /tickets/account-locked-out.md
**Related KB:** /kb/account-lockout-reset.md
**Related Scenario:** /scenarios/account-lockout-reset.md
**Category:** Account
**Environment:** Docker Desktop (Windows/macOS) or Docker Engine (Linux)

## Objectives

- Protect a page with HTTP Basic Auth
- Reset the password and verify access

## Prerequisites

- Docker running
- PowerShell or Bash

## Steps

1) Start stack (from repo root)
    - PowerShell

       ```powershell
       docker compose -f .\labs\htpasswd-auth-reset\assets\compose.yaml up -d
       ```

    - Bash

       ```bash
       docker compose -f ./labs/htpasswd-auth-reset/assets/compose.yaml up -d
       ```

2) Try accessing (expect auth required)

   ```powershell
   Invoke-WebRequest http://localhost:8090/secure -UseBasicParsing -Headers @{ Authorization = ("Basic " + [Convert]::ToBase64String([Text.Encoding]::ASCII.GetBytes("user:wrong"))) } | Select-Object -ExpandProperty StatusCode
   # Expect 401/403
   ```

3) Reset password

   ```powershell
   docker exec htpasswd sh -lc "htpasswd -b /auth/.htpasswd user newpass"
   ```

4) Verify access succeeds

   ```powershell
   $pair = "user:newpass"; $b64 = [Convert]::ToBase64String([Text.Encoding]::ASCII.GetBytes($pair));
   Invoke-WebRequest http://localhost:8090/secure -UseBasicParsing -Headers @{ Authorization = "Basic $b64" } | Select-Object -ExpandProperty StatusCode
   # Expect 200
   ```

## Verification

```powershell
$pair = "user:newpass"; $b64 = [Convert]::ToBase64String([Text.Encoding]::ASCII.GetBytes($pair));
Invoke-WebRequest http://localhost:8090/secure -UseBasicParsing -Headers @{ Authorization = "Basic $b64" } | Select-Object -ExpandProperty StatusCode
# Expect: 200
```

## Cleanup

```powershell
docker compose -f .\labs\htpasswd-auth-reset\assets\compose.yaml down -v
```
