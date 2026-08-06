# Project Beacon Hybrid SOC Architecture Design

## Document purpose

This document defines the planned hybrid Security Operations Centre
architecture for Project Beacon.

It combines the organisation profile, asset inventory, network zones,
trust boundaries and security data-source register into one coherent
technical design.

The architecture supports Beacon Professional Services Ltd, a fictional
UK SME employing approximately 200 people through office-based, hybrid
and remote working arrangements.

This document describes the intended design. A component must not be
described as deployed until it has been created, configured and
validated.

## Document status

- **Architecture version:** 1.0
- **Design status:** Planned
- **Deployment status:** Not yet fully deployed
- **Primary SIEM:** Microsoft Sentinel
- **Primary query language:** Kusto Query Language
- **Primary endpoint telemetry:** Windows Security Events and Sysmon
- **Primary network IDS:** Suricata
- **Optional network extension:** Zeek
- **Optional secondary SIEM:** Splunk
- **Testing environment:** Authorised isolated laboratory
- **Organisation:** Fictional
- **Incident activity:** Safely simulated or supported by approved datasets

# 1. Business and security context

Beacon Professional Services Ltd provides:

- Managed administrative support
- IT support and consulting
- Business-process services
- Customer-account management
- Project and technical support

The organisation stores and processes:

- Customer records
- Employee personal information
- Commercial contracts
- Financial information
- Microsoft 365 email
- Project and technical files
- Help-desk records
- System configuration information
- Security logs and incident evidence

The main security concerns are:

- Phishing
- Password spraying
- Account compromise
- Suspicious PowerShell execution
- Privilege escalation
- Lateral movement
- Data staging
- Attempted data exfiltration
- Limited centralised monitoring
- Inconsistent incident escalation
- Limited endpoint and network visibility
- Insufficiently tested incident-response procedures

# 2. Architecture objectives

The Project Beacon architecture is designed to:

1. Centralise relevant security telemetry.
2. Improve visibility across identity, endpoint, server, cloud and
   network activity.
3. Support alert triage and incident investigation.
4. Provide sufficient evidence to create technical timelines.
5. Support KQL monitoring, investigation and threat hunting.
6. Enable documented detection engineering.
7. Separate standard users from privileged administration.
8. Restrict communication between user, server and testing zones.
9. Protect the integrity of security logs and incident evidence.
10. Remain affordable and manageable for a resource-constrained SME.
11. Support four realistic simulated security incidents.
12. Produce sanitised public portfolio evidence.
13. Demonstrate practical Microsoft security-operations capability.
14. Translate technical findings into business-risk reporting.

# 3. Design principles

Project Beacon follows these principles:

- No system is automatically trusted because it is inside the network.
- Users receive only the access necessary for their responsibilities.
- Privileged accounts remain separate from standard accounts.
- Administrative activity must be logged.
- Servers are separated from ordinary user systems.
- Security logs are centralised where practical.
- Data sources are connected and validated one at a time.
- High-volume logging must have a defined investigation purpose.
- Cost controls must be configured before paid Azure deployment.
- Testing remains inside authorised laboratory environments.
- Fictional, simulated and deployed assets remain clearly distinguished.
- Failures, limitations and blocked integrations are documented honestly.
- Sensitive information is removed before publication.

# 4. High-level architectural layers

Project Beacon contains seven main architectural layers.

## Layer 1 — Users and identities

This layer contains:

- Standard employees
- Hybrid and remote employees
- Customer-account personnel
- Project and technical teams
- Service Desk personnel
- Systems administrators
- Managers and executives
- Standard user accounts
- Privileged administrator accounts
- Service accounts

Identity platforms and controls include:

- Microsoft Entra ID
- Active Directory Domain Services
- Multi-factor authentication
- Role-based access control
- Privileged accounts
- Standard employee accounts
- Service accounts

## Layer 2 — Employee endpoints

This layer contains representative Windows employee systems.

The fictional organisation contains approximately 200 employees, but
the practical laboratory will use a smaller number of representative
systems.

The initial endpoint will include:

- Windows operating system
- Windows Security Event logging
- Sysmon
- PowerShell logging
- Network connectivity to authorised laboratory services
- Connection to selected monitoring infrastructure

