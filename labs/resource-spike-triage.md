# Lab: Resource spike triage (CPU/Disk)

Practice identifying and resolving resource spikes that cause slowness.

**Related Ticket:** /tickets/computer-running-slow-lagging.md  
**Related KB:** /kb/workstation-performance-triage.md  
**Related Scenario:** /scenarios/workstation-performance-triage.md  
**Category:** Hardware  
**Environment:** Linux VM or Docker container

## Objectives
- Trigger a CPU or disk spike
- Identify the culprit
- Resolve and verify performance returns to normal

## Prerequisites
- Linux shell (VM or WSL2) or Docker

## Steps
1) Create a CPU spike (Linux VM)
   ```bash
   sudo apt-get update && sudo apt-get install -y stress-ng
   stress-ng --cpu 2 --timeout 60s &
   top -b -n 1 | head -n 20
   ```
2) Or create a CPU spike (Docker)
   ```bash
   docker run --rm -d --name cpu-spike alpine:3.20 sh -c "apk add --no-cache stress-ng && stress-ng --cpu 2 --timeout 60s"
   docker top cpu-spike
   ```
3) Resolve
   ```bash
   # VM: kill the process if still running
   pkill -f stress-ng || true
   # Docker: stop container
   docker stop cpu-spike || true
   ```
4) Verify
   ```bash
   top -b -n 1 | head -n 20
   # Expect CPU usage back to normal
   ```

   ## Verification
   ```bash
   top -b -n 1 | head -n 20
   # Expect: CPU/Disk normalized; no stress-ng running
   ```

## Cleanup
```bash
pkill -f stress-ng 2>/dev/null || true
docker rm -f cpu-spike 2>/dev/null || true
```
