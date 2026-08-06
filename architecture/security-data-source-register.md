# Project Beacon Security Data-Source Register

## Purpose

This register identifies the security telemetry required by Project
Beacon.

It documents:

- Where each log source originates
- Which assets generate the evidence
- How the evidence is expected to reach Microsoft Sentinel
- Which Sentinel or Log Analytics table may contain the data
- Which threats and investigations the source supports
- How successful ingestion will be validated
- Whether the source is planned, active, blocked, optional or deferred

This document is an architecture and deployment-planning artefact.

A source must not be marked Active until evidence has been successfully
generated, ingested and queried.

# 1. Data-source principles

Project Beacon follows these principles:

- Collect logs that support a defined security or investigation need.
- Avoid collecting unnecessary high-volume telemetry.
- Start with the most important identity, endpoint and server sources.
- Connect and validate one source at a time.
- Document licensing and cost limitations.
- Record the expected and actual destination table.
- Confirm timestamps, hostnames, users and IP addresses are accurate.
- Protect security logs from unauthorised access or alteration.
- Record failures and troubleshooting steps honestly.
- Review ingestion cost before increasing collection volume.
- Keep fictional, simulated and genuinely deployed evidence clearly separated.

# 2. Priority definitions

| Priority | Meaning | Deployment expectation |
|---|---|---|
| P1 — Essential | Required for the four core Project Beacon incidents | Must be attempted before optional integrations |
| P2 — Important | Adds valuable investigation or correlation evidence | Deploy after essential sources are working |
| P3 — Optional | Demonstrates additional platform or transferable skills | Use only when it does not delay the core project |

# 3. Deployment-status definitions

| Status | Meaning |
|---|---|
| Planned | Approved for a later deployment phase |
| In progress | Configuration has started but validation is incomplete |
| Active | Data has been generated, ingested and successfully queried |
| Partially active | Some required event types are available but gaps remain |
| Blocked | Deployment cannot continue because of a technical, licensing or access issue |
| Optional extension | Useful but not required for the core project |
| Deferred | Deliberately moved to a later stage |
| Retired | Removed from the environment |
| Simulated only | Evidence is produced using safe simulation or approved public data |

# 4. Identity data sources

| Source ID | Data source | Generating asset | Security evidence | Planned collection method | Expected destination | Priority | Status |
|---|---|---|---|---|---|---|---|
| DS-ID-001 | Microsoft Entra sign-in logs | `IDP-001` Microsoft Entra ID | Successful and failed sign-ins, IP addresses, applications, locations and authentication results | Microsoft Entra ID data connector | `SigninLogs` or the applicable Entra sign-in table | P1 | Planned |
| DS-ID-002 | Microsoft Entra audit logs | `IDP-001` Microsoft Entra ID | User, group, application, role and directory changes | Microsoft Entra ID data connector | `AuditLogs` | P1 | Planned |
| DS-ID-003 | Entra risky sign-in evidence | Microsoft Entra identity services | Risk detections, risky authentication and unusual sign-in indicators | Entra connector where licensing permits | Relevant Entra risk table | P2 | Planned subject to licensing |
| DS-ID-004 | Active Directory authentication events | `IDP-002`, `SRV-001`, `SRV-LAB-001` | Domain logons, failures, Kerberos activity, account lockouts and authentication changes | Windows Security Events through AMA or approved local collection | `SecurityEvent` | P1 | Planned |
| DS-ID-005 | Active Directory account-management events | Domain controller | User creation, deletion, password reset and group-membership changes | Windows Security Events through AMA | `SecurityEvent` | P1 | Planned |
| DS-ID-006 | Privileged-account activity | `IDP-005`, domain controller and administrator workstation | Administrative logons, privilege assignment and high-impact account activity | Windows and Entra log collection | `SecurityEvent`, `SigninLogs`, `AuditLogs` or applicable table | P1 | Planned |
| DS-ID-007 | Service-account authentication | `IDP-007` and server systems | Service logons, failures, unexpected hosts and unusual activity periods | Windows Security Events and Linux authentication logs | `SecurityEvent`, `Syslog` or applicable table | P2 | Planned |

