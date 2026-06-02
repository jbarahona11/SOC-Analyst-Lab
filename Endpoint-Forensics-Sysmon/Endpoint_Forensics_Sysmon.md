# Endpoint Forensics: Windows Sysmon Telemetry

🔗 **Objective**
Network traffic only tells half the story. To gain full-spectrum visibility into this Qakbot infection, network alerts must be correlated with endpoint logs. This section maps the Suricata network alert to the exact Windows System Monitor (Sysmon) Event IDs that a corporate SIEM would ingest.

---

## 1. Host Activity Timeline (`DESKTOP-EONIH83`)

The following table outlines the sequential execution of the malware on the compromised host immediately following the payload download.

| Timeline Sequence | Attack Phase | Sysmon Event ID | Technical Context & Evidence |
| :--- | :--- | :--- | :--- |
| **1. C2 Communication** | Initial Access / Delivery | **Event ID 3** (Network Connection) | Triggered when the initial application processes an outbound TCP connection to the external C2 server `188.167.188.224` over port 80. |
| **2. Payload Drop** | Staging | **Event ID 11** (File Create) | Logs when the masqueraded payload (`[malicious].png`) is downloaded and written to disk, typically staging in `\AppData\Local\Temp\`. |
| **3. Execution** | Execution | **Event ID 1** (Process Creation) | Logs when the `.png` file executes, revealing its true nature as a portable executable. This captures the command-line arguments and identifies spawned sub-processes (e.g., `cmd.exe` or `powershell.exe`). |
| **4. Defense Evasion** | Persistence / Injection | **Event ID 10** (Process Access) | Qakbot heavily relies on process injection. This captures the malicious binary opening a handle to inject code into legitimate Windows processes (like `explorer.exe`). |

---

## 2. Strategic Value

By correlating **Event ID 3** (Network Connection) with the **Suricata HTTP alert**, a SOC analyst can immediately verify that the payload was not just attempted, but successfully downloaded and executed on `DESKTOP-EONIH83`. This network-to-host visibility drastically reduces the time to triage, confirm, and contain the threat.
