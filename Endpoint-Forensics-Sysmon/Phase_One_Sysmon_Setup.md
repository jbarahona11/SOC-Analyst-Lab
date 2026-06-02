# Phase 1: Sysmon Installation and Configuration

### Objective
Deploy System Monitor (Sysmon) on a Windows host to generate and capture high-fidelity endpoint telemetry for threat hunting. 

### Execution
To filter out standard Windows background noise and focus exclusively on actionable, malicious indicators, the industry-standard **SwiftOnSecurity** configuration file was applied during installation. 

* **Tool:** Microsoft Sysinternals Sysmon
* **Configuration:** SwiftOnSecurity `sysmonconfig-export.xml`
* **Deployment:** Executed via Administrative PowerShell

**Installation Command:**
```powershell
.\Sysmon64.exe -accepteula -i sysmonconfig-export.xml

<img width="1093" height="630" alt="Sysmon Service Running" src="https://github.com/user-attachments/assets/08351b73-7e80-4337-b599-a49d7232361c" />
<img width="1098" height="635" alt="Sysmon Powershell first directory" src="https://github.com/user-attachments/assets/8c47afe0-e809-41ee-bce6-530a4143f9ce" />
<img width="1902" height="820" alt="Sysmonmonconfig" src="https://github.com/user-attachments/assets/adb3169e-5de2-4fc0-924c-59ea4896aef9" />
<img width="1892" height="563" alt="Sysmon Tool v15 2" src="https://github.com/user-attachments/assets/5fa4a060-a536-40a9-bbde-479b7a72a180" />

