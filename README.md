# SOC Automation Lab Project

Inspired by the [MyDFIR YouTube Channel](https://www.youtube.com/@MyDFIR), this project documents the creation of an automated Security Operations Center (SOC) lab environment, leveraging open-source tools to simulate threat detection, case management, and automated response.

---

## 🧱 Architecture Overview

The lab setup includes:

- **Wazuh**: For log collection and security monitoring.
- **TheHive**: For case management and threat intelligence triage.
- **Shuffle**: For workflow orchestration and automated response.
- **pfSense**: As the firewall and network segmentation layer.
- **Sysmon**: For detailed endpoint telemetry on Windows 10.
- **Windows & Ubuntu VMs**: As endpoint hosts to simulate attacks and log ingestion.

![Architecture Diagram](images/architecture_diagram.png)

---

## 🧰 Tools Used

| Tool      | Purpose                                 |
|-----------|------------------------------------------|
| Wazuh     | SIEM / Log Analysis                      |
| TheHive   | Case Management                          |
| Shuffle   | Workflow Automation                      |
| Sysmon    | Endpoint Logging                         |
| pfSense   | Firewall / Routing                       |
| Ubuntu    | Linux Syslog Source / Attack Host        |
| Windows 10| Endpoint for Detection and Sysmon Logs   |

---

## 🧪 Lab Setup Guide

### 1. Windows 10 + Sysmon Configuration
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

---

## 🔁 Workflow Example

```json
{
  "trigger": "critical_alert",
  "actions": [
    "Run VirusTotal scan",
    "Create case in TheHive",
    "Notify analyst via email"
  ]
}
```

---

## 📷 Screenshots

- ![Wazuh Dashboard](images/sample_screenshots/wazuh_dashboard.png)
- ![TheHive Case View](images/sample_screenshots/thehive_case.png)
- ![Shuffle Workflow](images/sample_screenshots/shuffle_flow.png)

---

## 🧠 Skills Practiced

- Security monitoring
- Automation workflows
- Case handling and triage
- Open-source tool configuration
- Alert enrichment and response

---

## 🙏 Credits

This project is based on the excellent [MyDFIR YouTube series](https://www.youtube.com/@MyDFIR), especially the SOC Automation Lab and 30-Day SOC Analyst Challenge.

> Subscribe and support the channel for more practical SOC content!

---

## 🔗 Related Resources

- [Wazuh Documentation](https://documentation.wazuh.com/)
- [TheHive Project](https://thehive-project.org/)
- [Shuffle Orchestration](https://shuffler.io/)
- [Sysmon GitHub](https://github.com/Sysinternals/Sysmon)
- [pfSense Documentation](https://docs.netgate.com/pfsense/en/latest/)

---

_This GitHub repository documents an educational SOC project for skill development only._
