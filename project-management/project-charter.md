# Project Beacon Charter

## Hybrid SOC and Incident Response Programme for a UK SME

## Project information

- **Project name:** Project Beacon
- **Full project title:** Hybrid SOC and Incident Response Programme for a UK SME
- **Fictional organisation:** Beacon Professional Services Ltd
- **Project owner:** Princewill Nwanguma
- **Project role:** Security Operations and Threat Detection Analyst
- **Repository:** UK-SME-Hybrid-SOC
- **Project type:** Personal cybersecurity portfolio and authorised laboratory project
- **Project status:** Planning and foundation
- **Project start date:** July 2026

## Executive summary

Project Beacon is a practical cybersecurity programme designed to
develop and demonstrate a hybrid Security Operations Centre and
incident-response capability for Beacon Professional Services Ltd, a
fictional UK-based organisation employing approximately 200 people.

The organisation depends on Microsoft 365, Microsoft Azure, Microsoft
Entra ID, Active Directory, Windows endpoints, Windows Server, Linux
systems and remote-access services.

The project will centralise security telemetry, develop threat
detections, investigate realistic incidents and create repeatable
response procedures.

The planned environment will use Microsoft Sentinel, Log Analytics,
KQL, Windows security events, Sysmon, Linux logs and network
intrusion-detection alerts.

The project will also produce technical investigation records,
incident-response runbooks, escalation procedures and executive-level
security reporting.

## Business problem

Beacon Professional Services Ltd relies heavily on user accounts,
Microsoft 365, remote access, Windows endpoints, cloud services and
shared business information.

However, the organisation has a limited internal security capability
and no dedicated 24-hour Security Operations Centre.

Security information is distributed across identity, endpoint, server,
cloud and network systems. This makes it difficult for the organisation
to identify related malicious activity quickly and build a complete
incident timeline.

The organisation also lacks consistent procedures for:

- Centralised security monitoring
- Alert triage
- Incident classification
- Evidence collection
- Incident escalation
- Containment decisions
- Business-impact assessment
- Post-incident improvement

Recent phishing emails, repeated authentication failures, suspected
password-spraying activity and unusual PowerShell execution have
increased the need for improved security visibility.

Without centralised monitoring and documented response procedures,
the organisation may fail to detect or contain compromised accounts,
malicious endpoint activity, privilege misuse or attempted data theft
quickly enough.

A delayed or inconsistent response could result in:

- Exposure of customer information
- Exposure of employee information
- Unauthorised access to commercial contracts
- Loss of confidential project files
- Disruption to business operations
- Financial loss
- Reputational damage
- Contractual or data-protection consequences

Project Beacon will address this problem by designing a practical,
repeatable and appropriately scaled hybrid SOC capability for a
resource-constrained UK SME.

## Project goal

Design, build and document a realistic hybrid Security Operations
Centre and incident-response capability for Beacon Professional
Services Ltd.

The project will demonstrate how a small UK organisation can improve
visibility across identity, endpoint, server, cloud and network
activity using appropriately scaled security controls, centralised
logging, documented detections and repeatable response procedures.

## Project objectives

Project Beacon will:

1. Design a documented hybrid SOC architecture for the fictional
   organisation.

2. Build a controlled Microsoft Azure environment supporting security
   monitoring and practical learning.

3. Configure Microsoft Sentinel and Log Analytics as the primary
   centralised security-monitoring platform.

4. Collect and analyse relevant identity, endpoint, server, cloud and
   network telemetry.

5. Develop and document at least 20 practical KQL queries for
   monitoring, investigation and threat hunting.

6. Create security detections for realistic attack behaviours affecting
   the organisation.

7. Simulate and investigate four authorised security incidents:

   - Password spraying against Microsoft Entra ID or Active Directory
   - Phishing followed by suspicious PowerShell activity
   - Privilege escalation and lateral movement
   - Data staging and attempted exfiltration

8. Produce an incident ticket, investigation hypothesis, evidence table,
   timeline, MITRE ATT&CK mapping and severity decision for each
   incident.

9. Create containment, eradication and recovery recommendations for
   each investigated incident.

10. Develop repeatable incident-response runbooks and an escalation
    procedure.

11. Translate technical findings into understandable business-risk
    reports.

12. Conduct a controlled multi-participant tabletop incident-response
    exercise.