## Layer 3 — Servers and internal services

This layer contains:

- Windows Server
- Active Directory Domain Services
- DNS
- File-server services
- Selected application services
- Ubuntu Linux server
- Linux authentication and system logging

The minimum laboratory representation is:

- One Windows Server evaluation system
- One Windows employee test endpoint
- One Ubuntu Linux server

## Layer 4 — Microsoft cloud services

This layer may contain:

- Microsoft Azure
- Microsoft Entra ID
- Microsoft 365
- Exchange Online
- SharePoint Online
- OneDrive for Business
- Microsoft Teams
- Microsoft Defender services where licensing permits

Not all Microsoft 365 or Defender components are guaranteed to be
available.

Licensing limitations will be documented honestly.

## Layer 5 — Security monitoring

This layer contains:

- Microsoft Sentinel
- Azure Log Analytics
- Azure Monitor
- Windows Security Events
- Sysmon
- PowerShell logs
- Linux Syslog
- Suricata
- Optional Zeek
- Optional Defender XDR telemetry
- Optional Splunk exercises
- Wireshark and packet evidence

## Layer 6 — Authorised testing

This layer contains:

- Kali Linux
- Fictional laboratory accounts
- Controlled Windows and Linux targets
- Safe network-traffic generation
- Approved packet captures
- Authorised attack simulations

The Kali system must remain inside the isolated laboratory boundary.

## Layer 7 — Documentation and reporting

This layer contains:

- GitHub repository
- Incident tickets
- Investigation records
- KQL query library
- Detection rules
- Runbooks
- Metrics
- Tabletop records
- Executive reports
- Final Word report
- Final PDF portfolio report

# 5. Planned architecture components

| Component ID | Component | Role | Zone | Planned status |
|---|---|---|---|---|
| ARCH-001 | Microsoft Entra ID | Cloud identity and authentication | Microsoft cloud services zone | Planned |
| ARCH-002 | Active Directory Domain Services | Domain identity and computer management | Server zone | Planned |
| ARCH-003 | Windows test endpoint | Represents an employee workstation | Corporate user and laboratory zones | Planned |
| ARCH-004 | Administrator workstation | Represents privileged administration | Privileged administration zone | Planned or logically represented |
| ARCH-005 | Windows Server | Provides AD, DNS and server evidence | Server zone | Planned |
| ARCH-006 | Ubuntu Linux server | Provides Syslog, SSH and privilege evidence | Server and laboratory zones | Planned |
| ARCH-007 | Azure subscription | Hosts the Azure mini-lab | Azure cloud zone | Planned |
| ARCH-008 | Azure resource group | Organises Beacon Azure resources | Azure cloud zone | Planned |
| ARCH-009 | Azure virtual network | Provides Azure network segmentation | Azure cloud zone | Planned |
| ARCH-010 | Azure user subnet | Contains representative endpoint resources | Azure cloud zone | Planned |
| ARCH-011 | Azure server subnet | Contains server or monitoring resources | Azure cloud zone | Planned |
| ARCH-012 | Azure management subnet | Supports selected management activity | Management plane | Planned where required |
| ARCH-013 | Network security group | Restricts Azure traffic | Azure cloud zone | Planned |
| ARCH-014 | Azure storage account | Demonstrates cloud storage and monitoring | Azure cloud zone | Planned |
| ARCH-015 | Log Analytics workspace | Stores and queries security telemetry | Security-monitoring zone | Planned |
| ARCH-016 | Microsoft Sentinel | Primary SIEM and incident platform | Security-monitoring zone | Planned |
| ARCH-017 | Azure Monitor | Creates resource monitoring and alerts | Security-monitoring zone | Planned |
| ARCH-018 | Sysmon | Provides detailed Windows telemetry | Endpoint and server zones | Planned |
| ARCH-019 | PowerShell logging | Provides script and command evidence | Endpoint and server zones | Planned |
| ARCH-020 | Suricata | Primary network intrusion-detection system | Monitoring and laboratory zones | Planned |
| ARCH-021 | Zeek | Optional network metadata source | Security-monitoring zone | Optional extension |
| ARCH-022 | Microsoft Defender XDR | Extended Microsoft investigation platform | Microsoft cloud and monitoring zones | Subject to licensing |
| ARCH-023 | Splunk | Optional secondary SIEM exercise | Security-monitoring zone | Optional extension |
| ARCH-024 | Kali Linux | Generates controlled security events | Authorised laboratory zone | Planned |
| ARCH-025 | SOC analyst workstation | Used for queries, investigation and documentation | Security-monitoring zone | Existing workstation |
| ARCH-026 | GitHub repository | Stores sanitised project artefacts | Documentation layer | Active |

