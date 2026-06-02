# Phase 2: Simulating Attacker Activity

### Objective
Generate realistic, safe telemetry on the Windows host to emulate standard attacker behaviors during the discovery, execution, and persistence phases. This telemetry is designed to trigger the newly deployed Sysmon service.

### Execution
The following commands were executed via Administrative PowerShell to simulate malicious actions:

**1. Discovery / Reconnaissance**
Simulating an attacker enumerating user privileges immediately after gaining initial access.
```powershell
whoami /all
```


https://github.com/user-attachments/assets/19544abe-1100-4664-82d7-5cee0c25d244

