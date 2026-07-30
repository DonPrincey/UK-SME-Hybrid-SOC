# Project Beacon RACI Matrix

## Purpose

This RACI matrix defines responsibility, accountability, consultation
and communication requirements for the major activities within
Project Beacon.

It helps prevent confusion during security monitoring, incident
investigation, containment, recovery and business communication.

## RACI definitions

| Letter | Meaning | Explanation |
|---|---|---|
| R | Responsible | Performs or coordinates the activity |
| A | Accountable | Owns the final decision or outcome |
| C | Consulted | Provides advice, evidence or specialist input |
| I | Informed | Receives relevant updates |

## Roles

The following fictional roles are used:

- Executive Sponsor
- Project Lead / SOC Analyst
- IT Manager
- Systems Administrator
- Service Desk
- Data Protection and Compliance Representative
- Human Resources
- Department Manager
- External Technology Provider

## Project delivery RACI matrix

| Activity | Executive Sponsor | Project Lead / SOC Analyst | IT Manager | Systems Administrator | Service Desk | Compliance | HR | Department Manager | External Provider |
|---|---|---|---|---|---|---|---|---|---|
| Approve Project Beacon | A | R | C | I | I | C | I | I | I |
| Define business problem | C | R | A | C | C | C | I | C | I |
| Define project scope | C | R | A | C | I | C | I | I | I |
| Maintain project documentation | I | A/R | C | C | I | I | I | I | I |
| Maintain project risk register | C | A/R | C | C | I | C | I | I | I |
| Define project success measurements | C | R | A | C | I | C | I | I | I |
| Design SOC architecture | I | R | A | C | I | I | I | I | C |
| Approve major architecture decisions | I | R | A | C | I | C | I | I | C |
| Configure Azure resources | I | A | C | R | I | I | I | I | C |
| Configure Microsoft Sentinel | I | A/R | C | C | I | I | I | I | C |
| Configure log collection | I | A | C | R | I | I | I | I | C |
| Develop KQL queries | I | A/R | C | C | I | I | I | I | I |
| Develop detection rules | I | A/R | C | C | I | I | I | I | C |
| Maintain detection backlog | I | A/R | C | C | I | I | I | I | I |
| Produce executive reporting | I | R | C | C | I | C | I | I | I |
| Approve improvement roadmap | A | R | C | C | I | C | I | C | I |

## Security incident RACI matrix

| Incident activity | Executive Sponsor | Project Lead / SOC Analyst | IT Manager | Systems Administrator | Service Desk | Compliance | HR | Department Manager | External Provider |
|---|---|---|---|---|---|---|---|---|---|
| Receive user security report | I | C | I | I | A/R | I | I | I | I |
| Triage security alert | I | A/R | C | C | C | I | I | I | I |
| Open incident ticket | I | A/R | I | I | C | I | I | I | I |
| Define investigation hypothesis | I | A/R | C | C | I | I | I | I | I |
| Gather technical evidence | I | A | C | R | C | I | I | I | C |
| Build incident timeline | I | A/R | C | C | I | I | I | I | C |
| Determine incident severity | I | R | A | C | C | C | I | C | I |
| Assess business impact | C | R | A | C | I | C | C | R | I |
| Assess data-protection impact | I | C | C | I | I | A/R | C | I | I |
| Disable compromised user account | I | R | A | R | C | C | I | I | I |
| Isolate affected endpoint | I | R | A | R | C | I | I | C | C |
| Block malicious IP or domain | I | R | A | R | I | I | I | I | C |
| Approve high-impact containment | A | R | R | C | I | C | I | C | I |
| Preserve evidence | I | A | C | R | I | C | I | I | C |
| Communicate with affected employees | I | C | A | I | R | C | C | C | I |
| Communicate with customers | A | C | C | I | I | C | I | C | I |
| Contact external provider | I | C | A | R | I | I | I | I | R |
| Recover affected systems | I | C | A | R | I | I | I | C | C |
| Validate recovery | I | R | A | R | C | I | I | C | C |
| Close incident ticket | I | A/R | C | C | C | C | I | I | I |
| Conduct lessons-learned review | C | A/R | C | C | C | C | C | C | C |
| Update detections and runbooks | I | A/R | C | C | C | C | I | I | C |

## Scenario-specific accountability

### Password-spraying incident

- The SOC Analyst investigates failed sign-in patterns.
- The IT Manager approves high-impact account restrictions.
- The Systems Administrator disables or resets compromised accounts.
- Compliance is consulted if sensitive data may have been accessed.

### Phishing and suspicious PowerShell

- The Service Desk receives and records the initial user report.
- The SOC Analyst analyses email, process and endpoint evidence.
- The Systems Administrator isolates the affected endpoint.
- Human Resources is consulted if employee conduct becomes relevant.

### Privilege escalation and lateral movement

- The SOC Analyst identifies affected users, devices and systems.
- The IT Manager approves major containment actions.
- The Systems Administrator restricts privileged accounts and systems.
- The Executive Sponsor is informed if critical services are affected.

### Data staging and attempted exfiltration

- The SOC Analyst identifies staged files, destinations and affected data.
- Compliance assesses privacy and reporting obligations.
- The IT Manager coordinates technical containment.
- The Executive Sponsor approves external or customer communication.

## RACI operating rules

Project Beacon will use these rules:

1. Every major activity must have at least one responsible role.
2. Every major activity should have only one clearly accountable role.
3. Accountable roles may delegate work but retain ownership.
4. Consulted stakeholders should be involved before important decisions.
5. Informed stakeholders should receive relevant and timely updates.
6. High-impact containment requires business and technical coordination.
7. Compliance must be consulted when personal or customer data may be affected.
8. All significant decisions must be recorded in the incident documentation.

## Review requirements

The RACI matrix will be reviewed:

- At the end of the project-leadership phase
- After the architecture is designed
- Before the first incident simulation
- After the tabletop exercise
- Whenever responsibilities or escalation procedures change