## Identity monitoring use cases

Identity telemetry will support:

- Password-spraying investigation
- Account-compromise detection
- Successful login after repeated failures
- Unusual source-IP analysis
- Privileged-group changes
- Suspicious administrator activity
- Remote-access investigation
- Correlation between identity and endpoint events

# 5. Windows endpoint and server data sources

| Source ID | Data source | Generating asset | Security evidence | Planned collection method | Expected destination | Priority | Status |
|---|---|---|---|---|---|---|---|
| DS-WIN-001 | Windows Security Events | `WIN-END-LAB-001` | Logons, failures, privilege use, account changes and policy activity | Windows Security Events through Azure Monitor Agent and a data collection rule | `SecurityEvent` | P1 | Planned |
| DS-WIN-002 | Domain-controller Security Events | `SRV-LAB-001` | Domain authentication, Kerberos, account lockouts and group changes | Windows Security Events through AMA | `SecurityEvent` | P1 | Planned |
| DS-WIN-003 | Sysmon Operational log | `WIN-END-LAB-001` | Process creation, network connections, file creation, registry activity and process relationships | Azure Monitor Agent using an appropriate data collection rule or approved forwarding method | Expected `Event` or configured custom destination; validate during deployment | P1 | Planned |
| DS-WIN-004 | PowerShell Operational log | Windows test endpoint and server | Script-block, module and engine activity | AMA collection of selected Windows event channels | Expected `Event` or configured destination; validate during deployment | P1 | Planned |
| DS-WIN-005 | Windows Defender or antivirus events | Windows systems | Malware detection, quarantine and security-control changes | Selected Windows event channels or Defender connector where available | `Event`, Defender table or applicable destination | P2 | Planned |
| DS-WIN-006 | Windows Firewall events | Windows endpoint and server | Allowed and blocked connections | Selected Windows event collection | `SecurityEvent`, `Event` or applicable destination | P2 | Planned |
| DS-WIN-007 | Remote Desktop activity | Windows server and endpoint | Remote interactive logons, failures and session evidence | Windows Security Events | `SecurityEvent` | P1 | Planned |
| DS-WIN-008 | Scheduled-task events | Windows systems | Creation, modification and execution of scheduled tasks | Security Events, Sysmon and task-scheduler operational logs | `SecurityEvent`, `Event` or applicable destination | P2 | Planned |
| DS-WIN-009 | Windows service activity | Windows systems | New services, service changes and suspicious persistence | Security Events and Sysmon | `SecurityEvent` or `Event` | P2 | Planned |
| DS-WIN-010 | File-access auditing | File server or selected laboratory folder | Access, modification, deletion and permission changes | Selected Windows object-access auditing | `SecurityEvent` | P2 | Planned |

## Initial Windows event priorities

The first Windows collection should support:

- Successful logons
- Failed logons
- Account lockouts
- New process creation
- Privileged logons
- User and group changes
- New services
- Scheduled tasks
- PowerShell execution
- Remote desktop activity
- Security-log clearing
- File access where auditing is deliberately enabled

## Windows validation requirements

A Windows source becomes Active only when:

- The correct device is associated with the collection rule.
- A known event is generated safely.
- The event appears in the expected workspace.
- The hostname is correct.
- The username or security identifier is present where expected.
- The timestamp is accurate.
- The event can be found using KQL.
- Duplicate ingestion has been checked.
- The evidence screenshot has been sanitised.

# 6. Linux data sources

