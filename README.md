# SOC Automation-Lab

## Overview
This lab demonstrates the use of automation within a Security Operations Center (SOC) to improve workflow efficiency. It highlights the implementation of automated playbooks, alert handling, and incident response using security tools and scripting.

## Objectives
Automate repetitive and time-consuming SOC tasks like alert triage, enrichment, and response execution to reduce analyst workload and improve responsiveness and accuracy.

## Technologies & Tools Used
- Security Information and Event Management (SIEM) tool
- Security Orchestration, Automation, and Response (SOAR) platform
- Python and PowerShell scripts for automating key SOC functions
- APIs for integration and data exchange
- Alert enrichment APIs and tools
- Incident ticketing systems

## Network Architecture & Workflow
#Architecture Diagram

<img width="812" height="766" alt="image" src="https://github.com/user-attachments/assets/118eea80-58a1-4e02-b6e0-a75f65e09a24" />

This diagram represents the end-to-end architecture of the SOC automation setup. It illustrates how Wazuh collects logs from the Windows 10 client, sends them to Shuffle for enrichment, and ultimately logs alerts in The Hive for incident response.

Workflow Diagram
<img width="1192" height="452" alt="image" src="https://github.com/user-attachments/assets/8c48a432-13e4-4529-bc36-1b77613f756d" />
This simplified diagram provides an overview of the incident flow from detection to resolution. It highlights the key steps in how security alerts move from detection (Wazuh) to enrichment (Shuffle) and case management (The Hive).

Shuffle Automation Workflow
<img width="1491" height="818" alt="image" src="https://github.com/user-attachments/assets/c10b1619-0c96-49e5-a277-61f8b6596fb0" />
This detailed visualization of the Shuffle workflow shows how security alerts are processed, enriched with VirusTotal, and forwarded to The Hive. The workflow also includes email notifications for security analysts.

## Methodology
1. Collect security alerts and data from various sources into the SIEM system.
2. Develop automation workflows and playbooks on the SOAR platform to respond to alerts automatically.
3. Use scripts and APIs to enrich alert data with additional context and intelligence.
4. Automate incident creation, updating, and closing in the ticketing system.
5. Continuously monitor workflow automation effectiveness and optimize processes.

## Installation Guide
1. Prerequisites
- Oracle VirtualBox installed.
- Ubuntu ISO for Wazuh and The Hive.
- Windows 10 ISO for client machine.
- Access to VirusTotal API (Free or Paid).
  
2. Setup Instructions
Step 1: Install Wazuh
- Create an Ubuntu 24.04 VM in VirtualBox.
- Install Wazuh using the provided installation script.
- Configure ossec.conf to forward logs to Shuffle.

Step 2: Install The Hive
- Create an Ubuntu 20.04 VM.
- Install necessary dependencies.
- Configure hive_application.conf to connect with Wazuh.
- Start The Hive service.

Step 3: Setup Windows 10 VM
- Install Sysmon to capture detailed logs.
- Configure Sysmon using sysmonconfig.xml.
- Install the Wazuh agent and connect it to Wazuh Manager.

Step 4: Configure Shuffle
- Register at Shuffler.io.
- Create a workflow for handling alerts.
- Connect Shuffle to Wazuh and The Hive using API keys.

## Configuration Files
- ossec.conf → Wazuh configuration.
- cassandra.yaml → Cassandra settings for The Hive.
- hive_application.conf → The Hive configuration.
- sysmonconfig.xml → Sysmon rules for Windows telemetry.
- shuffle_workflow.json → Workflow automation in Shuffle.

## Testing & Validation
1. Run Mimikatz on Windows 10 VM:
- Wazuh should detect suspicious activity.
- Alert should be forwarded to Shuffle.
- Shuffle enriches the alert using VirusTotal.
- The Hive should log a new security case.
- Email/SMS notification should be triggered.

2. Review The Hive:
- Verify case details and logs.
- Initiate response actions.

3. Confirm Automated Response:
- Wazuh should execute remediation steps (e.g., blocking IPs, terminating processes).

## Conclusion
The key steps and achievements of this lab include:

1. Installing and configuring a Windows 10 client with Sysmon for detailed event generation.
2. Setting up Wazuh as the central event management and alerting platform.
3. Installing and configuring TheHive for case management and coordinated response actions.
4. Generating Mimikatz telemetry and creating custom alerts in Wazuh.
5. Integrating Shuffle as the SOAR platform for workflow automation.
6. Building an automated workflow to extract file hashes, check reputation scores with VirusTotal, create alerts in TheHive, and notify SOC analysts via email.

With this lab, we have gained hands-on experience in implementing an automated SOC workflow using powerful open-source tools. We can now leverage this knowledge to enhance your organization's security operations, improve incident response times, and streamline SOC processes.
