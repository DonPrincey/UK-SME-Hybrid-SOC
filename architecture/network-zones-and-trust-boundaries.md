# Project Beacon Network Zones and Trust Boundaries

## Purpose

This document defines the logical network zones, trust boundaries and
permitted communication paths for Project Beacon.

The design separates users, servers, administrative systems, security
monitoring services, cloud resources and authorised testing systems.

The objective is to reduce unnecessary access, improve monitoring and
limit the potential impact of compromised accounts or devices.

# 1. Network design principles

Project Beacon follows these principles:

- No system is trusted solely because it is inside the network.
- Users receive only the access needed for their responsibilities.
- Administrative systems are separated from ordinary user systems.
- Servers are placed in restricted network zones.
- Security-monitoring systems receive logs without providing unnecessary
  access back into monitored systems.
- Remote access requires authenticated and controlled entry.
- The Kali testing machine remains inside an authorised laboratory zone.
- Communication between zones is restricted and monitored.
- High-risk changes require approval and documentation.
- All public portfolio information must remain sanitised.

# 2. Logical network zones

| Zone ID | Zone name | Main assets | Trust level | Main security purpose |
|---|---|---|---|---|
| ZONE-001 | Internet / external zone | Public internet, external IP addresses and external services | Untrusted | Represents traffic and services outside Beacon's control |
| ZONE-002 | Remote-access zone | Remote employees, VPN entry point and remote authentication services | Partially trusted | Controls access from remote users into Beacon services |
| ZONE-003 | Corporate user zone | Standard Windows employee endpoints | Standard trust | Supports normal employee access to business services |
| ZONE-004 | Privileged administration zone | Administrator workstations and privileged accounts | Highly restricted | Protects administrative activity and high-impact credentials |
| ZONE-005 | Server zone | Active Directory, DNS, file and application servers | Restricted | Protects critical identity and business services |
| ZONE-006 | Security-monitoring zone | Sentinel, Log Analytics, Suricata, Zeek and analyst systems | Restricted | Centralises and analyses security evidence |
| ZONE-007 | Azure cloud zone | Azure virtual network, subnets, VM, storage and monitoring services | Restricted cloud environment | Hosts the planned Azure mini-lab |
| ZONE-008 | Microsoft cloud services zone | Entra ID, Microsoft 365, Exchange, SharePoint and OneDrive | Externally managed trusted service | Provides cloud identity, email and collaboration |
| ZONE-009 | Authorised laboratory zone | Kali Linux, test endpoint and laboratory servers | Isolated and controlled | Generates safe security events and attack simulations |
| ZONE-010 | Management plane | Azure portal, administrative consoles and configuration interfaces | Highly restricted | Controls high-impact system and cloud configuration |

# 3. Planned laboratory network ranges

The following private ranges are reserved for documentation and planned
laboratory use.

| Network | Planned range | Purpose |
|---|---|---|
| Azure virtual network | `10.20.0.0/16` | Overall Azure Project Beacon network |
| Azure user subnet | `10.20.10.0/24` | Representative endpoint systems |
| Azure server subnet | `10.20.20.0/24` | Server or monitoring systems |
| Azure management subnet | `10.20.30.0/24` | Administrative services where required |
| Local isolated lab | `192.168.50.0/24` | Local authorised VirtualBox or equivalent lab |
| Security-monitoring segment | `192.168.60.0/24` | Suricata, Zeek or monitoring systems where separated |

These ranges are planned documentation values.

Actual deployed addresses must be recorded after the laboratory is
created.

# 4. Trust boundaries

A trust boundary exists where users, systems or data move between areas
with different trust levels.

## TB-001 — Internet to Beacon services

**Boundary:**

```text
Internet → Firewall, VPN or Microsoft cloud service
```

**Primary risks:**

- Password spraying
- Phishing
- Malicious connections
- Exploitation attempts
- Command-and-control traffic
- Data exfiltration

**Required controls:**

- Firewall and network-security rules
- Multi-factor authentication
- VPN authentication
- Sign-in monitoring
- Suricata or equivalent network monitoring
- Blocking and alerting for suspicious indicators

## TB-002 — Remote users to internal or cloud services

**Boundary:**

```text
Remote employee → VPN or cloud authentication → Beacon resources
```

**Primary risks:**

- Stolen credentials
- Compromised personal or remote devices
- Unusual geographic sign-ins
- Session-token theft
- Unauthorised remote access

**Required controls:**

- MFA
- Entra ID sign-in monitoring
- VPN logging
- Device and account verification
- Conditional Access where licensing permits
- Least-privilege access

## TB-003 — Corporate user zone to server zone

**Boundary:**

```text
Employee endpoint → File, application, identity or technical server
```

**Primary risks:**

- Lateral movement
- Credential theft
- Unauthorised file access
- Malware propagation
- Privilege escalation

**Required controls:**

- Network segmentation
- Restricted administrative ports
- Windows authentication logging
- Sysmon
- File-access monitoring
- Firewall or NSG rules
- Privileged-access controls

## TB-004 — Standard user zone to privileged administration zone

**Boundary:**

```text
Standard employee systems → Administrative systems and credentials
```

**Primary risks:**

- Theft of privileged credentials
- Abuse of administrator sessions
- Pass-the-hash or similar credential misuse
- Unauthorised configuration changes

**Required controls:**

- Separate administrator accounts
- Dedicated administrator workstation
- Restricted logon rights
- Privileged logon monitoring
- MFA where supported
- No normal email or web browsing using privileged accounts

## TB-005 — On-premises environment to Azure

**Boundary:**

```text
Local or simulated Beacon environment → Azure virtual network and services
```

**Primary risks:**