| Source ID | Data source | Generating asset | Security evidence | Planned collection method | Expected destination | Priority | Status |
|---|---|---|---|---|---|---|---|
| DS-LNX-001 | Linux system logs | `SRV-LAB-002` | System, service, kernel and general operating-system activity | Syslog through Azure Monitor Agent | `Syslog` | P1 | Planned |
| DS-LNX-002 | Linux authentication logs | Ubuntu server | SSH logins, failed authentication and privilege activity | Syslog through AMA | `Syslog` | P1 | Planned |
| DS-LNX-003 | `sudo` activity | Ubuntu server | Commands executed with elevated privileges | Syslog collection | `Syslog` | P1 | Planned |
| DS-LNX-004 | Linux service activity | Ubuntu server | Service start, stop, failure and configuration evidence | Syslog through AMA | `Syslog` | P2 | Planned |
| DS-LNX-005 | Linux audit evidence | Ubuntu server | Detailed process, file or account activity where audit configuration is enabled | Syslog, custom logs or an approved integration | `Syslog` or configured custom table | P2 | Planned |
| DS-LNX-006 | Linux network connections | Ubuntu server | Listening services and outbound connection evidence | Syslog, audit evidence, Zeek or Suricata | Relevant network or custom table | P2 | Planned |

## Linux validation requirements

The initial Linux validation test should include:

1. A successful SSH login inside the authorised laboratory
2. A failed SSH login using a fictional account
3. A permitted `sudo` command
4. A service start or stop event
5. Confirmation that the events appear with the correct hostname and time

# 7. Azure data sources

| Source ID | Data source | Generating asset | Security evidence | Planned collection method | Expected destination | Priority | Status |
|---|---|---|---|---|---|---|---|
| DS-AZR-001 | Azure Activity Logs | Azure subscription | Resource creation, deletion, configuration and administrative operations | Azure Activity data connector or diagnostic configuration | `AzureActivity` | P1 | Planned |
| DS-AZR-002 | Resource-group activity | Beacon resource group | Changes affecting Project Beacon resources | Azure Activity Logs | `AzureActivity` | P1 | Planned |
| DS-AZR-003 | Network security-group changes | Azure NSG | Creation, modification and deletion of traffic rules | Azure Activity Logs | `AzureActivity` | P1 | Planned |
| DS-AZR-004 | Azure role assignments | Azure RBAC | New or changed access assignments | Azure Activity and Entra audit evidence | `AzureActivity`, `AuditLogs` or applicable table | P1 | Planned |
| DS-AZR-005 | Virtual-machine operational evidence | Azure VM | VM start, stop, restart, configuration and guest telemetry | Azure Monitor and guest-log collection | Relevant Azure Monitor and guest tables | P2 | Planned |
| DS-AZR-006 | Azure Monitor alerts | Azure resources | Triggered conditions and resource alerts | Azure Monitor integration | Applicable alert or resource table | P2 | Planned |
| DS-AZR-007 | Storage-account activity | Azure storage account | Configuration, access and security-relevant storage operations | Diagnostic settings where cost and access permit | Applicable resource-specific table | P2 | Planned |
| DS-AZR-008 | Log Analytics health and usage | Log Analytics workspace | Ingestion volume, table availability and collection failures | Workspace usage and health queries | `Usage` and relevant health information | P1 | Planned |
| DS-AZR-009 | Azure cost and budget alerts | Azure subscription | Budget thresholds and unexpected spending | Azure Cost Management notification and evidence | Management evidence; not necessarily Sentinel telemetry | P1 | Planned |

## Azure monitoring priorities

Azure telemetry will support:

- Unauthorised resource changes
- Overly permissive network rules
- Unexpected resource deletion
- New privileged-role assignments
- Monitoring interruption
- Suspicious storage changes
- Unexpected virtual-machine activity
- Cost-control validation

# 8. Microsoft 365 data sources