# 6. Identity architecture

## Hybrid identity design

Project Beacon uses a hybrid identity model consisting of:

- Microsoft Entra ID for cloud identities and access
- Active Directory for domain users, computers and internal services
- Standard user accounts for daily activity
- Separate privileged administrator accounts
- Service accounts for selected services and scheduled activity
- MFA where available
- Azure RBAC for cloud-resource access

## Identity security requirements

The architecture requires:

- Standard and administrator accounts to remain separate
- Administrative access to be limited
- Privileged-role changes to be logged
- Authentication failures to be monitored
- Successful logons after repeated failures to be investigated
- Unusual source IP addresses to be reviewed
- Service-account activity to be baselined
- MFA to be used where available
- High-impact identity changes to be documented
- Disabled or weakened identity controls to generate investigation activity

## Planned identity evidence

The planned identity evidence includes:

- Entra sign-in logs
- Entra audit logs
- Windows authentication events
- Domain-controller Security Events
- Account-lockout events
- User and group changes
- Privileged-role assignments
- Service-account authentication
- MFA success and failure evidence where available

# 7. Endpoint architecture

## Fictional endpoint environment

Beacon contains logical endpoint groups for:

- General office employees
- Hybrid and remote employees
- Customer-account staff
- Project and technical teams
- Service Desk personnel
- Systems administrators
- Managers and executives

## Laboratory endpoint

The initial laboratory will use one representative Windows endpoint.

The endpoint will generate:

- Successful logons
- Failed authentication attempts
- Process creation
- Suspicious PowerShell activity
- Network connections
- File creation
- Scheduled-task activity
- Windows service activity
- Privileged activity
- Selected firewall and antivirus evidence

## Endpoint telemetry

The endpoint will use:

- Windows Security Events
- Sysmon
- PowerShell Operational logging
- Selected Windows Defender or antivirus events where available
- Windows Firewall evidence where useful

# 8. Server architecture

## Windows Server

The Windows Server laboratory system may provide:

- Active Directory Domain Services
- DNS
- Domain authentication
- User and group management
- File or shared-resource activity
- Remote administration evidence

Important Windows Server events include:

- Successful and failed logons
- Kerberos activity
- Account lockouts
- User creation and deletion
- Group-membership changes
- Privileged logons
- Remote Desktop activity
- New Windows services
- Scheduled tasks
- PowerShell execution
- Security-log clearing

## Linux server

The Ubuntu Linux server will provide:

- SSH activity
- Successful and failed authentication
- `sudo` evidence
- Service activity
- Syslog
- Process evidence where available
- Network evidence where available

The Linux server may also host Suricata or Zeek if this is practical and
does not interfere with the core server role.

# 9. Network architecture

## Logical network zones

The architecture includes:

- Internet and external zone
- Remote-access zone
- Corporate user zone
- Privileged administration zone
- Server zone
- Security-monitoring zone
- Azure cloud zone
- Microsoft cloud services zone
- Authorised laboratory zone
- Management plane

## Planned network ranges

| Network | Planned range | Purpose |
|---|---|---|
| Azure virtual network | `10.20.0.0/16` | Overall Azure Project Beacon network |
| Azure user subnet | `10.20.10.0/24` | Representative endpoint resources |
| Azure server subnet | `10.20.20.0/24` | Server or monitoring resources |
| Azure management subnet | `10.20.30.0/24` | Management services where required |
| Local isolated laboratory | `192.168.50.0/24` | Local VirtualBox or equivalent laboratory |
| Security-monitoring segment | `192.168.60.0/24` | Suricata, Zeek or monitoring systems |

These are planned documentation values.

Actual deployed addresses must be recorded after deployment.

## Network restrictions

The design restricts:

