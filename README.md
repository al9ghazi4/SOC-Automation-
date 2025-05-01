# SOC Automation Lab Project

This project documents the creation of an automated Security Operations Center (SOC) lab environment, leveraging open-source tools to simulate threat detection, case management, and automated response.

In this lab, I configured multiple virtual machines including Windows 11 and Ubuntu to act as endpoints and attack targets. I deployed **Sysmon** on Windows to collect detailed telemetry and configured **Winlogbeat** to forward logs to **Wazuh**, which served as the SIEM platform. On the Linux side, system logs were also forwarded to Wazuh for unified monitoring.

I installed and configured **TheHive** for incident case management and integrated it with **Cortex** for automated threat intelligence lookups. **Shuffle** was deployed as the automation engine, used to build workflows that respond to critical alerts by triggering Cortex analyzers, generating cases in TheHive, and notifying analysts.

To simulate real-world attack scenarios, I used **Mimikatz** on the Windows endpoint to emulate credential dumping attacks. This activity was detected by Wazuh and automatically processed by Shuffle workflows for enrichment and case creation, demonstrating the effectiveness of SOC automation in detecting and responding to threats.

---

## 🧱 Architecture Overview

The lab setup includes:

- **Wazuh**: For log collection and security monitoring.
- **TheHive**: For case management and threat intelligence triage.
- **Shuffle**: For workflow orchestration and automated response.
- **Sysmon**: For detailed endpoint telemetry on Windows 11.
- **Mimikatz**: For simulating credential access attacks.
- **Windows & Ubuntu VMs**: As endpoint hosts to simulate attacks and log ingestion.

![Architecture Diagram](https://github.com/al9ghazi4/SOC-Automation-/blob/main/Untitled%20Diagram.drawio.png)

---

## 🧰 Tools Used

| Tool      | Purpose                                 |
|-----------|------------------------------------------|
| Wazuh     | SIEM / Log Analysis                      |
| TheHive   | Case Management                          |
| Shuffle   | Workflow Automation                      |
| Sysmon    | Endpoint Logging                         |
| Mimikatz  | Credential Dumping Simulation            |
| Ubuntu    | Linux Syslog Source / Attack Host        |
| Windows 11| Endpoint for Detection and Sysmon Logs   |

---

## 🧪 Lab Setup Guide

### 1. Windows 11 + Sysmon Configuration
- Install Sysmon with pre-built SwiftOnSecurity config.
- Enable Winlogbeat or Filebeat for forwarding logs to Wazuh.

### 2. Wazuh Setup
- Install Wazuh manager and agent.
- Forward logs from Windows + Ubuntu hosts.
- Tune rules to reduce false positives.

### 3. TheHive + Cortex
- Install TheHive 5.
- Integrate Cortex analyzers (VirusTotal, MISP, etc).
- Configure templates for automated case creation.

### 4. Shuffle
- Use Shuffle to build workflows that:
  - Auto-respond to critical alerts.
  - Trigger Cortex scans.
  - Create incidents in TheHive.

### 5. Mimikatz Attack Simulation
- Use Mimikatz, a post-exploitation tool for Windows, to simulate credential harvesting techniques such as dumping LSASS memory, extracting plaintext passwords, hashes, and Kerberos tickets.
- Mimikatz is widely used in red teaming and threat simulation to emulate real-world credential access attacks (e.g., MITRE ATT&CK T1003: Credential Dumping).
- Execute pass-the-hash or pass-the-ticket operations to observe Wazuh’s detection response.
- Confirm detection of suspicious credential access activity and validate that it triggers automated workflows via Shuffle.

> Learn more: [Mimikatz GitHub](https://github.com/gentilkiwi/mimikatz), [MITRE ATT&CK T1003](https://attack.mitre.org/techniques/T1003/)
- Confirm detection by Wazuh and trigger workflow in Shuffle.


---

## 📷 Screenshots

- https://drive.google.com/drive/folders/1IPDgSK79i8l1C6-YZFypaQtOZk3ypHG2?usp=drive_link
---

## 🧠 Skills Practiced

- Security monitoring
- Automation workflows
- Case handling and triage
- Open-source tool configuration
- Alert enrichment and response

---

## 🔗 Related Resources

- [Wazuh Documentation](https://documentation.wazuh.com/)
- [TheHive Project](https://thehive-project.org/)
- [Shuffle Orchestration](https://shuffler.io/)
- [Sysmon GitHub](https://github.com/Sysinternals/Sysmon)
- [Mimikatz GitHub](https://github.com/gentilkiwi/mimikatz)

---

_This GitHub repository documents an educational SOC project for skill development only._
