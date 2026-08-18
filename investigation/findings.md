# Investigation Findings

## Executive Summary

A simulated suspicious PowerShell execution was investigated using Windows Sysmon telemetry.

The investigation identified PowerShell process creation, command-line activity involving a PowerShell script, system owner/user discovery using `whoami.exe`, and the parent-child process relationship between the observed processes.

The activity was mapped to the MITRE ATT&CK framework and treated as suspicious behavior within the controlled lab environment.

---

## Findings

### 1. Suspicious PowerShell Execution

Sysmon **Event ID 1 — Process Create** recorded the execution of `powershell.exe`.

The event contained command-line information showing PowerShell executing a script-related command.

**MITRE ATT&CK:** `T1059.001 — PowerShell`

**Evidence:**
- Sysmon Event ID: 1
- Process: `powershell.exe`
- PowerShell command-line telemetry captured
- Screenshot: `01-sysmon-powershell-execution.png`

---

### 2. System Owner/User Discovery

A subsequent `whoami.exe` process was observed through Sysmon Event ID 1.

The event was identified as system owner/user discovery activity.

**MITRE ATT&CK:** `T1033 — System Owner/User Discovery`

**Evidence:**
- Sysmon Event ID: 1
- Process: `whoami.exe`
- Sysmon rule identified the activity as System Owner/User Discovery
- Screenshot: `02_t1033_whoami_system_discovery.png`

---

### 3. Process Relationship Analysis

The investigation examined the parent and child process information available in Sysmon.

This provided execution context and helped establish the relationship between the observed PowerShell activity and subsequent processes.

**Evidence:**
- Parent Process ID
- Parent Image
- Process ID
- Process GUID
- Screenshot: `03_process_relationship.png`

---

## MITRE ATT&CK Mapping

| Technique | ID | Observed Activity |
|---|---|---|
| PowerShell | T1059.001 | PowerShell process execution |
| System Owner/User Discovery | T1033 | `whoami.exe` execution |

---

## Analyst Assessment

The observed activity contains multiple behaviors commonly associated with command execution and host discovery.

The combination of PowerShell execution followed by system owner/user discovery warrants investigation in a real SOC environment.

However, this activity was intentionally generated as part of a controlled security lab. Therefore, the findings should be interpreted as a simulated investigation rather than evidence of an actual compromise.

---

## Conclusion

The investigation successfully demonstrated how Sysmon process creation telemetry can be used to:

- Identify suspicious PowerShell execution
- Examine command-line activity
- Detect system discovery behavior
- Analyze parent-child process relationships
- Map observed activity to MITRE ATT&CK techniques

This investigation demonstrates a basic SOC workflow from **alert → evidence collection → process analysis → MITRE mapping → analyst assessment**.