| Source ID | Data source | Generating asset | Security evidence | Planned collection method | Expected destination | Priority | Status |
|---|---|---|---|---|---|---|---|
| DS-M365-001 | Microsoft 365 audit activity | Microsoft 365 tenant | User and administrative activity across supported services | Microsoft 365 data connector where trial access permits | `OfficeActivity` or applicable Microsoft 365 table | P2 | Planned subject to licensing |
| DS-M365-002 | Exchange Online activity | Exchange Online | Mailbox access, administrative changes and forwarding-rule activity | Microsoft 365 or Defender connector | `OfficeActivity`, Defender email table or applicable destination | P2 | Planned subject to licensing |
| DS-M365-003 | SharePoint activity | SharePoint Online | File access, sharing, downloads and permission changes | Microsoft 365 data connector | `OfficeActivity` or applicable table | P2 | Planned subject to licensing |
| DS-M365-004 | OneDrive activity | OneDrive for Business | File access, sharing and large downloads | Microsoft 365 data connector | `OfficeActivity` or applicable table | P2 | Planned subject to licensing |
| DS-M365-005 | Teams activity | Microsoft Teams | Collaboration and selected audit activity | Microsoft 365 data connector | `OfficeActivity` or applicable table | P3 | Optional extension |
| DS-M365-006 | Defender email alerts | Defender for Office 365 where available | Phishing, malicious attachments, malicious links and email incidents | Microsoft Defender XDR connector | Applicable Defender alert and email tables | P2 | Planned subject to licensing |

## Microsoft 365 investigation use cases

These sources may support:

- Phishing investigation
- Malicious mailbox-rule detection
- Compromised mailbox analysis
- Unauthorised file sharing
- Large-volume file download
- Activity following an unusual sign-in
- Business-email-compromise investigation

# 9. Network-security data sources

| Source ID | Data source | Generating asset | Security evidence | Planned collection method | Expected destination | Priority | Status |
|---|---|---|---|---|---|---|---|
| DS-NET-001 | Suricata `eve.json` | `SEC-007` Suricata sensor | IDS alerts, flows, DNS, HTTP, TLS and network metadata | CEF, Syslog or Custom Logs via AMA depending on final design | `CommonSecurityLog`, `Syslog` or a custom table | P1 | Planned |
| DS-NET-002 | Suricata fast alert log | Suricata sensor | Human-readable alert records | Local evidence and optional custom ingestion | Custom table or local evidence | P2 | Planned |
| DS-NET-003 | Zeek connection logs | `SEC-008` Zeek sensor | Source, destination, ports, protocols and connection state | Syslog, CEF or custom-log collection | `Syslog` or custom table | P3 | Optional extension |
| DS-NET-004 | Zeek DNS logs | Zeek sensor | DNS queries, responses and unusual-domain evidence | Custom or Syslog-based ingestion | Custom table or `Syslog` | P3 | Optional extension |
| DS-NET-005 | Zeek HTTP or TLS logs | Zeek sensor | Web and encrypted-session metadata | Custom-log ingestion | Custom table | P3 | Optional extension |
| DS-NET-006 | Packet captures | Wireshark, tcpdump or approved capture system | Detailed packet-level evidence | Stored locally as investigation evidence; not continuously ingested | Evidence file rather than normal Sentinel table | P2 | Planned |
| DS-NET-007 | VPN authentication logs | Remote-access service | Remote login success, failure, source IP and session times | Syslog, CEF or service connector | `CommonSecurityLog`, `Syslog` or service-specific table | P2 | Simulated unless a safe source is available |
| DS-NET-008 | Firewall or NSG network evidence | Firewall or Azure NSG | Allowed, denied and configuration activity | Syslog, CEF, Azure logs or flow evidence where enabled | Appropriate network or Azure table | P2 | Planned |

## Suricata deployment decision

Suricata is the primary network intrusion-detection source for the core
project.

The final ingestion method will be selected after evaluating:

- Available Azure trial access
- Log volume
- AMA support
- Whether CEF formatting is used
- Whether direct custom-log ingestion is more practical
- The cost of continuous ingestion
- The investigation value of each event type

The actual destination table must be recorded after testing.

# 10. Microsoft Defender data sources

