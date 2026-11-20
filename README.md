# SOC Build-Out Using Splunk

## 1. Project Overview

This project demonstrates a basic Security Operations Center (SOC) monitoring environment using Splunk Enterprise, Sysmon, Windows and Ubuntu Linux.

The objective was to collect endpoint security logs, monitor system activity, identify suspicious events, configure detections and visualize security events through a centralized dashboard.

## 2. Architecture

**Monitoring workflow:**

1. Windows endpoint generates system and security events.
2. Sysmon collects detailed Windows process and network activity.
3. Windows Universal Forwarder forwards logs to Splunk.
4. Ubuntu Server generates authentication and system logs.
5. Ubuntu Universal Forwarder forwards Linux logs to Splunk.
6. Splunk Enterprise indexes, searches and analyzes the collected events.
7. Dashboards and alerts support security monitoring.

## 3. Tools and Technologies

| Tool | Purpose |
|---|---|
| Splunk Enterprise | SIEM and log analysis |
| Windows 11 | Endpoint monitoring |
| Ubuntu Server 24.04.5 | Linux log monitoring |
| Sysmon | Windows system activity monitoring |
| Splunk Universal Forwarder | Log forwarding |
| PowerShell | Testing and system administration |

## 4. Implemented Features

- Centralized Windows and Ubuntu log collection.
- Windows Sysmon event monitoring.
- Linux authentication log monitoring.
- Windows failed-login detection.
- PowerShell process activity monitoring.
- Administrator group modification monitoring.
- Sysmon network connection monitoring.
- SOC dashboard with multiple monitoring panels.
- Scheduled alert configuration for repeated Windows failed logins.

## 5. Detection Use Cases

| Security activity | Event / Detection |
|---|---|
| Failed Windows logins | Event ID 4625 |
| PowerShell execution | Sysmon Event ID 1 |
| Administrator group changes | Event ID 4732 |
| Network connections | Sysmon Event ID 3 |

MITRE ATT&CK references used in the project include:

- T1110 – Brute Force
- T1059.001 – PowerShell
- T1098 – Account Manipulation
- T1049 – System Network Connections Discovery

## 6. Testing and Validation

The lab was tested using controlled activities, including:

- Generating Windows failed-login events.
- Monitoring PowerShell process activity.
- Testing encoded PowerShell command detection using a harmless test.
- Adding and subsequently removing a temporary user from the Administrators group.
- Verifying Sysmon network connection events.
- Confirming Ubuntu authentication and system logs were received in Splunk.

Screenshots and configuration files are included in this repository.

## 7. Repository Contents

- `SOC-Build-Out-Report.md` – Detailed project report.
- `SOC-Build-Out-Report.pdf` – PDF version of the report.
- `*.png` – Implementation screenshots and evidence.
- `Sysmon-Current-Configuration.txt` – Sysmon configuration evidence.
- `sysmon-network-config.xml` – Sysmon network monitoring configuration.

## 8. Implementation Limitations

This project implements a basic two-endpoint SOC monitoring environment.

The following components from the broader project requirements were not implemented:

- Suricata network intrusion detection integration.
- Atomic Red Team simulation.
- TheHive case management.
- Cortex analysis integration.
- Shuffle SOAR automated response.

These are identified as future enhancements rather than completed implementations.

## 9. Future Enhancements

- Integrate Suricata for network intrusion detection.
- Add additional MITRE ATT&CK detection rules.
- Integrate TheHive and Cortex for incident management.
- Implement Shuffle SOAR automation.
- Expand endpoint coverage and detection testing.

## 10. Author

**GitHub:** [@Harshavadhan25](https://github.com/Harshavadhan25)

**Project:** Security Operations Center Build-Out

**Domain:** Cybersecurity / Security Operations

---

This project was developed as a hands-on cybersecurity learning exercise.
