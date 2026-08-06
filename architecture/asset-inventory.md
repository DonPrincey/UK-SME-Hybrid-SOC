# Project Beacon Asset Inventory

## Purpose

This document identifies the systems, services, identities, security
tools and information assets included in the Project Beacon hybrid SOC
environment.

**## Asset identification standard

Every important asset will use a consistent identifier.

| Asset category | Identifier format | Example |
|---|---|---|
| User group | `USR-GRP-###` | `USR-GRP-001` |
| Identity platform | `IDP-###` | `IDP-001` |
| Windows endpoint group | `WIN-END-###` | `WIN-END-001` |
| Server | `SRV-###` | `SRV-001` |
| Cloud service | `CLD-###` | `CLD-001` |
| Security tool | `SEC-###` | `SEC-001` |
| Network asset | `NET-###` | `NET-001` |
| Information asset | `DATA-###` | `DATA-001` |

Asset identifiers will be used consistently in diagrams, investigations,
risk assessments and incident reports.

# 1. User groups

Beacon Professional Services Ltd has approximately 200 employees.

The following user groups represent the main types of people who access
the organisation's systems and information.

| Asset ID | User group | Approximate number | Access requirements | Security relevance | Criticality |
|---|---|---:|---|---|---|
| USR-GRP-001 | General office employees | 80 | Microsoft 365, email, shared files and business applications | Common phishing targets and possible source of compromised accounts | Medium |
| USR-GRP-002 | Hybrid and remote employees | 60 | Microsoft 365, VPN, remote access and cloud applications | Increased exposure to credential theft and unauthorised remote access | High |
| USR-GRP-003 | Customer-account personnel | 20 | Customer records, email, contracts and account-management systems | Access to customer information makes compromised accounts high impact | High |
| USR-GRP-004 | Project and technical teams | 20 | Project files, technical systems, shared storage and collaboration tools | May access commercially sensitive files and technical environments | High |
| USR-GRP-005 | Service Desk personnel | 8 | Help-desk platform, remote-support tools and limited account-management functions | Could be targeted for password resets, social engineering or remote-access misuse | High |
| USR-GRP-006 | Systems administrators | 4 | Servers, Active Directory, Azure, endpoints and privileged tools | Privileged accounts could enable lateral movement and widespread compromise | Critical |
| USR-GRP-007 | Managers and executives | 8 | Financial information, contracts, email and sensitive business documents | High-value phishing and business-email-compromise targets | Critical |

## User security considerations

The most significant user-related risks include:

- Phishing and credential theft
- Password spraying
- Weak or reused passwords
- Session-token theft
- Unauthorised remote access
- Abuse of privileged accounts
- Accidental disclosure of customer or employee information
- Social engineering of Service Desk personnel
- Compromise of executive email accounts

# 2. Identity and access assets

| Asset ID | Asset name | Asset type | Purpose | Important logs or evidence | Criticality |
|---|---|---|---|---|---|
| IDP-001 | Microsoft Entra ID | Cloud identity platform | Authenticates users to Microsoft 365, Azure and selected cloud applications | Sign-in logs, audit logs, risky sign-ins and authentication failures | Critical |
| IDP-002 | Active Directory Domain Services | On-premises identity platform | Manages domain users, computers, groups and access to internal systems | Security events, account changes, Kerberos events and group-membership changes | Critical |
| IDP-003 | Multi-factor authentication | Identity security control | Adds an additional authentication requirement for selected users and services | MFA success, failure and challenge records | High |
| IDP-004 | Role-based access control | Access-control mechanism | Restricts Azure and administrative permissions according to assigned roles | Role assignments, activity logs and permission changes | High |
| IDP-005 | Privileged administrator accounts | Privileged identities | Manage Active Directory, Azure, servers and security tools | Privileged logons, account changes, role changes and administrative actions | Critical |
| IDP-006 | Standard employee accounts | User identities | Provide day-to-day access to email, documents and business services | Successful and failed sign-ins, lockouts and unusual access | High |
| IDP-007 | Service accounts | Non-human identities | Support scheduled tasks, applications and internal services | Service logons, authentication failures and permission use | High |

## Identity monitoring priorities

Project Beacon will prioritise monitoring for:

- Repeated failed sign-ins across multiple accounts
- One password attempted against many users
- Successful logins after repeated failures
- Sign-ins from unusual locations or IP addresses
- New privileged-role assignments
- Addition of users to privileged groups
- Disabled security controls
- Unexpected service-account activity
- Privileged logons outside expected working patterns
- Authentication activity followed by suspicious endpoint behaviour

# 3. Windows endpoint assets

Beacon employees primarily use managed Windows laptops and desktops.

For the portfolio environment, these devices are represented as logical
asset groups rather than 200 individually created machines.

