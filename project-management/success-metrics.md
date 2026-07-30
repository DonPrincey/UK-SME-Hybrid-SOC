# Project Beacon Success Measurements

## Purpose

This document defines the measurable outcomes that will be used to
determine whether Project Beacon has successfully delivered its
technical, operational, incident-response and business objectives.

The project will not be considered complete solely because security
tools have been installed. Completion requires working evidence,
documented investigations, tested procedures and clear business
reporting.

## Measurement principles

Project Beacon will use the following principles:

- Every major deliverable must have visible evidence.
- Technical controls must be tested rather than merely configured.
- Important queries and detections must be documented.
- Incident investigations must follow a repeatable structure.
- Business impact must be explained alongside technical findings.
- Failures and limitations must be documented honestly.
- Public evidence must be sanitised before publication.

# 1. Project-governance measurements

| Measurement | Target | Evidence | Status |
|---|---:|---|---|
| Fictional organisation profile completed | 1 | `organisation-profile.md` | Complete |
| Project charter completed | 1 | `project-charter.md` | Complete |
| Stakeholder register completed | 1 | `stakeholder-register.md` | Complete |
| Risk register completed | 1 | `risk-register.md` | Complete |
| Success-measurement framework completed | 1 | `success-metrics.md` | Complete |
| RACI matrix completed | 1 | `raci-matrix.md` | Complete |
| Major project phases formally reviewed | 1 review per phase | Progress and review records | Not started |

# 2. Architecture measurements

| Measurement | Target | Evidence | Status |
|---|---:|---|---|
| Hybrid SOC architecture diagram | 1 | Architecture image and explanation | Not started |
| Security-log data-flow diagram | 1 | Log-flow image and explanation | Not started |
| Asset inventory | 1 complete inventory | `asset-inventory.md` | Not started |
| Security data-source register | 1 complete register | `data-source-register.md` | Not started |
| Trust boundaries identified | All major boundaries | Architecture documentation | Not started |
| Major systems labelled | 100% of in-scope systems | Architecture diagram | Not started |

## Required architecture components

The architecture must identify:

- Windows endpoint
- Windows Server
- Active Directory
- Microsoft Entra ID
- Microsoft Azure
- Microsoft Sentinel
- Log Analytics
- Linux server
- Sysmon
- Snort or Suricata
- Kali Linux testing machine
- Remote-access services
- Network zones
- Log sources
- Security-monitoring flow

# 3. Azure mini-lab measurements

| Measurement | Target | Evidence | Status |
|---|---:|---|---|
| Resource group created | 1 | Screenshot and configuration notes | Not started |
| Virtual network created | 1 | Screenshot and architecture record | Not started |
| Subnets created | 2 | Network configuration evidence | Not started |
| Network security group created | 1 | Rule and configuration evidence | Not started |
| Windows or Linux virtual machine deployed | At least 1 | VM evidence | Not started |
| Storage account created | 1 | Configuration evidence | Not started |
| Log Analytics workspace created | 1 | Workspace evidence | Not started |
| Azure Monitor alert created | At least 1 | Alert configuration evidence | Not started |
| RBAC assignment demonstrated | At least 1 | Role-assignment evidence | Not started |
| Cost controls configured | Budget and alert | Cost-management evidence | Not started |

# 4. Security-monitoring measurements

| Measurement | Target | Evidence | Status |
|---|---:|---|---|
| Microsoft Sentinel enabled | 1 environment | Sentinel screenshot and notes | Not started |
| Windows security telemetry documented | At least 1 source | Data-source record | Not started |
| Sysmon telemetry documented | At least 1 endpoint | Sysmon events and notes | Not started |
| Linux telemetry documented | At least 1 source | Syslog evidence | Not started |
| Network-security telemetry documented | At least 1 source | Snort or Suricata evidence | Not started |
| Identity telemetry documented | At least 1 source | Entra ID or equivalent evidence | Not started |
| Log timestamps validated | All active sources | Validation records | Not started |
| Data-ingestion failures documented | Every major failure | Troubleshooting notes | Not started |

# 5. KQL measurements

| Measurement | Target | Evidence | Status |
|---|---:|---|---|
| Documented KQL queries | At least 20 | Files in `kql/` | Not started |
| Authentication queries | At least 3 | KQL query files | Not started |
| Endpoint or process queries | At least 3 | KQL query files | Not started |
| Network queries | At least 2 | KQL query files | Not started |
| Privilege or lateral-movement queries | At least 3 | KQL query files | Not started |
| Data-staging or exfiltration queries | At least 2 | KQL query files | Not started |
| Time-window comparison query | At least 1 | Documented KQL query | Not started |
| Join or correlation query | At least 1 | Documented KQL query | Not started |
| MITRE ATT&CK mappings | All investigation queries where relevant | Query documentation | Not started |

## KQL documentation requirements

Every important query must contain:

- Query name
- Investigation purpose
- Required table or data source
- Complete KQL query
- Explanation of the logic
- Expected results
- Analyst interpretation
- MITRE ATT&CK mapping where relevant
- False-positive considerations
- Known limitations

# 6. Detection-engineering measurements

| Measurement | Target | Evidence | Status |
|---|---:|---|---|
| Documented detections | At least 4 | Detection files | Not started |
| Password-spraying detection | 1 | Detection documentation | Not started |
| Suspicious PowerShell detection | 1 | Detection documentation | Not started |
| Privilege or lateral-movement detection | 1 | Detection documentation | Not started |
| Data-staging or exfiltration detection | 1 | Detection documentation | Not started |
| MITRE ATT&CK mapping | 100% of core detections | Detection records | Not started |
| Severity assigned | 100% of core detections | Detection records | Not started |
| False positives considered | 100% of core detections | Tuning notes | Not started |
| Detection tuning recorded | At least 1 tuning record per detection | Detection records | Not started |
| Detection backlog maintained | 1 active backlog | Detection backlog file | Not started |