| Source ID | Data source | Generating asset | Security evidence | Planned collection method | Expected destination | Priority | Status |
|---|---|---|---|---|---|---|---|
| DS-DEF-001 | Defender XDR alerts | Microsoft Defender XDR | Correlated security alerts and incidents | Microsoft Defender XDR data connector where trial access permits | `SecurityAlert`, `SecurityIncident` or relevant Defender tables | P2 | Planned subject to licensing |
| DS-DEF-002 | Defender for Endpoint device events | Windows test endpoint | Process, file, registry, network and device evidence | Defender XDR integration | Relevant `Device*` advanced-hunting tables | P2 | Planned subject to licensing |
| DS-DEF-003 | Defender for Identity evidence | Active Directory environment | Suspicious identity and domain behaviour | Defender XDR integration | Relevant identity or alert tables | P3 | Optional subject to licensing |
| DS-DEF-004 | Defender for Cloud alerts | Azure resources | Cloud posture and workload alerts | Defender for Cloud or Defender XDR integration | `SecurityAlert` or relevant cloud-security table | P3 | Optional subject to licensing |

## Licensing boundary

Defender sources will not be treated as required for core project
completion when suitable trial access is unavailable.

The project must continue using:

- Windows Security Events
- Sysmon
- Entra evidence
- Linux logs
- Suricata
- Microsoft Sentinel
- Safe simulations or approved public datasets

# 11. Microsoft Sentinel operational data

| Source ID | Data source | Generating asset | Security evidence | Planned collection method | Expected destination | Priority | Status |
|---|---|---|---|---|---|---|---|
| DS-SEN-001 | Microsoft Sentinel alerts | Sentinel analytics rules and connected products | Security alerts generated from detection logic | Native Sentinel operation | `SecurityAlert` | P1 | Planned |
| DS-SEN-002 | Microsoft Sentinel incidents | Sentinel | Grouped alerts, entities, status and investigation information | Native Sentinel operation | `SecurityIncident` | P1 | Planned |
| DS-SEN-003 | Analytics-rule execution evidence | Sentinel | Rule triggers and alert generation | Sentinel configuration and incident records | Applicable Sentinel tables and configuration evidence | P1 | Planned |
| DS-SEN-004 | Data-connector health | Sentinel and Log Analytics | Connector availability and ingestion gaps | Connector status and health checks | Health evidence and applicable tables | P1 | Planned |
| DS-SEN-005 | Automation activity | Sentinel automation rules or playbooks | Automated assignments, status changes or response actions | Sentinel operational evidence | Applicable Sentinel or Azure activity evidence | P3 | Deferred until core detections work |

# 12. Secondary SIEM data sources

| Source ID | Data source | Platform | Planned purpose | Priority | Status |
|---|---|---|---|---|---|
| DS-SPL-001 | Selected Windows or network dataset | Splunk Enterprise trial or free lab | Recreate a small number of Sentinel detections using SPL | P3 | Optional extension |
| DS-SPL-002 | Suricata sample data | Splunk | Demonstrate transferable network investigation skills | P3 | Optional extension |
| DS-SPL-003 | Small SOC dashboard dataset | Splunk | Produce one secondary SIEM dashboard | P3 | Optional extension |

Splunk will not replace Microsoft Sentinel as Project Beacon's primary
SIEM.

It will be used only after the Sentinel, KQL and incident-investigation
requirements are substantially complete.

# 13. Core deployment order

The planned deployment sequence is:

1. Log Analytics workspace
2. Microsoft Sentinel
3. Azure Activity Logs
4. Windows Security Events from the test endpoint
5. Windows Security Events from the laboratory server
6. Sysmon Operational events
7. PowerShell Operational events
8. Linux Syslog and authentication evidence
9. Microsoft Entra sign-in and audit evidence where available
10. Suricata network alerts
11. Microsoft 365 evidence where licensing permits
12. Defender XDR evidence where trial access permits
13. Zeek as an optional extension
14. Splunk as an optional secondary SIEM exercise

# 14. Four-incident evidence mapping

