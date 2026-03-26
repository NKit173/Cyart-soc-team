
1. Threat Hunting Methodologies
What to Learn:
Core Concepts:
Proactive Threat Hunting: Understand hypothesis-driven hunting (e.g., searching for TTPs like T1078 - Valid Accounts misuse) vs. reactive incident response. Example: Hunt for anomalous privilege escalation in logs.
Hunting Frameworks: Study frameworks like SqRR (Search, Query, Retrieve, Respond) and TaHiTI (Targeted Hunting integrating Threat Intelligence).
Data Sources for Hunting: Learn to leverage diverse sources (e.g., EDR logs, network traffic, threat intelligence feeds) for effective hunting.

Key Objectives: Develop skills to proactively identify threats using structured methodologies and data analysis.
How to Learn:
Study SqRR and TaHiTI via SANS Threat Hunting papers.
Explore threat hunting case studies (e.g., APT29 via MITRE ATT&CK).
Review Elastic’s threat hunting guide for practical approaches.


2. Advanced SOAR Automation
What to Learn:
Core Concepts:
SOAR Components: Understand Security Orchestration, Automation, and Response components: orchestration (workflow integration), automation (e.g., auto-ticketing), and response (e.g., auto-containment).
Playbook Development: Learn to design playbooks for common incidents (e.g., phishing, malware). Example: Automate IP blocking for C2 traffic.
Integration with SIEM/EDR: Explore integrating SOAR with tools like Wazuh or Elastic for streamlined workflows.

Key Objectives: Build proficiency in automating repetitive SOC tasks to improve efficiency and response times.
How to Learn:
Study SOAR concepts via Splunk SOAR documentation.
Review playbook examples in TheHive Project for incident response automation.
Analyze automation case studies (e.g., phishing response automation via CISA’s SOAR guide).


3. Post-Incident Analysis and Continuous Improvement
What to Learn:
Core Concepts:
Root Cause Analysis (RCA): Learn RCA techniques (e.g., 5 Whys, Fishbone Diagram) to identify incident causes. Example: RCA for a phishing breach revealing weak email filters.
Lessons Learned Process: Understand how to conduct post-mortems to improve processes, tools, and training.
Metrics and KPIs: Study SOC metrics like Mean Time to Detect (MTTD) and Mean Time to Respond (MTTR) to measure performance.

Key Objectives: Master post-incident analysis to drive continuous improvement in SOC operations.
How to Learn:
Study RCA techniques via SANS Reading Room.
Review NIST SP 800-61 for post-incident activity guidelines.
Explore SOC metrics via CISA’s Cybersecurity Metrics.


4. Adversary Emulation Techniques
What to Learn:
Core Concepts:
Adversary Emulation: Understand simulating attacker TTPs (e.g., T1566 - Phishing, T1210 - Exploitation of Remote Services) to test SOC detection and response capabilities.
Emulation Frameworks: Study tools like MITRE Caldera for automated adversary simulation. Example: Simulate a spearphishing attack to test email filtering.
Red-Blue Team Collaboration: Learn how emulation informs defensive strategies and improves detection rules.

Key Objectives: Develop skills to simulate adversary behaviors to enhance SOC preparedness and validate controls.
How to Learn:
Explore MITRE Caldera for emulation workflows and TTP mappings.
Study adversary emulation case studies (e.g., APT28 via MITRE ATT&CK).
Review Red Canary’s emulation guide for practical approaches.


5. Security Metrics and Executive Reporting
What to Learn:
Core Concepts:
Advanced SOC Metrics: Understand metrics like dwell time (time from compromise to detection), false positive rate, and incident resolution rate to evaluate SOC performance.
Executive Reporting: Learn to present metrics and incident summaries to non-technical stakeholders using clear visualizations and narratives.
Continuous Improvement: Use metrics to identify gaps (e.g., high MTTD indicating slow detection) and propose solutions.

Key Objectives: Build proficiency in measuring SOC performance and communicating results to leadership.
How to Learn:
Study SOC metrics via SANS Reading Room (e.g., “Measuring SOC Success”).
Review CISA’s Cybersecurity Metrics for reporting frameworks.
Explore executive reporting templates via SANS Incident Response templates.




Practical Application

1. Threat Hunting Practice
Activities:
Tools: Elastic Security, Velociraptor, AlienVault OTX.
Tasks: Develop a hunting hypothesis, query logs, and validate findings.
Enhanced Tasks:
Hypothesis Development: Formulate a hypothesis (e.g., “Unauthorized privilege escalation in domain accounts”). Query Elastic Security for Event ID 4672 (role assignment). Document:
| Timestamp            | User       | Event ID | Notes                     |
|----------------------|------------|----------|---------------------------|
| 2025-08-18 15:00:00  | testuser   | 4672     | Unexpected admin role     |
Threat Intelligence Hunt: Use AlienVault OTX to search for T1078 IOCs (e.g., suspicious IPs). Cross-reference with Velociraptor queries (SELECT * FROM processes).
Hunting Report: Summarize findings in a 100-word report, mapping to MITRE ATT&CK T1078.