- Direct public access to administrative services
- Standard-user access to domain-controller administration
- Unrestricted administrative communication between zones
- Kali access outside the authorised laboratory
- Public access to security logs
- Unnecessary inbound access to monitoring tools
- Unapproved transfer of sensitive information
- Normal user accounts performing privileged operations

## Network monitoring

Network monitoring may include:

- Suricata alerts
- Suricata `eve.json`
- DNS evidence
- Connection and flow records
- Packet captures
- Optional Zeek logs
- Azure Activity Logs
- Network security-group changes
- VPN evidence where safely available

# 10. Azure architecture

The planned Azure mini-lab will contain:

- One Azure subscription
- One Beacon resource group
- One virtual network
- Two primary subnets
- One network security group
- At least one Windows or Linux virtual machine
- One storage account
- One Log Analytics workspace
- One Azure Monitor alert
- One RBAC assignment

## Planned Azure naming convention

| Resource type | Proposed name |
|---|---|
| Resource group | `rg-beacon-soc-lab-uks-01` |
| Virtual network | `vnet-beacon-soc-uks-01` |
| User subnet | `snet-users-01` |
| Server subnet | `snet-servers-01` |
| Management subnet | `snet-management-01` |
| Network security group | `nsg-beacon-soc-01` |
| Log Analytics workspace | `law-beacon-soc-uks-01` |
| Storage account | To be created using Azure naming requirements |
| Virtual machine | `vm-beacon-lab-01` |

Actual names may be adjusted during deployment where Azure naming rules
require it.

## Azure security controls

The architecture will use:

- Azure RBAC
- Network security groups
- Azure Activity Logs
- Cost alerts
- Resource grouping
- Restricted administrative access
- VM auto-shutdown
- Minimal resource sizing
- Removal of unused resources
- Monitoring of role and configuration changes

## Azure cost controls

Before deploying resources:

- Confirm the available Azure account or student credit
- Create a budget
- Configure cost alerts
- Select the smallest suitable resources
- Configure VM auto-shutdown
- Avoid unnecessary public IP addresses
- Limit log-ingestion volume
- Review cost after each technical session
- Delete resources that are no longer required

# 11. Security-monitoring architecture

## Microsoft Sentinel

Microsoft Sentinel is the primary SIEM for Project Beacon.

Sentinel will be used to:

- Centralise security telemetry
- Run KQL queries
- Create analytics rules
- Generate alerts
- Create and manage incidents
- Investigate users, devices, IP addresses and processes
- Support threat hunting
- Document MITRE ATT&CK coverage
- Support workbooks and dashboards where practical

## Azure Log Analytics

Log Analytics will store the primary Microsoft-focused telemetry.

Planned tables may include:

- `SecurityEvent`
- `SigninLogs`
- `AuditLogs`
- `AzureActivity`
- `Syslog`
- `CommonSecurityLog`
- `SecurityAlert`
- `SecurityIncident`
- `OfficeActivity`
- Relevant custom or Defender tables

Actual table names will be confirmed during deployment.

## Windows telemetry

Sysmon will provide:

- Process creation
- Parent-child process relationships
- Network connections
- File creation
- Registry activity
- Selected persistence indicators

PowerShell logging will provide:

- Script-block evidence
- Module activity
- Command activity
- PowerShell engine events

## Network telemetry

Suricata is the primary network IDS.

Suricata may provide:

- IDS alerts
- Network flows
- DNS evidence
- HTTP metadata
- TLS metadata
- Source and destination IP addresses
- Port and protocol information

Zeek remains optional and may provide:

- Connection logs
- DNS logs
- HTTP metadata
- TLS metadata
- Protocol-level evidence

## Microsoft Defender telemetry

Where trial access permits, Defender XDR may provide:

- Correlated alerts
- Endpoint evidence
- Process trees
- Device timelines
- Email-security evidence
- Identity alerts
- Advanced Hunting data

Defender is not mandatory where licensing prevents access.

## Secondary SIEM

Splunk remains an optional exercise.

It may later be used to:

- Ingest a small selected dataset
- Recreate one or more KQL detections using SPL
- Build a small dashboard
- Demonstrate transferable SIEM knowledge

Splunk will not replace Microsoft Sentinel.

# 12. Planned security-log flows

## Windows endpoint flow