| Incident | Required primary sources | Useful secondary sources |
|---|---|---|
| Password spraying | Entra sign-in logs, Windows authentication failures, domain-controller events | VPN logs, firewall evidence and risky-sign-in data |
| Phishing and suspicious PowerShell | Entra sign-ins, Microsoft 365 activity, PowerShell logs and Sysmon | Defender email alerts, DNS evidence and endpoint network connections |
| Privilege escalation and lateral movement | Windows Security Events, Sysmon, domain-controller logs and privileged-account activity | Suricata, Zeek, firewall evidence and Defender for Identity |
| Data staging and attempted exfiltration | Sysmon, file-access evidence, PowerShell and network telemetry | SharePoint, OneDrive, Suricata, Zeek and Defender endpoint evidence |

# 15. Source-validation checklist

Every source must pass the following checks before it is marked Active:

- [ ] Source asset exists
- [ ] Required connector or collection method is configured
- [ ] Collection rule is assigned correctly where required
- [ ] A safe known event has been generated
- [ ] The expected event appears in Log Analytics or Sentinel
- [ ] Actual destination table is recorded
- [ ] Hostname or device identity is correct
- [ ] User identity is present where expected
- [ ] Source and destination IP information is correct where expected
- [ ] Timestamp is accurate
- [ ] Time zone has been considered
- [ ] Duplicate ingestion has been checked
- [ ] A basic KQL validation query has been saved
- [ ] Ingestion volume has been reviewed
- [ ] Cost implications have been reviewed
- [ ] Screenshot evidence has been sanitised
- [ ] Failure and troubleshooting notes have been recorded
- [ ] Register status has been updated

# 16. Data-source validation record

This table will be completed during deployment.

| Source ID | Test date | Test event | Actual table | Result | Issue found | Evidence location | Status |
|---|---|---|---|---|---|---|---|
| DS-AZR-001 | Not tested | Azure resource change | To be confirmed | Not tested | None recorded | To be added | Planned |
| DS-WIN-001 | Not tested | Windows logon event | To be confirmed | Not tested | None recorded | To be added | Planned |
| DS-WIN-003 | Not tested | Sysmon process creation | To be confirmed | Not tested | None recorded | To be added | Planned |
| DS-WIN-004 | Not tested | PowerShell test command | To be confirmed | Not tested | None recorded | To be added | Planned |
| DS-LNX-001 | Not tested | Linux Syslog event | To be confirmed | Not tested | None recorded | To be added | Planned |
| DS-ID-001 | Not tested | Entra sign-in | To be confirmed | Not tested | None recorded | To be added | Planned |
| DS-NET-001 | Not tested | Suricata alert | To be confirmed | Not tested | None recorded | To be added | Planned |

# 17. Cost-control considerations

Before activating a data source, Project Beacon will consider:

- Estimated daily ingestion volume
- Whether the source is necessary for a defined use case
- Whether filtering can reduce unnecessary events
- Whether the source is covered by a trial
- Whether retention settings create additional cost
- Whether a local evidence file is sufficient
- Whether continuous ingestion is required
- Whether the source can be enabled only during laboratory sessions

High-volume collection must not be activated without a clear security
or learning objective.

# 18. Register maintenance

This register will be updated:

- When a connector is configured
- When an actual destination table is confirmed
- When a source becomes Active
- When ingestion fails
- When licensing prevents deployment
- When a source is deferred or retired
- When a new incident requires additional telemetry
- At the end of every major project phase

# 19. Current summary

At the time of creating this register:

- The security data sources are planned.
- GitHub documentation is active.
- Microsoft Sentinel has not yet been deployed.
- Log Analytics has not yet been deployed.
- Windows and Linux logs have not yet been ingested.
- Suricata evidence has not yet been ingested.
- Defender and Microsoft 365 sources depend on available licensing.
- Zeek and Splunk remain optional extensions.

These statuses must be updated only after real configuration and
validation work has been completed.