13. Record lessons learned and convert identified gaps into practical
    security improvements.

14. Publish sanitised portfolio evidence without exposing passwords,
    secrets, personal information or unauthorised systems.

## Project scope

### In-scope technologies

The project may include:

- Microsoft Azure
- Microsoft Sentinel
- Azure Log Analytics
- Azure Monitor
- Microsoft Entra ID
- Active Directory
- Windows endpoints
- Windows Server
- Linux server
- Windows Security Events
- Sysmon
- PowerShell logging
- Snort or Suricata
- Network packet and connection data
- Kali Linux used only within the authorised laboratory
- Kusto Query Language
- MITRE ATT&CK
- GitHub documentation
- Safe simulated or publicly available security data

### In-scope activities

The project includes:

- Business and security-requirement analysis
- SOC architecture design
- Asset identification
- Log-source identification
- Security telemetry collection
- Data-source validation
- KQL query development
- Alert and detection creation
- Alert triage
- Incident investigation
- Evidence collection
- Timeline development
- Root-cause hypothesis development
- Blast-radius assessment
- Severity classification
- MITRE ATT&CK mapping
- Containment recommendations
- Incident-response runbook development
- Escalation planning
- Tabletop-exercise facilitation
- Executive reporting
- Lessons-learned reviews
- Detection and process improvement

## Out-of-scope activities

The following activities are outside the project scope:

- Testing public systems without explicit authorisation
- Testing employer, university or customer systems
- Conducting destructive attacks
- Developing or distributing malware
- Collecting real customer or employee information
- Publishing passwords, credentials, API keys or access tokens
- Publishing personal IP addresses or sensitive account identifiers
- Claiming the portfolio project is paid commercial employment
- Operating a real 24-hour Security Operations Centre
- Guaranteeing complete security protection
- Building a production-ready enterprise environment
- Performing unrelated penetration-testing projects
- Using live phishing against real users
- Attempting unauthorised account access

## Major project deliverables

Project Beacon will produce:

1. Fictional organisation profile
2. Project charter
3. Stakeholder register
4. Risk register
5. Success-measurement framework
6. RACI matrix
7. Asset inventory
8. Hybrid SOC architecture diagram
9. Security-log data-flow diagram
10. Azure mini-lab
11. Microsoft Sentinel and Log Analytics environment
12. Data-source register
13. KQL query library
14. Documented detection rules
15. Detection backlog
16. Four complete incident-investigation records
17. Incident-response runbooks
18. Alert-severity matrix
19. Incident-escalation procedure
20. Tabletop-exercise plan and decision record
21. SOC performance dashboard
22. Executive incident briefing
23. Post-incident review
24. Prioritised security-improvement roadmap
25. Final GitHub portfolio presentation

## Project assumptions

The project assumes that:

- All technical activity will occur within authorised environments.
- The organisation, users and security incidents are fictional.
- Free, trial or low-cost technology will be prioritised.
- Some security events may be safely simulated.
- Some investigations may use sanitised public datasets when live
  product telemetry is unavailable.
- Microsoft product availability may depend on licensing and trial
  access.
- Portfolio screenshots will be sanitised before publication.
- Technical results will be documented honestly, including failures and
  limitations.

## Project constraints

The project is subject to:

- Limited Azure and software budget
- Limited Microsoft trial or licence availability
- Limited local computing resources
- A single primary project owner
- Time available alongside certification study and job applications
- The requirement to avoid unauthorised activity
- The requirement to protect credentials and personal information
- The need to keep the environment small enough to complete
- Possible differences between laboratory and production environments
- The need to document every major technical task

## High-level delivery sequence

| Stage | Planned output |
|---|---|
| Foundation | Organisation profile, charter, risks, metrics and RACI |
| Architecture | Asset inventory, architecture and log-flow diagrams |
| Azure foundation | Azure mini-lab and monitoring controls |
| SOC foundation | Sentinel, Log Analytics and data sources |
| Query development | Documented KQL monitoring and hunting queries |
| Detection engineering | Tested detections and tuning records |
| Incident investigation | Four complete incident cases |
| Response leadership | Runbooks, escalation and tabletop exercise |
| Reporting | Dashboard, executive report and improvement roadmap |
| Portfolio completion | Final documentation and interview presentation |
