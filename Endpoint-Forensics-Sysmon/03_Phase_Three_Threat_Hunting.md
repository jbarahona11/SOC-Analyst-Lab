# Phase 3: Threat Hunting & Log Analysis

### Objective
Correlate the simulated malicious activity with actual endpoint logs. Utilize Windows Event Viewer to filter Sysmon telemetry, extract Indicators of Compromise (IoCs), and document the attacker's digital footprint.

### Execution
The investigation focused on the `Microsoft-Windows-Sysmon/Operational` log directory.

**1. Process Creation (Event ID 1)**
Filtered the logs for Event ID 1 to track command-line execution. Successfully isolated the exact moment the attacker executed reconnaissance and persistence commands.
* **Evidence Extracted:** The `CommandLine` field positively identified the execution of `whoami /all` and the malicious `schtasks` creation. 


**2. Network Connection (Event ID 3)**
Adjusted the log filter to Event ID 3 to track network beaconing. 
* **Evidence Extracted:** The `DestinationIp` field successfully captured the simulated outbound C2 connection to `8.8.8.8`.

<img width="1917" height="1007" alt="threat detection" src="https://github.com/user-attachments/assets/92b8194f-7537-475e-8973-6777415b2d56" />