2. SOAR Playbook Development
Activities:
Tools: Splunk Phantom, TheHive, Google Docs.
Tasks: Design and test a playbook for automated incident response.
Enhanced Tasks:
Playbook Creation: Create a Splunk Phantom playbook to auto-block IPs for phishing alerts. Example steps: Check IP reputation → Block via CrowdSec → Create TheHive ticket.
Playbook Test: Simulate a phishing alert in Wazuh and verify playbook execution. Document:
| Playbook Step | Status  | Notes                     |
|---------------|---------|---------------------------|
| Check IP      | Success | IP flagged as malicious   |
| Block IP      | Success | CrowdSec blocked 192.168.1.102 |
Documentation: Write a 50-word playbook summary in Google Docs.


3. Post-Incident Analysis
Activities:
Tools: Google Sheets, Draw.io.
Tasks: Conduct RCA, document lessons learned, and calculate SOC metrics.
Enhanced Tasks:
Root Cause Analysis: Use the 5 Whys method for a mock phishing incident. Document in Google Sheets:
| Question       | Answer                     |
|----------------|----------------------------|
| Why was email opened? | User clicked malicious link |
| Why was link clicked? | Weak email filtering       |
Fishbone Diagram: Create a Fishbone Diagram in Draw.io for the incident, identifying causes (e.g., process, technology).
Metrics Calculation: Calculate MTTD and MTTR for a mock incident (e.g., Detection: 2 hours, Response: 4 hours). Summarize in 50 words.


4. Alert Triage with Automation
Activities:
Tools: Wazuh, VirusTotal, TheHive.
Tasks: Triage alerts and automate validation with threat intelligence.
Enhanced Tasks:
Triage Simulation: Analyze a mock alert (e.g., “Suspicious File Download”) in Wazuh. Document:
| Alert ID | Description            | Source IP      | Priority | Status |
|----------|------------------------|----------------|----------|--------|
| 005      | File Download          | 192.168.1.102  | High     | Open   |
Automated Validation: Configure TheHive to auto-check file hashes with VirusTotal. Summarize results in 50 words.


5. Evidence Analysis
Activities:
Tools: Velociraptor, FTK Imager.
Tasks: Analyze collected evidence and maintain chain-of-custody.
Enhanced Tasks:
Evidence Analysis: Use Velociraptor to analyze network connections (SELECT * FROM netstat) from a Windows VM. Identify suspicious connections.
Chain-of-Custody: Document evidence collection:
| Item       | Description       | Collected By | Date       | Hash Value        |
|------------|-------------------|--------------|------------|-------------------|
| Network Log| Server-Z Log      | SOC Analyst  | 2025-08-18 | <SHA256>          |

6. Adversary Emulation Practice
Activities:
Tools: MITRE Caldera, Wazuh.
Tasks: Simulate adversary TTPs and test SOC detection capabilities.
Enhanced Tasks:
Emulation Simulation: Use Caldera to simulate a spearphishing attack (T1566). Configure Wazuh to detect the attack. Document:
| Timestamp            | TTP         | Detection Status | Notes                     |
|----------------------|-------------|------------------|---------------------------|
| 2025-08-18 17:00:00 | T1566       | Detected         | Phishing email blocked    |
Emulation Report: Summarize the emulation results in a 100-word report, highlighting detection gaps.


7. Security Metrics and Executive Reporting
Activities:
Tools: Elastic Security, Google Sheets, Google Docs.
Tasks: Calculate advanced metrics and create executive reports.
Enhanced Tasks:
Metrics Dashboard: Create an Elastic Security dashboard for MTTD, MTTR, and false positive rate. Example: MTTD = 2 hours, MTTR = 4 hours.
Executive Report: Draft a 150-word executive summary in Google Docs, presenting metrics and recommendations for SOC improvement.
Metrics Analysis: Analyze dwell time for a mock incident in Google Sheets. Summarize findings in 50 words.


8. Capstone Project: Comprehensive SOC Incident Response
Activities:
Tools: Metasploit, Wazuh, CrowdSec, TheHive, MITRE Caldera, Elastic Security, Google Docs.
Tasks: Simulate a complex attack, detect, triage, respond, analyze, emulate, and report.
Enhanced Tasks:
Attack Simulation: Exploit a Metasploitable2 vulnerability with Metasploit (e.g., Samba usermap script: use exploit/multi/samba/usermap_script). Follow Metasploit Unleashed.
Adversary Emulation: Use Caldera to simulate a related TTP (e.g., T1210 - Exploitation of Remote Services). Document detection in Wazuh:
| Timestamp            | Source IP      | Alert Description | MITRE Technique |
|----------------------|----------------|-------------------|-----------------|
| 2025-08-18 16:00:00 | 192.168.1.102  | Samba exploit     | T1210          |
Detection and Triage: Configure Wazuh to alert on the attack and triage in TheHive.
Response and Containment: Isolate the VM and block the attacker’s IP with CrowdSec. Verify with a ping test.
SOAR Automation: Create a TheHive case and automate IP blocking via a playbook. Verify execution.
Post-Incident Analysis: Conduct RCA using the 5 Whys and create a Fishbone Diagram in Draw.io.
Metrics Reporting: Calculate MTTD, MTTR, and dwell time in Elastic Security. Create a dashboard.
Reporting: Write a 300-word report in Google Docs using a SANS template, including Executive Summary, Timeline, RCA, and Recommendations.
Stakeholder Briefing: Draft a 150-word briefing for a non-technical executive, summarizing the incident, metrics, and improvements.
