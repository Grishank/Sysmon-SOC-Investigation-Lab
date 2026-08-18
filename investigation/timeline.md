# Investigation Timeline

This timeline documents the major events observed during the simulated SOC investigation.

| Time (UTC) | Event | Evidence | Analysis |
|---|---|---|---|
| 16:39:37 | PowerShell process created | Sysmon Event ID 1 | PowerShell execution was captured by Sysmon and mapped to T1059.001 |
| 16:39:37 | PowerShell command-line activity observed | Sysmon Event ID 1 | Command-line telemetry provided additional context about the simulated activity |
| 16:46:58 | `whoami.exe` executed | Sysmon Event ID 1 | System owner/user discovery activity was identified and mapped to T1033 |
| During investigation | Parent-child process relationship analyzed | Sysmon process metadata | Parent process information was examined to understand process execution context |
| Investigation complete | Activity classified | Combined Sysmon evidence | Activity was confirmed as simulated suspicious behavior inside the isolated lab |

---

## Key Timeline Observations

### 1. PowerShell Execution

Sysmon recorded the creation of a PowerShell process through **Event ID 1 — Process Create**.

The event contained process metadata and command-line information useful for determining what the process was doing.

**MITRE ATT&CK:** T1059.001 — PowerShell

### 2. System Owner/User Discovery

A subsequent `whoami.exe` process was recorded.

This activity was identified as system owner/user discovery behavior.

**MITRE ATT&CK:** T1033 — System Owner/User Discovery

### 3. Process Relationship Analysis

Parent-process information from Sysmon was examined to understand how the observed processes were related.

This helped establish execution context rather than analyzing each process in isolation.

---

## Investigation Flow

```text
PowerShell Execution
        ↓
Sysmon Event ID 1
        ↓
Command-Line Analysis
        ↓
System Discovery Activity
        ↓
Parent/Child Process Analysis
        ↓
MITRE ATT&CK Mapping
        ↓
Investigation Conclusion