| Asset ID | Asset name | Operating system | Approximate quantity | Primary users | Monitoring source | Criticality |
|---|---|---|---:|---|---|---|
| WIN-END-001 | Office employee endpoints | Windows 11 | 80 | General office employees | Windows Security Events and Sysmon | Medium |
| WIN-END-002 | Hybrid and remote endpoints | Windows 11 | 60 | Hybrid and remote employees | Windows Security Events, Sysmon and VPN evidence | High |
| WIN-END-003 | Customer-account endpoints | Windows 11 | 20 | Customer-account personnel | Windows Security Events and Sysmon | High |
| WIN-END-004 | Technical-team endpoints | Windows 11 | 20 | Project and technical personnel | Windows Security Events, Sysmon and PowerShell logs | High |
| WIN-END-005 | Service Desk endpoints | Windows 11 | 8 | Service Desk personnel | Windows Security Events, Sysmon and remote-support logs | High |
| WIN-END-006 | Administrator workstations | Windows 11 | 4 | Systems administrators | Windows Security Events, Sysmon, PowerShell and privileged-logon events | Critical |
| WIN-END-007 | Executive endpoints | Windows 11 | 8 | Managers and executives | Windows Security Events and Sysmon | Critical |

## Planned laboratory endpoint

The practical lab will not recreate all 200 employee endpoints.

It will use a smaller representative endpoint:

| Asset ID | Asset name | Purpose | Planned configuration | Criticality |
|---|---|---|---|---|
| WIN-END-LAB-001 | Beacon Windows test endpoint | Represents a Beacon employee workstation during monitoring and incident simulations | Windows, Sysmon, PowerShell logging and security-event collection | High |

This endpoint may be used to simulate:

- User logons
- Failed authentication attempts
- Suspicious PowerShell execution
- Process creation
- Network connections
- File creation or staging
- Privilege-related activity
- Endpoint isolation and investigation procedures

## Windows endpoint monitoring priorities

The SOC will prioritise:

- Process creation
- PowerShell execution
- Suspicious parent-child process relationships
- New services
- Scheduled tasks
- Local account changes
- Privileged logons
- Remote logons
- Network connections
- File creation in unusual locations
- Security-control changes
- Evidence of credential access or lateral movement**


# 4. Server assets

Beacon Professional Services Ltd uses Windows and Linux servers to
provide identity, file-storage, application and technical services.

The fictional business environment contains several logical server
assets. The practical laboratory will recreate only a small
representative selection.

| Asset ID | Asset name | Platform | Primary purpose | Environment | Important evidence | Criticality |
|---|---|---|---|---|---|---|
| SRV-001 | BEACON-DC01 | Windows Server | Active Directory Domain Services and DNS | Fictional business environment | Authentication events, account changes, Kerberos events, group changes and administrative activity | Critical |
| SRV-002 | BEACON-FS01 | Windows Server | Stores departmental, customer and project files | Fictional business environment | File access, permission changes, failed access, file creation and large-volume copying | Critical |
| SRV-003 | BEACON-APP01 | Windows Server | Hosts selected internal business applications | Fictional business environment | Application logs, service events, logons and process activity | High |
| SRV-004 | BEACON-LNX01 | Ubuntu Linux Server | Supports selected technical or internal services | Fictional business environment | Syslog, authentication, process, service and network-connection logs | High |
| SRV-LAB-001 | Beacon Windows Server laboratory system | Windows Server evaluation | Represents Active Directory, DNS and Windows server activity in the controlled lab | Planned laboratory | Windows Security Events, PowerShell logs and Sysmon where appropriate | Critical |
| SRV-LAB-002 | Beacon Linux laboratory server | Ubuntu Linux | Generates Linux authentication, process and network telemetry | Planned laboratory | Syslog, authentication logs, service logs and network evidence | High |

## Server monitoring priorities

Project Beacon will prioritise monitoring for:

- Successful and failed administrative logons
- Creation, deletion and modification of user accounts
- Addition of users to privileged groups
- Kerberos and authentication anomalies
- New or modified services
- Scheduled-task creation
- Suspicious PowerShell activity
- Remote desktop and remote-management activity
- File permission changes
- Unusually large file access or copying
- Linux SSH authentication activity
- Use of elevated privileges
- Unexpected outbound network connections
- Security-log clearing or monitoring disruption

## Laboratory limitation

The laboratory will not recreate every fictional production server.

The minimum planned server representation is:

- One Windows Server evaluation system
- One Windows employee test endpoint
- One Linux server or Linux security-monitoring system

Additional systems will be added only where they provide meaningful
monitoring or incident-investigation evidence.

# 5. Microsoft 365 and Azure assets

Beacon relies on Microsoft cloud services for identity, communication,
collaboration, file storage and security monitoring.

