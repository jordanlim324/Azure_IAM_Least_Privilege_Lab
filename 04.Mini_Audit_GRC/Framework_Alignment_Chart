## Framework Alignment

Throughout the creation and implementation of this project I had noticed a few risks and flaws in my designs. I decided to document some of the risks seen within the project and map them to common frameworks such as NIST CSF and MITRE ATT&CK.

### NIST CSF 2.0 Mapping
   - The NIST CSF 2.0 published by the US Department of Commerce gives all organizations a set of guidelines to manage cybersecurity risks. The following chart details NIST CSF 2.0's Core Functions, and how well this lab has or has not adhered to those functions.

<div align = center>

| NIST CSF 2.0 Function | How This Lab Maps To The Function |
|:-------:|:--------:|
|Govern| Ownership model, with root tenant as governing authority, and Risk Register representing governance decisions and risk management strategies.|
|Identify| User/group inventory across three tiers (Administrator, Employee, Contractor) and Risk Register Scoring (Likelihood x Impact) representing asset identification and risk assessment.|
|Protect| Project Core - Role Based Access Control (RBAC), Least-Privilege role design, Security Defaults and MFA Enforcement, and mandatory password resets all fall under access control and identity protections.|
|Detect|Gap/Missing - The project has no logging, monitoring, or SIEM integration. No clear way to detect the misuse of access that is technically authorized.|
|Respond|Out of Scope for lab|
|Recover|Out of Scope for lab|

</div align = center>

### MITRE ATT&CK Mapping
   - The MITRE ATT&CK Framework is a knowledge base of a wide variety of tactics and techniques used by threat actors, based on real-world observation.

<div align = center>

| Risk | MITRE ATT&CK Mapping |
|:-------:|:--------:|
|Owner Escalation and Self Managed Admin Group Ownership (R01 and R02)|T1098 - Account Manipulation|
|Uncontrolled Role Assignment (R05) | T1098.003 - Account Manipulation: Additional Cloud Roles |
|Contractor/Guest Account Handling (R04) | T1078.004 - Valid Accounts: Cloud Accounts |

</div align = center>