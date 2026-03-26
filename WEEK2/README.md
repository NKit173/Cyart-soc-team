
Theoretical Knowledge

1. Alert Priority Levels
What to Learn:
Core Concepts:
Priority Definitions: Understand severity levels (Critical, High, Medium, Low) based on impact (e.g., data breach, service disruption) and urgency (e.g., active exploitation). Example: Critical = ransomware encryption; High = unauthorized admin access.
Assignment Criteria: Prioritize using asset criticality (e.g., production server vs. test VM), exploit likelihood (e.g., known CVE with public exploit), and business impact (e.g., financial loss). Example: CVSS score of 9.8 for Log4Shell (CVE-2021-44228) = Critical.
Scoring Systems: Master CVSS for risk quantification and explore SOC tools like Splunk’s risk scoring for alert prioritization.

Key Objectives: Develop skills to assess and prioritize alerts using standardized criteria for efficient SOC operations.
How to Learn:
Study CVSS using FIRST’s CVSS guide to understand base, temporal, and environmental metrics.
Review NIST SP 800-61 for incident severity classification and prioritization workflows.
Analyze a real-world case (e.g., Log4Shell prioritization in CISA’s alerts) to map CVSS scores to priority levels.


2. Incident Classification
What to Learn:
Core Concepts:
Incident Categories: Classify incidents by type, such as malware, phishing, DDoS, insider threats, or data exfiltration. Example: Insider threat = unauthorized data export by employee.
Taxonomy: Use frameworks like MITRE ATT&CK (e.g., T1566 - Phishing), ENISA Incident Taxonomy, and VERIS (Vocabulary for Event Recording and Incident Sharing) for standardized labeling.
Contextual Metadata: Enrich incidents with details like affected systems, timestamps, source IPs, and IOCs (e.g., malicious hash).

Key Objectives: Build proficiency in categorizing, labeling, and enriching incidents to streamline investigations.
How to Learn:
Explore MITRE ATT&CK to map incidents to tactics and techniques.
Study ENISA Incident Taxonomy and VERIS framework for classification standards.
Review case studies (e.g., phishing campaigns via SANS Reading Room) to practice adding metadata.


3. Basic Incident Response
What to Learn:
Core Concepts:
Incident Lifecycle: Understand phases: Preparation (e.g., playbooks), Identification (e.g., alert triage), Containment (e.g., isolate systems), Eradication (e.g., remove malware), Recovery (e.g., restore services), Lessons Learned (e.g., post-mortem).
Procedures: Learn system isolation, evidence preservation (e.g., memory dumps, file hashing), communication protocols, and SOAR tools for automation (e.g., Splunk Phantom for workflow orchestration).

Key Objectives: Master the incident response lifecycle and procedures to respond effectively to security events.
How to Learn:
Study NIST SP 800-61 Incident Handling Guide for lifecycle details.
Use SANS Incident Handler’s Handbook for response templates and best practices.
Explore Let’s Defend for simulated incident response scenarios and SOAR concepts.


Practical Application
1. Alert Management Practice
Activities:
Tools: Google Sheets, Wazuh, TheHive.
Tasks: Create an alert classification system, prioritize alerts, document response procedures, create incident tickets, and practice escalation.
Enhanced Tasks:
Alert Classification System: Create a Google Sheets table to map alerts to MITRE ATT&CK techniques:
| Alert ID | Type        | Priority | MITRE Tactic       |
|----------|-------------|----------|--------------------|
| 001      | Phishing    | High     | T1566             |
Test with a mock alert (e.g., “Phishing Email: Suspicious Link”).
Prioritize Alerts: Simulate alerts (e.g., “Critical: Log4Shell Exploit Detected” vs. “Low: Port Scan”) and score using CVSS in Google Sheets. Example: Log4Shell CVSS 9.8 = Critical.
Dashboard Creation: In Wazuh, create a dashboard to visualize alert priorities (e.g., pie chart for Critical vs. High alerts).
Incident Ticket: Draft a ticket in TheHive with fields:
Title: [Critical] Ransomware Detected on Server-X
Description: Indicators: [File: crypto_locker.exe], [IP: 192.168.1.50]
Priority: Critical
Assignee: SOC Analyst
Escalation Role-Play: Draft a 100-word email to escalate a Critical alert to Tier 2, summarizing the incident and IOCs.


