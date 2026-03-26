
Theoretical Knowledge
1. Advanced Log Analysis
What to Learn:
Core Concepts:
Log Correlation: Understand correlating logs from multiple sources (e.g., firewall, endpoint, application logs) to identify attack patterns. Example: Linking failed logins (Event ID 4625) with suspicious outbound traffic.
Anomaly Detection: Learn techniques to detect anomalies (e.g., unusual login times, high-volume data transfers) using statistical or rule-based methods.
Log Enrichment: Explore adding context to logs (e.g., geolocation for IPs, user roles) to enhance analysis.

Key Objectives: Develop skills to analyze and correlate logs to uncover complex threats and reduce false positives.
How to Learn:
Study log correlation techniques via SANS Reading Room (e.g., “Effective Log Analysis” papers).
Explore anomaly detection with Elastic’s documentation.
Review case studies (e.g., Equifax breach via CISA reports) to understand log correlation in real incidents.


2. Threat Intelligence Integration
What to Learn:
Core Concepts:
Threat Intelligence Types: Understand indicators of compromise (IOCs) (e.g., malicious IPs, hashes), tactics, techniques, and procedures (TTPs), and threat feeds (e.g., STIX/TAXII).
Integration in SOC: Learn to integrate threat intelligence into SIEMs for automated alert enrichment. Example: Matching a suspicious IP to a known C2 server.
Threat Hunting with Intelligence: Use intelligence to proactively search for threats (e.g., hunting for T1078 - Valid Accounts misuse).

Key Objectives: Build proficiency in leveraging threat intelligence to enhance detection and response.
How to Learn:
Explore MITRE ATT&CK for TTPs and their application in threat hunting.
Study STIX/TAXII standards via OASIS Cyber Threat Intelligence.
Review AlienVault OTX for practical threat feed examples.


3. Incident Escalation Workflows
What to Learn:
Core Concepts:
Escalation Tiers: Understand SOC tier structure (Tier 1: Triage, Tier 2: Investigation, Tier 3: Advanced Analysis) and escalation criteria (e.g., severity, complexity).
Communication Protocols: Learn structured communication for escalation (e.g., SITREP - Situation Reports) and stakeholder briefings.
Automation in Escalation: Explore SOAR tools for automating escalation tasks (e.g., ticket assignment, alert enrichment).

Key Objectives: Master workflows for escalating incidents and communicating with stakeholders effectively.
How to Learn:
Study escalation workflows in NIST SP 800-61.
Review SANS Incident Handler’s Handbook for communication templates.
Explore SOAR concepts via Splunk SOAR documentation.


Practical Application

1. Advanced Log Analysis
Activities:
Tools: Elastic Security, Security Onion, Google Sheets.
Tasks: Correlate logs, detect anomalies, and enrich log data.
Enhanced Tasks:
Log Correlation: Ingest sample logs (e.g., from Boss of the SOC dataset) into Elastic Security. Correlate failed logins (Event ID 4625) with outbound traffic. Document:
| Timestamp            | Event ID | Source IP      | Destination IP | Notes                     |
|----------------------|----------|----------------|----------------|---------------------------|
| 2025-08-18 12:00:00  | 4625     | 192.168.1.100  | 8.8.8.8        | Suspicious DNS request    |
Anomaly Detection: Create an Elastic rule to detect high-volume data transfers (e.g., bytes_out > 1MB in 1m). Test with a mock file transfer.
Log Enrichment: Use a GeoIP plugin in Elastic to add geolocation to an IP. Summarize findings in 50 words.


2. Threat Intelligence Integration
Activities:
Tools: Wazuh, AlienVault OTX, TheHive.
Tasks: Import threat feeds, enrich alerts, and hunt for threats.
Enhanced Tasks:
Threat Feed Import: Import an AlienVault OTX feed into Wazuh to match IOCs (e.g., malicious IPs). Test with a mock IP (e.g., 192.168.1.100).
Alert Enrichment: Enrich a Wazuh alert with OTX data (e.g., IP reputation). Document:
| Alert ID | IP            | Reputation        | Notes                     |
|----------|---------------|-------------------|---------------------------|
| 003      | 192.168.1.100 | Malicious (OTX)   | Linked to C2 server       |
Threat Hunting: Hunt for T1078 (Valid Accounts) in Wazuh logs using a query (e.g., user.name != "system"). Summarize findings in 50 words.


3. Incident Escalation Practice
Activities:
Tools: TheHive, Google Docs.
Tasks: Simulate escalation, draft SITREPs, and automate workflows.
Enhanced Tasks:
Escalation Simulation: Create a TheHive case for a High-priority alert (e.g., unauthorized access). Escalate to Tier 2 with a 100-word summary.
SITREP Draft: Write a Situation Report in Google Docs for a mock incident:
Title: Unauthorized Access on Server-Y
Summary: Detected at 2025-08-18 13:00, IP: 192.168.1.200, MITRE T1078
Actions: Isolated server, escalated to Tier 2
Workflow Automation: Create a simple Splunk Phantom playbook to auto-assign High-priority alerts to Tier 2. Test with a mock alert.


4. Alert Triage with Threat Intelligence
Activities:
Tools: Wazuh, VirusTotal, AlienVault OTX.
Tasks: Triage alerts and validate IOCs using threat intelligence.
Enhanced Tasks:
Triage Simulation: Analyze a mock alert (e.g., “Suspicious PowerShell Execution”) in Wazuh. Document:
| Alert ID | Description            | Source IP      | Priority | Status |
|----------|------------------------|----------------|----------|--------|
| 004      | PowerShell Execution   | 192.168.1.101  | High     | Open   |
IOC Validation: Cross-reference the alert’s IP or hash with VirusTotal and OTX. Summarize findings in 50 words.


5. Evidence Preservation and Analysis
Activities:
Tools: Velociraptor, FTK Imager.
Tasks: Collect and preserve evidence, maintain chain-of-custody.
Enhanced Tasks:
Volatile Data Collection: Use Velociraptor to collect network connections (SELECT * FROM netstat) from a Windows VM. Save to CSV.
Evidence Collection: Collect a memory dump (SELECT * FROM Artifact.Windows.Memory.Acquisition) and hash it using sha256sum. Document:
| Item       | Description       | Collected By | Date       | Hash Value        |
|------------|-------------------|--------------|------------|-------------------|
| Memory Dump| Server-Y Dump     | SOC Analyst  | 2025-08-18 | <SHA256>          |

6. Capstone Project: Full SOC Workflow Simulation
Activities:
Tools: Metasploit, Wazuh, CrowdSec, TheHive, Google Docs.
Tasks: Simulate an attack, detect, triage, respond, escalate, and report.
Enhanced Tasks:
Attack Simulation: Exploit a Metasploitable2 vulnerability with Metasploit (e.g., Samba usermap script: use exploit/multi/samba/usermap_script). Follow Metasploit Unleashed.
Detection and Triage: Configure Wazuh to alert on the attack. Document:
| Timestamp            | Source IP      | Alert Description | MITRE Technique |
|----------------------|----------------|-------------------|-----------------|
| 2025-08-18 14:00:00  | 192.168.1.101  | Samba exploit     | T1210          |
Response and Containment: Isolate the VM and block the attacker’s IP with CrowdSec. Verify with a ping test.
Escalation: Escalate to Tier 2 via TheHive with a 100-word case summary.
Reporting: Write a 200-word report in Google Docs using a SANS template, including Executive Summary, Timeline, and Recommendations.
Briefing: Draft a 100-word briefing for a non-technical manager, summarizing the incident and actions.
