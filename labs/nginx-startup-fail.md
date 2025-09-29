# Lab: Nginx fails to start (config error)

Make a broken web server boot again by fixing a one-word typo.

**Related KB:** /kb/nginx-config-basics.md (optional)  
**Category:** Software  
**Environment:** Docker Desktop (Windows/macOS) or Docker Engine (Linux)

**Owner:**  
**Last Reviewed:**  
**Next Review Due:**  

## Why this matters (30 seconds)

This is what real-life looks like: “my web page won’t load” and the container keeps restarting. Your job is to read the logs, spot the typo, make a tiny change, and prove the fix.

## Objectives

- Diagnose a containerized Nginx startup failure
- Fix a simple configuration error and verify success

Time: ~10–15 min  •  Difficulty: Beginner

## Prerequisites (quick preflight)

- Docker is installed and running
  - PowerShell

  ```powershell
    docker --version
    docker compose version
    ```
  
  - Bash

  ```bash
    docker --version
    docker compose version
    ```
  

## Steps

1) Start the broken stack (from repo root)

   - PowerShell

     ```powershell
     docker compose -f .\labs\nginx-startup-fail\assets\compose.yaml up -d
     ```
  
   - Bash

     ```bash
     docker compose -f ./labs/nginx-startup-fail/assets/compose.yaml up -d
     ```
  

2) Observe the failure
   - Status

     ```powershell
     docker compose -f .\labs\nginx-startup-fail\assets\compose.yaml ps
     ```
  
   - Logs (look for “unknown directive” or “invalid”)

     ```powershell
     docker compose -f .\labs\nginx-startup-fail\assets\compose.yaml logs nginx
     ```
  

3) Identify the issue
   - Open `labs/nginx-startup-fail/assets/nginx.conf`
   - Find the misspelled directive and fix the typo

4) Fix and retry
   - Change `roooot` to `root` in nginx.conf
   - Recreate the container

     ```powershell
     docker compose -f .\labs\nginx-startup-fail\assets\compose.yaml up -d --force-recreate
     ```

## Verification (success criteria)

- Browse <http://localhost:8080> and see “Nginx is up”
- Container health should go to `healthy` once the page is served
- Or use a CLI check:
  - Check health status quickly

    ```powershell
    docker compose -f .\labs\nginx-startup-fail\assets\compose.yaml ps
    # Expect: State shows "running (healthy)"
    ```
  - PowerShell

    ```powershell
    Invoke-WebRequest http://localhost:8080 -UseBasicParsing | Select-Object -ExpandProperty StatusCode
    # Expect: 200
    ```

  - Bash

    ```bash
    curl -s -o /dev/null -w "%{http_code}" http://localhost:8080
    # Expect: 200
    ```


## Hints (if you’re stuck)

- Re-run logs and read the first error: it usually tells you exactly what Nginx didn’t understand.
- If the fix doesn’t apply, make sure you recreated the container with `--force-recreate`.
- If port 8080 is busy, edit `compose.yaml` and change `8080:80` to another free port (e.g., `8081:80`).
- On Windows, if you see file permission issues, temporarily remove `:ro` from the volume lines to test.

## Metrics / Feedback

- Estimated time: 10 minutes
- Common pitfalls: wrong compose path; forgetting `--force-recreate` after config changes
- Optional next step: write a KB titled “Nginx: fix startup syntax errors” linking this lab

## Bonus challenges (optional)

- Inspect the health status with `docker compose ps` and experiment with failing/healthy states
- Explain in one sentence why pinning `nginx:1.27-alpine` improves reproducibility
- Change the published port and update your verification command

## Cleanup

```powershell
docker compose -f .\labs\nginx-startup-fail\assets\compose.yaml down -v
```

