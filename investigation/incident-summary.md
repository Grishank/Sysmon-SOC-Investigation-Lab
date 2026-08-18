# Incident Summary

## Incident Overview

A simulated suspicious PowerShell activity was generated inside an isolated Windows 11 virtual machine to practice a basic SOC investigation workflow.

The activity was monitored using **Sysmon** and investigated through **Windows Event Viewer**, with a focus on **Sysmon Event ID 1 — Process Create**.

---

## Investigation Objective

The investigation was performed to:

- Identify suspicious PowerShell execution
- Examine process creation telemetry
- Analyze command-line activity
- Identify system discovery behavior
- Examine parent-child process relationships
- Map observed behavior to the **MITRE ATT&CK** framework

---

## Environment

| Component | Details |
|---|---|
| Operating System | Windows 11 |
| Environment | Oracle VirtualBox |
| Telemetry | Sysmon |
| Log Source | Microsoft-Windows-Sysmon/Operational |
| Primary Event | Sysmon Event ID 1 — Process Create |
| Investigation Tool | Windows Event Viewer |
| Analysis | PowerShell + Sysmon telemetry |

---

## Simulated Activity

The investigation began with a simulated PowerShell execution.

Sysmon Event ID 1 recorded the creation of the PowerShell process and provided process metadata including:

- Process ID
- Executable image
- Command-line information
- Process GUID
- Parent process information
- File metadata

The observed PowerShell activity was associated with **MITRE ATT&CK T1059.001 — PowerShell**.

---

## System Discovery Activity

Additional Sysmon telemetry showed execution of `whoami.exe`.

This activity was mapped to:

**MITRE ATT&CK T1033 — System Owner/User Discovery**

The event demonstrated how process creation telemetry can reveal system discovery commands that may appear during suspicious activity.

---

## Key Findings

The investigation established the following:

1. A PowerShell process was created and captured by Sysmon Event ID 1.
2. The command-line data provided useful context about the PowerShell activity.
3. `whoami.exe` execution was identified as system owner/user discovery behavior.
4. Parent-process information was used to examine the process relationship.
5. The observed behavior was mapped to relevant MITRE ATT&CK techniques.

---

## Investigation Outcome

The activity was identified as **simulated suspicious behavior in an isolated lab environment**, not a real-world security incident.

The investigation demonstrated a basic SOC workflow:

**Telemetry → Event Analysis → Process Investigation → Behavior Identification → MITRE ATT&CK Mapping**