2. Response Documentation
Activities:
Tools: Google Docs, Draw.io.
Tasks: Create incident response templates, document investigation steps, create checklists, and conduct a mock post-mortem.
Enhanced Tasks:
Incident Response Template: Use a SANS template in Google Docs to document a mock phishing incident:
1. Executive Summary
2. Timeline
3. Impact Analysis
4. Remediation Steps
5. Lessons Learned
Investigation Steps: Log actions for a mock incident:
| Timestamp            | Action                     |
|----------------------|----------------------------|
| 2025-08-18 14:00:00 | Isolated endpoint          |
| 2025-08-18 14:30:00 | Collected memory dump      |
Phishing Checklist: Create a checklist in Google Docs:
- [ ] Confirm email headers
- [ ] Check link reputation (VirusTotal)
- [ ] Identify affected users
Post-Mortem: Summarize lessons learned from a simulated breach in 50 words, focusing on process improvements.


3. Alert Triage Practice
Activities:
Tools: Wazuh, VirusTotal, AlienVault OTX.
Tasks: Simulate triage with sample alerts and validate false positives.
Enhanced Tasks:
Triage Simulation: Analyze a mock alert (e.g., “Brute-force SSH Attempts”) in Wazuh. Document:
| Alert ID | Description            | Source IP      | Priority | Status |
|----------|------------------------|----------------|----------|--------|
| 002      | Brute-force SSH        | 192.168.1.100  | Medium   | Open   |
Threat Intelligence Validation: Cross-reference the alert’s IP or file hash with AlienVault OTX to validate IOCs. Summarize findings in 50 words.


4. Evidence Preservation
Activities:
Tools: Velociraptor, FTK Imager.
Tasks: Practice evidence preservation and chain-of-custody documentation.
Enhanced Tasks:
Volatile Data Collection: Use Velociraptor to collect network connections (SELECT * FROM netstat) from a Windows VM. Save to CSV.
Evidence Collection: Collect a memory dump (SELECT * FROM Artifact.Windows.Memory.Acquisition) and hash it using sha256sum. Document:
| Item       | Description       | Collected By | Date       | Hash Value        |
|------------|-------------------|--------------|------------|-------------------|
| Memory Dump| Server-X Dump     | SOC Analyst  | 2025-08-18 | <SHA256>          |

5. Capstone Project: Full Alert-to-Response Cycle
Activities:
Tools: Metasploit, Wazuh, CrowdSec, Google Docs.
Tasks: Simulate an attack, detect, triage, respond, and document.
Enhanced Tasks:
Attack Simulation: Exploit a Metasploitable2 vulnerability with Metasploit (e.g., vsftpd backdoor: use exploit/unix/ftp/vsftpd_234_backdoor). Follow Metasploit Unleashed.
Detection and Triage: Configure Wazuh to alert on the attack. Document:
| Timestamp            | Source IP      | Alert Description | MITRE Technique |
|----------------------|----------------|-------------------|-----------------|
| 2025-08-18 11:00:00 | 192.168.1.100  | VSFTPD exploit    | T1190          |
Response: Isolate the VM and block the attacker’s IP with CrowdSec. Verify with a ping test.
Reporting: Write a 200-word report in Google Docs using a SANS template, including Executive Summary, Timeline, and Recommendations.
Stakeholder Briefing: Draft a 100-word briefing for a non-technical manager, summarizing the incident and actions taken.


Deadline: Friday 4:30 PM 
Submission: Create a GitHub Repository named cyart-soc-team in that create folder named Week 2, Add all the Documentation (PDF, notes, screenshot), Workflow with Steps (In Sub Folder or Readme File)

You will need to Submit that Git Repository Link to me via DM On Friday