```text
Windows test endpoint
    → Windows Security Events
    → Sysmon
    → PowerShell Operational logs
    → Azure Monitor Agent or approved collection method
    → Log Analytics
    → Microsoft Sentinel
```

## Windows Server and Active Directory flow

```text
Windows Server / Active Directory
    → Authentication and account events
    → Windows Security Events
    → Azure Monitor Agent
    → Log Analytics
    → Microsoft Sentinel
```

## Linux server flow

```text
Ubuntu Linux server
    → Syslog and authentication evidence
    → Azure Monitor Agent
    → Log Analytics
    → Microsoft Sentinel
```

## Entra ID flow

```text
Microsoft Entra ID
    → Sign-in and audit logs
    → Sentinel data connector
    → Log Analytics / Microsoft Sentinel
```

## Azure activity flow

```text
Microsoft Azure
    → Azure Activity Logs
    → Log Analytics / Microsoft Sentinel
```

## Suricata flow

```text
Suricata sensor
    → eve.json, Syslog, CEF or custom collection
    → Log Analytics
    → Microsoft Sentinel
```

## Microsoft 365 and Defender flow

```text
Microsoft 365 or Defender
    → Supported data connector
    → Microsoft Sentinel
```

## Investigation and reporting flow

```text
SOC analyst
    → KQL queries
    → Alerts and incidents
    → Investigation documentation
    → Detection improvements
    → Runbooks
    → Executive reporting
```

The dedicated security-log data-flow diagram will visualise these paths.

# 13. Four-incident architecture support

## Incident 1 — Password spraying

Primary components:

- Microsoft Entra ID
- Active Directory
- Domain controller
- Windows Security Events
- Sign-in logs
- Microsoft Sentinel
- KQL

Supporting evidence:

- VPN logs
- Firewall or network evidence
- Source IP information
- Account-lockout events

## Incident 2 — Phishing and suspicious PowerShell

Primary components:

- Microsoft 365 or simulated email evidence
- Windows endpoint
- Sysmon
- PowerShell logging
- Entra sign-in logs
- Microsoft Sentinel
- KQL

Supporting evidence:

- DNS activity
- Network connections
- Suricata alerts
- Defender evidence where available

## Incident 3 — Privilege escalation and lateral movement

Primary components:

- Windows endpoint
- Windows Server
- Active Directory
- Windows Security Events
- Sysmon
- Privileged-account evidence
- Microsoft Sentinel
- KQL

Supporting evidence:

- Suricata
- Optional Zeek
- Remote Desktop events
- Service and scheduled-task activity
- Defender for Identity where available

## Incident 4 — Data staging and attempted exfiltration

Primary components:

- Windows endpoint or file server
- File evidence
- Sysmon
- PowerShell
- Suricata
- Microsoft Sentinel
- KQL

Supporting evidence:

- SharePoint or OneDrive activity where available
- DNS evidence
- Large outbound transfers
- Optional Zeek
- Defender endpoint evidence

# 14. Administrative security design

Administrative activities must use:

- Separate privileged accounts
- Restricted management access
- Documented RBAC assignments
- Logged privileged activity
- Dedicated administrator systems where practical
- Approval for high-impact containment
- No routine browsing or email using privileged accounts
- Evidence preservation for significant changes
- Clear separation between standard and administrative sessions

# 15. Evidence and documentation design

Every major technical task will produce:

- A Markdown explanation
- Sanitised screenshots
- Professional Git commits
- Configuration notes
- Validation evidence
- Troubleshooting records
- Known limitations
- Updated status information

Every incident investigation will contain:

- Incident ticket
- Alert or trigger
- Investigation hypothesis
- Evidence table
- Technical timeline
- KQL queries
- MITRE ATT&CK mapping
- Severity decision
- Containment recommendation
- Business-impact assessment
- Lessons learned
- Detection improvements

# 16. Deployment sequence

## Stage 1 — Account and cost controls

1. Confirm Azure account eligibility.
2. Review available credits or trial access.
3. Create an Azure budget.
4. Configure cost alerts.
5. Define final resource naming conventions.

## Stage 2 — Azure foundation

