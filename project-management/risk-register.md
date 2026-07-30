# Project Beacon Risk Register

## Purpose

This risk register identifies technical, operational, financial,
security and project-delivery risks that could affect Project Beacon.

Each risk is assessed using likelihood and impact scores. Mitigation
actions are assigned to reduce either the probability of the risk
occurring or the damage it could cause.

## Risk-scoring method

- **Likelihood:** 1 to 5
- **Impact:** 1 to 5
- **Risk score:** Likelihood × Impact

| Score | Rating | Required response |
|---:|---|---|
| 1–4 | Low | Monitor and manage through normal controls |
| 5–9 | Medium | Assign mitigation and review regularly |
| 10–15 | High | Prioritise mitigation and track closely |
| 16–25 | Critical | Immediate action and senior oversight required |

## Risk register

| ID | Category | Risk description | Likelihood | Impact | Score | Rating | Mitigation | Owner | Status |
|---|---|---|---:|---:|---:|---|---|---|---|
| R-001 | Financial | Azure resources could create unexpected charges if services are left running or incorrectly configured. | 3 | 4 | 12 | High | Create budgets and cost alerts, use low-cost resources and remove unused services after testing. | Project Lead | Open |
| R-002 | Information security | Passwords, API keys, access tokens or connection details could accidentally be committed to the public GitHub repository. | 2 | 5 | 10 | High | Use secret scanning, `.gitignore`, environment variables and a pre-commit review checklist. | Project Lead | Open |
| R-003 | Privacy | Screenshots could expose email addresses, account identifiers, IP addresses or other personal information. | 3 | 5 | 15 | High | Review, crop and sanitise every screenshot before publication. | Project Lead | Open |
| R-004 | Technical | Windows, Linux, Sysmon or network logs may fail to reach Log Analytics or Microsoft Sentinel. | 3 | 4 | 12 | High | Configure and test one data source at a time, validate timestamps and document troubleshooting steps. | Project Lead / Systems Administrator | Open |
| R-005 | Licensing | Microsoft Sentinel, Defender or Entra features may be unavailable because of trial or licence restrictions. | 4 | 3 | 12 | High | Prioritise available features, use safe simulations and document licence-related limitations honestly. | Project Lead | Open |
| R-006 | Resources | The local computer may lack enough memory, storage or processing power to run several virtual machines simultaneously. | 3 | 3 | 9 | Medium | Use lightweight systems, limit concurrent virtual machines and create checkpoints before major changes. | Project Lead | Open |
| R-007 | Scope | The project could become too large because it combines Azure, Sentinel, KQL, endpoints, networking, incidents and reporting. | 4 | 4 | 16 | Critical | Follow the approved scope, complete one phase at a time and prioritise required deliverables. | Project Lead | Open |
| R-008 | Schedule | Certification study, applications and other responsibilities could delay project milestones. | 4 | 3 | 12 | High | Use weekly time blocks, maintain a progress tracker and move incomplete tasks into the next planned session. | Project Lead | Open |
| R-009 | Documentation | Technical work may be completed without sufficient evidence, explanations or screenshots. | 4 | 3 | 12 | High | Document each lab during the session and commit evidence before starting the next task. | Project Lead | Open |
| R-010 | Detection quality | Detection rules could create excessive false positives or miss important activity. | 3 | 4 | 12 | High | Test against expected and benign activity, document limitations and maintain tuning records. | Project Lead / SOC Analyst | Open |
| R-011 | Incident realism | Simulated incidents may not resemble realistic SOC investigations closely enough. | 3 | 3 | 9 | Medium | Use realistic attack behaviours, MITRE ATT&CK mappings, evidence timelines and business context. | Project Lead / SOC Analyst | Open |
| R-012 | Unauthorised activity | Testing could accidentally target systems outside the authorised laboratory environment. | 2 | 5 | 10 | High | Use isolated lab networks, verify target addresses and document the authorised testing boundary. | Project Lead | Open |
| R-013 | Data loss | Virtual-machine files, queries, screenshots or reports could be lost through failure or accidental deletion. | 2 | 4 | 8 | Medium | Use GitHub version control, local backups and virtual-machine snapshots. | Project Lead | Open |
| R-014 | Misrepresentation | Portfolio work could be incorrectly described as paid employment or production SOC experience. | 2 | 5 | 10 | High | Clearly label the work as a personal authorised laboratory and fictional-organisation project. | Project Lead | Open |
| R-015 | Business continuity | Containment actions in a real organisation could interrupt essential services. | 3 | 5 | 15 | High | Require approval for high-impact actions and document safer alternatives, rollback plans and business effects. | IT Manager | Open |
| R-016 | Compliance | A security incident involving customer or employee information may not be escalated to the appropriate privacy or compliance stakeholder. | 3 | 5 | 15 | High | Include compliance assessment in the escalation process and incident-response runbooks. | Compliance Representative | Open |

## Highest-priority risks

The initial highest-priority risks are:

1. **R-007 — Project scope expansion**
2. **R-003 — Exposure of sensitive information in screenshots**
3. **R-015 — Business disruption caused by containment**
4. **R-016 — Failure to escalate data-protection concerns**
5. **R-001 — Unexpected Azure charges**

These risks require active monitoring throughout the project.

## Risk-management process

Project Beacon will use the following process:

1. Identify new risks during each project phase.
2. Assign likelihood and impact scores.
3. Calculate and record the risk rating.
4. Assign a risk owner.
5. Define mitigation actions.
6. Review high and critical risks before major technical changes.
7. Update the status after controls are implemented.
8. Record any risks that become actual issues.

## Risk statuses

The following statuses will be used:

- **Open:** Risk identified but mitigation is incomplete
- **Mitigation in progress:** Controls are currently being implemented
- **Monitoring:** Controls exist, but the risk remains under observation
- **Closed:** Risk has been adequately addressed
- **Accepted:** The remaining risk has been acknowledged and accepted

## Review schedule

The risk register will be reviewed:

- At the end of every major project phase
- Before creating paid Azure resources
- Before publishing screenshots or technical evidence
- Before conducting incident simulations
- After the tabletop exercise
- During the final portfolio review
