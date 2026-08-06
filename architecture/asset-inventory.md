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