- Incorrect network configuration
- Overly permissive security rules
- Exposed cloud services
- Unauthorised resource changes
- Compromised credentials

**Required controls:**

- Network security groups
- RBAC
- Azure Activity Logs
- Cost and configuration alerts
- Restricted management access
- Documented resource ownership

## TB-006 — Beacon identities to Microsoft 365 services

**Boundary:**

```text
Entra ID account → Exchange, SharePoint, OneDrive or Teams
```

**Primary risks:**

- Mailbox compromise
- Malicious forwarding rules
- Unauthorised file sharing
- Large downloads
- Business-email compromise

**Required controls:**

- MFA
- Sign-in and audit logging
- Role restrictions
- Mailbox and file-activity monitoring
- Approved external-sharing settings
- Incident escalation for compromised accounts

## TB-007 — Monitored systems to security-monitoring zone

**Boundary:**

```text
Endpoints, servers, identities and network sensors → Log Analytics/Sentinel
```

**Primary risks:**

- Missing logs
- Altered evidence
- Incorrect timestamps
- Excessive log volume
- Monitoring interruption

**Required controls:**

- Validated log connectors
- Time synchronisation
- Restricted access to security logs
- Ingestion monitoring
- Data-source health checks
- Evidence-integrity procedures

## TB-008 — Authorised laboratory zone to monitored systems

**Boundary:**

```text
Kali testing machine → Authorised Windows/Linux laboratory targets
```

**Primary risks:**

- Testing the wrong target
- Escaping the isolated laboratory
- Generating uncontrolled traffic
- Accidental access to unrelated systems

**Required controls:**

- Isolated private network
- Verified target IP addresses
- Written testing boundary
- Controlled fictional accounts
- Ability to stop activity immediately
- No public or third-party targets

## TB-009 — Security analyst to monitoring and evidence systems

**Boundary:**

```text
SOC analyst workstation → Sentinel, logs, incident records and GitHub evidence
```

**Primary risks:**

- Unauthorised evidence changes
- Exposure of personal information
- Accidental publication of secrets
- Incorrect incident conclusions

**Required controls:**

- Restricted analyst access
- Version control
- Sanitisation checks
- Query and evidence documentation
- Separation of facts, assumptions and conclusions

# 5. Permitted communication matrix

| Source zone | Destination zone | Purpose | Expected access | Monitoring requirement |
|---|---|---|---|---|
| Internet | Remote-access zone | VPN or authenticated remote access | Restricted | Authentication and firewall logs |
| Internet | Microsoft cloud services | Microsoft 365 and Entra access | Approved secure services only | Sign-in and audit logs |
| Remote-access zone | Corporate user services | Remote employee work | Authenticated and restricted | VPN, identity and endpoint logs |
| Corporate user zone | Server zone | Business applications, files and authentication | Required ports only | Windows, Sysmon and network evidence |
| Privileged administration zone | Server zone | Authorised administration | Restricted administrative protocols | Privileged logons and process activity |
| Server zone | Security-monitoring zone | Security-log forwarding | Outbound log delivery | Ingestion and source-health monitoring |
| Corporate user zone | Security-monitoring zone | Endpoint-log forwarding | Outbound log delivery | Sysmon and Windows event validation |
| Azure cloud zone | Security-monitoring zone | Azure activity and resource logs | Approved connector access | Azure and Sentinel monitoring |
| Microsoft cloud services | Security-monitoring zone | Identity and service audit logs | Approved connector access | Connector-health monitoring |
| Authorised laboratory zone | Laboratory targets | Controlled simulations | Approved test traffic only | Suricata, Sysmon and packet evidence |
| Security analyst workstation | Security-monitoring zone | Investigation and query access | Authenticated analyst access | Audit and investigation records |

# 6. Prohibited or restricted communication

The following communication must be blocked or tightly restricted:

- Direct internet access to internal administrative services
- Standard employee access to domain-controller administration
- Kali access to public or unrelated systems
- Unrestricted user-to-server administrative protocols
- Unauthorised traffic between user and server subnets
- Public access to Log Analytics or incident evidence
- Unapproved external sharing of sensitive business data
- Normal user accounts performing privileged administrative actions
- Security tools accepting unnecessary inbound connections
- Credentials or secrets being transferred into the public repository

# 7. Monitoring points

Security monitoring should be positioned at:

1. Internet and firewall boundary
2. VPN and remote-access entry point
3. Entra ID and Microsoft 365 authentication layer
4. Windows endpoints using Security Events and Sysmon
5. Active Directory and Windows Server systems
6. Linux authentication and system logs
7. User-to-server network boundary
8. Azure Activity Logs and resource configuration
9. Suricata network sensor
10. Log Analytics and Microsoft Sentinel ingestion layer

# 8. Initial architecture decisions

Project Beacon adopts the following initial decisions:

- Microsoft Sentinel will be the primary SIEM.
- Log Analytics will hold the primary Microsoft security telemetry.
- Sysmon will provide detailed Windows endpoint telemetry.
- Suricata will be the primary network IDS.
- Zeek will be an optional network-metadata extension.
- Splunk will remain an optional secondary SIEM exercise.
- Active Directory and Entra ID will represent hybrid identity.
- The Kali system will remain inside the authorised laboratory zone.
- The practical lab will use representative systems rather than 200 machines.
- High-impact administrative access will be separated from normal user activity.

# 9. Review and update requirements

This document must be updated when:

- The final architecture diagram is created
- Actual subnet ranges are deployed
- A new data source is connected
- A tool is added or deferred
- Firewall or NSG rules are changed
- An incident reveals an unexpected communication path
- The tabletop exercise identifies a responsibility or access gap