| Asset ID | Asset name | Service type | Primary purpose | Environment | Important evidence | Criticality |
|---|---|---|---|---|---|---|
| CLD-001 | Microsoft 365 tenant | Cloud productivity platform | Provides organisational email, collaboration and cloud services | Fictional business environment / trial where available | User activity, email events, audit records and authentication evidence | Critical |
| CLD-002 | Exchange Online | Cloud email service | Provides employee and business email | Fictional business environment / trial where available | Mailbox activity, forwarding rules, suspicious messages and email audit events | Critical |
| CLD-003 | SharePoint Online | Cloud document platform | Stores shared departmental and project documents | Fictional business environment / trial where available | File access, sharing, downloading and permission changes | High |
| CLD-004 | OneDrive for Business | User cloud storage | Stores and synchronises individual employee files | Fictional business environment / trial where available | File access, sharing, synchronisation and large-volume downloads | High |
| CLD-005 | Microsoft Teams | Collaboration platform | Supports messaging, meetings and file collaboration | Fictional business environment / trial where available | User activity, file-sharing and audit events | Medium |
| CLD-006 | Microsoft Azure subscription | Cloud platform | Hosts the Project Beacon Azure mini-lab and security services | Planned laboratory | Azure Activity Logs, resource changes, role assignments and sign-in activity | Critical |
| CLD-007 | Beacon Azure resource group | Azure management container | Organises the project’s Azure laboratory resources | Planned laboratory | Resource creation, deletion and configuration changes | High |
| CLD-008 | Beacon virtual network | Azure networking service | Provides network segmentation for the Azure laboratory | Planned laboratory | Network configuration, NSG activity and traffic evidence | High |
| CLD-009 | Azure storage account | Cloud storage service | Demonstrates storage configuration, access and monitoring | Planned laboratory | Access records, configuration changes and security alerts | High |
| CLD-010 | Log Analytics workspace | Security-data platform | Stores and queries logs used by Microsoft Sentinel | Planned laboratory | Ingestion status, table contents, query results and retention settings | Critical |

## Cloud monitoring priorities

Project Beacon will monitor or document:

- Unusual sign-in activity
- Authentication failures
- Risky or unexpected locations
- Mailbox forwarding-rule creation
- Unusual email access
- Large file downloads
- External file sharing
- Privileged-role assignments
- Azure resource creation or deletion
- Changes to networking and security controls
- Storage-account access
- Log-ingestion failures
- Attempts to disable or reduce monitoring

## Cloud-lab distinction

Assets marked as part of the fictional business environment represent
Beacon's intended operational environment.

Assets marked as planned laboratory resources will be created only
where trial access, licensing and cost controls permit.

The repository will clearly distinguish between:

- Fictional business assets
- Planned laboratory assets
- Successfully deployed laboratory assets
- Simulated or dataset-based evidence

# 6. Information assets

Beacon stores customer, employee, contractual, financial and technical
information.

These information assets explain why the organisation is a realistic
target for phishing, account compromise, privilege escalation and data
exfiltration.

| Asset ID | Information asset | Classification | Likely location | Business owner | Security relevance | Criticality |
|---|---|---|---|---|---|---|
| DATA-001 | Customer records | Restricted | Customer systems, SharePoint and business applications | Customer Account Manager | Exposure could harm customers and create contractual or regulatory consequences | Critical |
| DATA-002 | Employee personal information | Restricted | Human Resources systems and protected file storage | Human Resources | Exposure could affect employee privacy and data-protection responsibilities | Critical |
| DATA-003 | Commercial contracts | Confidential | SharePoint, file server and management storage | Executive Leadership | May contain pricing, obligations and commercially sensitive information | High |
| DATA-004 | Financial information | Restricted | Finance systems, protected files and executive storage | Finance Manager | Theft or manipulation could cause direct financial and reputational damage | Critical |
| DATA-005 | Microsoft 365 email | Confidential | Exchange Online | Department Managers | Compromised mailboxes may expose business information or enable further phishing | High |
| DATA-006 | Project and technical files | Confidential | SharePoint, OneDrive and file server | Project Managers | May contain client information, designs, technical details and business plans | High |
| DATA-007 | Help-desk records | Internal or confidential | Service-management platform | IT Manager | May expose user problems, device information and account-support activity | High |
| DATA-008 | Security logs and incident evidence | Restricted | Log Analytics, Sentinel and investigation records | Project Lead / SOC Analyst | Evidence must remain accurate, available and protected from unauthorised alteration | Critical |
| DATA-009 | System configuration information | Restricted | Administrative systems and protected documentation | Systems Administrator | Could assist attackers in identifying systems, accounts and security weaknesses | Critical |
| DATA-010 | Backup and recovery information | Restricted | Protected backup locations | IT Manager | Compromise could prevent recovery or support destructive attacks | Critical |

## Data-protection priorities

The project will prioritise:

- Confidentiality of customer and employee information
- Integrity of security logs and incident evidence
- Protection of financial and contractual information
- Monitoring of unusual access and file downloads
- Restriction of privileged access
- Protection against unauthorised sharing
- Identification of large-volume file copying
- Preservation of evidence during investigations
- Sanitisation of all public portfolio material

## Data-handling boundary

Project Beacon will not use genuine customer, employee or employer data.

All records used in demonstrations will be:

- Fictional
- Sanitised
- Safely simulated
- Generated within the authorised laboratory
- Obtained from approved public security datasets where necessary
