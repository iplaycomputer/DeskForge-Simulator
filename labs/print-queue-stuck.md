# Lab: Print queue stuck (department-wide)

Reproduce a stuck print queue and practice clearing jobs and restarting the "spooler" safely.

**Related Ticket:** /tickets/cannot-print-to-shared-printer.md  
**Related KB:** /kb/printer-queue-clearing.md  
**Related Scenario:** /scenarios/printer-queue-clearing.md  
**Category:** Hardware  
**Environment:** Docker Desktop (Windows/macOS) or Docker Engine (Linux)

## Objectives

- Simulate a department-wide stuck print queue
- Clear the queue and restart the service
- Verify a new job processes

## Prerequisites (preflight)

- Docker running
- PowerShell or Bash

## Steps

1) Start the simulated print service (from repo root)
    - PowerShell

       ```powershell
       docker compose -f .\labs\print-queue-stuck\assets\compose.yaml up -d
       ```


    - Bash

       ```bash
       docker compose -f ./labs/print-queue-stuck/assets/compose.yaml up -d
       ```

2) Submit a job and simulate a stuck queue

   ```powershell
   # submit two jobs
   docker exec print-queue echo "report-a.pdf" >> /queue/jobs.txt
   docker exec print-queue echo "report-b.pdf" >> /queue/jobs.txt
   # simulate stuck consumer
   docker stop print-queue-consumer
   ```

3) Diagnose

   ```powershell
   docker exec print-queue cat /queue/jobs.txt
   docker compose -f .\labs\print-queue-stuck\assets\compose.yaml ps
   ```

4) Fix

   ```powershell
   # clear the oldest bad job and restart consumer
   docker exec print-queue sed -i '1d' /queue/jobs.txt
   docker start print-queue-consumer
   ```
5) Verify

   ```powershell
   # remaining job should be processed (file moved to processed.txt)
   docker exec print-queue cat /queue/processed.txt
   ```

## Verification

```powershell
   docker exec print-queue cat /queue/processed.txt
   # Expect: remaining job name present; queue stable
```


## Cleanup

```powershell
docker compose -f .\labs\print-queue-stuck\assets\compose.yaml down -v
```