# 7. Incident-investigation measurements

Project Beacon will complete four simulated incidents:

1. Password spraying
2. Phishing followed by suspicious PowerShell
3. Privilege escalation and lateral movement
4. Data staging and attempted exfiltration

| Measurement | Target | Evidence | Status |
|---|---:|---|---|
| Complete simulated investigations | 4 | Incident folders | Not started |
| Incident tickets | 4 | Incident-ticket files | Not started |
| Investigation hypotheses | 4 | Investigation records | Not started |
| Evidence tables | 4 | Evidence files | Not started |
| Technical timelines | 4 | Timeline files | Not started |
| KQL or investigation queries | At least 1 set per incident | Query files | Not started |
| MITRE ATT&CK mappings | 4 complete mappings | Incident records | Not started |
| Severity decisions | 4 | Incident records | Not started |
| Containment recommendations | 4 | Incident records | Not started |
| Business-impact assessments | 4 | Incident records | Not started |
| Lessons-learned reviews | 4 | Incident records | Not started |
| Detection improvements | At least 1 per incident | Detection backlog | Not started |

## Required incident structure

Every incident must contain:

- Alert or detection source
- Incident ticket
- Initial investigation hypothesis
- Investigation questions
- Evidence table
- Login, process or network timeline
- Relevant queries
- Affected users, systems or data
- MITRE ATT&CK mapping
- Severity decision
- Containment recommendation
- Business-impact assessment
- Lessons learned
- Detection or process improvements

# 8. Incident-response measurements

| Measurement | Target | Evidence | Status |
|---|---:|---|---|
| Alert-severity matrix | 1 | Severity document | Not started |
| Incident-escalation procedure | 1 | Escalation document | Not started |
| Incident-response runbooks | At least 4 | Files in `runbooks/` | Not started |
| Compromised-account procedure | 1 | Runbook | Not started |
| Phishing-response procedure | 1 | Runbook | Not started |
| Suspicious PowerShell procedure | 1 | Runbook | Not started |
| Data-exfiltration procedure | 1 | Runbook | Not started |
| Decision owners identified | All major decisions | RACI and runbooks | Not started |
| Communication requirements documented | All severity levels | Escalation procedure | Not started |

# 9. Tabletop-exercise measurements

| Measurement | Target | Evidence | Status |
|---|---:|---|---|
| Tabletop scenario created | 1 | Scenario document | Not started |
| Participants recruited | At least 2 other people | Participant record | Not started |
| Exercise led by project owner | 1 completed session | Exercise record | Not started |
| Decisions recorded | All major decisions | Decision log | Not started |
| Technical and business issues discussed | Both categories | Exercise notes | Not started |
| Lessons learned documented | 1 report | Lessons-learned file | Not started |
| Response procedures improved | At least 2 improvements | Updated runbooks or escalation process | Not started |

# 10. Executive-reporting measurements

| Measurement | Target | Evidence | Status |
|---|---:|---|---|
| Executive incident briefing | 1 | Executive report | Not started |
| Post-incident review | 1 | Review document | Not started |
| SOC performance dashboard | 1 | Dashboard or report | Not started |
| Security-improvement roadmap | 1 | Prioritised roadmap | Not started |
| Business risks clearly explained | All major incidents | Executive reporting | Not started |
| Technical jargon reduced | All executive reports | Final review | Not started |
| Recommendations prioritised | High, medium and low priority | Improvement roadmap | Not started |

# 11. Portfolio-quality measurements

| Measurement | Target | Evidence | Status |
|---|---:|---|---|
| Public repository contains no secrets | 100% compliance | Secret and manual review | Ongoing |
| Screenshots sanitised | 100% compliance | Screenshot review | Ongoing |
| Professional commit messages used | 100% of major commits | Git history | Ongoing |
| Folder structure remains organised | All project phases | Repository review | Ongoing |
| Major files contain clear explanations | 100% of portfolio files | Documentation review | Ongoing |
| Broken links corrected | Zero known broken links | Final repository review | Not started |
| Final README explains the complete project | 1 complete README | Root `README.md` | Not started |
| Five-minute project explanation prepared | 1 presentation script | Interview material | Not started |
| Final Word report prepared | 1 | Word document | Not started |
| Final PDF portfolio report prepared | 1 | PDF document | Not started |

# 12. Completion definition

Project Beacon will be considered complete when:

1. All mandatory governance documents are complete.
2. Version one of the hybrid SOC architecture is published.
3. The Azure mini-lab has been built and documented.
4. Security telemetry from the selected sources has been analysed.
5. At least 20 KQL queries have been documented.
6. At least four core detections have been created.
7. Four complete incident investigations have been documented.
8. Incident-response runbooks and escalation procedures exist.
9. A multi-participant tabletop exercise has been completed.
10. Executive reports and an improvement roadmap have been produced.
11. Public evidence has been reviewed for sensitive information.
12. The project can be confidently explained during an interview.

## Review process

Success measurements will be reviewed:

- At the end of every project phase
- After each major technical deployment
- After every simulated incident
- After the tabletop exercise
- Before publishing the final portfolio
- Before using the project in job applications or interviews

Statuses will be updated using:

- **Not started**
- **In progress**
- **Blocked**
- **Complete**
- **Deferred**