1. Create the resource group.
2. Create the virtual network.
3. Create the user subnet.
4. Create the server subnet.
5. Create the network security group.
6. Create the storage account.
7. Create the Log Analytics workspace.
8. Create at least one virtual machine.
9. Configure VM auto-shutdown.
10. Create one Azure Monitor alert.
11. Demonstrate one RBAC assignment.

## Stage 3 — Sentinel foundation

1. Enable Microsoft Sentinel.
2. Confirm the correct Log Analytics workspace.
3. Review available data connectors.
4. Connect Azure Activity Logs.
5. Validate ingestion.
6. Save the first KQL validation queries.

## Stage 4 — Windows logging

1. Prepare the Windows endpoint.
2. Enable selected Windows auditing.
3. Install Sysmon.
4. Enable PowerShell logging.
5. Configure collection.
6. Generate known safe events.
7. Validate events in Sentinel.

## Stage 5 — Server and Linux logging

1. Prepare Windows Server.
2. Configure Active Directory where practical.
3. Create fictional users and groups.
4. Prepare the Ubuntu Linux server.
5. Connect Syslog.
6. Generate safe test events.
7. Validate ingestion.

## Stage 6 — Network detection

1. Install Suricata.
2. Confirm sensor placement.
3. Generate authorised test traffic.
4. Review local alerts.
5. Select the ingestion method.
6. Send selected evidence to Sentinel.
7. Validate queries and timestamps.

## Stage 7 — Optional integrations

1. Entra ID and Microsoft 365 connectors.
2. Defender XDR trial.
3. Zeek.
4. Splunk.
5. Additional Sigma or SPL detection conversions.

Optional integrations must not delay the core Sentinel environment.

# 17. Architecture acceptance criteria

The written architecture design is acceptable when:

- All required systems are identified.
- Every system has a clear purpose.
- Fictional and deployed assets are distinguished.
- User, server, administration, monitoring and testing zones are separated.
- Major trust boundaries are documented.
- Log sources are mapped to the monitoring platform.
- The four incidents have sufficient planned evidence.
- Sentinel is identified as the primary SIEM.
- Suricata is identified as the primary network IDS.
- Kali is restricted to the authorised laboratory.
- Cost controls are included.
- Licensing limitations are explained.
- The architecture can be converted into a clear diagram.

# 18. Known limitations

The initial architecture has the following limitations:

- It does not recreate 200 physical endpoints.
- Defender and Microsoft 365 access may depend on trial licensing.
- Azure resources may need to be reduced to control costs.
- Some telemetry may be simulated.
- The Suricata ingestion method is not yet confirmed.
- Actual Log Analytics table names may differ after deployment.
- Local and Azure laboratory components may not remain continuously connected.
- The environment is educational and not production-ready.
- Availability and disaster-recovery design are limited.
- Splunk and Zeek are optional rather than core requirements.

# 19. Architecture decision record

| Decision ID | Decision | Reason |
|---|---|---|
| ADR-001 | Use Microsoft Sentinel as the primary SIEM | Closely aligned with the target Microsoft Security Operations role |
| ADR-002 | Use KQL as the primary query language | Required for Sentinel monitoring, hunting and detection |
| ADR-003 | Use Sysmon for Windows endpoint visibility | Provides detailed process and network telemetry |
| ADR-004 | Use Suricata as the primary network IDS | Provides practical network detection and structured alert evidence |
| ADR-005 | Keep Zeek optional | Adds useful metadata but must not delay core work |
| ADR-006 | Keep Splunk secondary | Demonstrates transferable SIEM skills without diluting Microsoft focus |
| ADR-007 | Use representative laboratory systems | Controls cost and computing requirements |
| ADR-008 | Separate privileged administration | Reduces credential and lateral-movement risk |
| ADR-009 | Keep Kali isolated | Prevents unauthorised or accidental testing |
| ADR-010 | Validate one data source at a time | Simplifies troubleshooting and cost control |

# 20. Review requirements

This architecture design must be reviewed:

- After the version-one architecture diagram is created
- Before deploying Azure resources
- After actual subnet ranges are known
- After each major data source is connected
- Before every incident simulation
- After the tabletop exercise
- During the final portfolio review

Any significant change must also be reflected in:

- The asset inventory
- The network-zones document
- The security data-source register
- The architecture diagram
- The security-log data-flow diagram
- The success-metrics tracker
