# Security Operations Center (SOC) Build-Out Report

## 1. Executive Summary

This project involved building a small-scale Security Operations Center (SOC) monitoring environment using Splunk Enterprise as the Security Information and Event Management (SIEM) platform.

The environment collected and analyzed security events from a Windows host and an Ubuntu Server virtual machine. Windows Sysmon and Splunk Universal Forwarder provided endpoint telemetry, while the Ubuntu Universal Forwarder transmitted Linux system and authentication logs.

A centralized Splunk dashboard was developed to monitor failed logins, PowerShell process activity, administrator group changes, Linux authentication activity, and network connections.

The project demonstrates basic SIEM deployment, log collection, security event analysis, detection development, and dashboard-based monitoring.

## 2. Project Objectives

- Deploy a centralized SIEM platform.
- Collect security logs from Windows and Linux systems.
- Monitor endpoint and authentication activity.
- Identify suspicious activities through Splunk searches.
- Develop detection queries for important security events.
- Build a SOC monitoring dashboard.
- Document testing results and recommendations.

## 3. Lab Environment

| Component | Configuration |
|---|---|
| SIEM Platform | Splunk Enterprise |
| Host Operating System | Windows |
| Linux Endpoint | Ubuntu Server 24.04.5 LTS |
| Endpoint Monitoring | Windows Sysmon |
| Log Forwarding | Splunk Universal Forwarder |
| Splunk Web Interface | http://localhost:8000 |
| Receiving Port | 9997 |
| Log Index | main |
| Virtualization | Oracle VirtualBox |

The project was implemented using one Windows laptop and an Ubuntu virtual machine.

## 4. Tools and Technologies

- **Splunk Enterprise:** Centralized log collection, searching, analysis, alerting and visualization.
- **Windows Sysmon:** Captured detailed Windows process and network activity.
- **Splunk Universal Forwarder:** Forwarded Windows and Ubuntu logs to the Splunk server.
- **Ubuntu Server:** Provided Linux system and authentication logs.
- **Splunk Search Processing Language (SPL):** Used to search, filter and analyze security events.

## 5. Implementation

### 5.1 SIEM Deployment

Splunk Enterprise was installed and configured on the Windows host. The Splunk web interface was accessed locally.

The receiving port 9997 was enabled to accept forwarded events from endpoint systems.

### 5.2 Windows Endpoint Monitoring

Windows Sysmon was installed and configured to collect endpoint telemetry.

The configuration enabled monitoring of process creation, network connections, DNS queries and other relevant system activities.

Windows security events and Sysmon events were forwarded to Splunk for centralized analysis.

### 5.3 Linux Log Collection

An Ubuntu Server virtual machine was configured as a second monitoring endpoint.

Splunk Universal Forwarder was installed and configured on Ubuntu. It monitored:

- `/var/log/syslog`
- `/var/log/auth.log`

The collected Linux logs were forwarded to the Windows Splunk server through port 9997.

### 5.4 Centralized Log Analysis

Splunk received Windows and Ubuntu events in the `main` index.

Search queries were used to analyze authentication failures, process execution, administrator group changes and network connection activity.

## 6. Detection Use Cases

The following monitoring and detection use cases were implemented and tested.

| Detection Use Case | Event Source | Purpose |
|---|---|---|
| Windows Failed Logins | Windows Security Event ID 4625 | Identify repeated authentication failures |
| PowerShell Process Activity | Sysmon Event ID 1 | Monitor PowerShell process execution |
| Encoded PowerShell Indicators | Sysmon process events | Identify encoded PowerShell command indicators |
| Administrator Group Changes | Windows Security Event ID 4732 | Detect additions to local security groups |
| Linux Authentication Activity | Ubuntu auth.log | Monitor Linux authentication events |
| Network Connection Activity | Sysmon Event ID 3 | Monitor endpoint network connections |

These use cases were developed using Splunk searches and dashboard panels.

## 7. Alert Configuration

A scheduled Splunk alert named **SOC - Multiple Failed Windows Logins** was configured.

The alert search monitored Windows Security Event ID 4625 and evaluated whether the number of matching failed-login events reached five or more.

The alert was configured to run hourly over the previous 24 hours.

The alert configuration was saved and enabled. Successful alert triggering was not confirmed during the documented testing.

## 8. SOC Monitoring Dashboard

A centralized SOC dashboard was developed with five monitoring panels:

1. Windows Failed Login Activity
2. Ubuntu Authentication Activity
3. PowerShell Process Activity
4. Administrator Group Changes
5. Network Connection Activity

The dashboard provides a consolidated view of security events collected from both monitored endpoints.

## 9. Testing and Validation

The following controlled tests were performed:

- Windows failed-login events were generated and observed in Splunk.
- PowerShell process execution was monitored through Sysmon.
- A harmless encoded PowerShell test was performed to validate event visibility.
- A temporary local user was added to the Administrators group to verify Event ID 4732 detection. The temporary user was subsequently removed.
- Sysmon network connection events were collected and analyzed.
- Ubuntu authentication and system logs were verified in Splunk.

The tests confirmed that the configured log collection and monitoring searches were functioning.

## 10. MITRE ATT&CK Mapping

| Observed Activity | MITRE ATT&CK Technique | Technique ID |
|---|---|---|
| Repeated failed authentication attempts | Brute Force | T1110 |
| PowerShell execution | Command and Scripting Interpreter: PowerShell | T1059.001 |
| Administrator group modification | Account Manipulation | T1098 |
| Network connection monitoring | System Network Connections Discovery | T1049 |

These mappings describe the relevant behaviors monitored by the project. They do not imply that a complete adversary simulation was performed.

## 11. Implementation Limitations

The project was completed as a resource-constrained, two-endpoint SOC lab. The following components from the proposed full-scale architecture were not implemented:

- **Suricata:** Network IDS deployment and alert forwarding were not completed.
- **Atomic Red Team:** Formal Atomic Red Team attack simulations were not performed.
- **TheHive:** Case management integration was not deployed.
- **Cortex:** Automated observable analysis integration was not deployed.
- **Shuffle SOAR:** Automated incident response workflows were not configured.

The implemented environment therefore demonstrates SIEM-based endpoint and log monitoring, rather than a fully integrated SOC with network IDS and SOAR capabilities.

## 12. Recommendations and Future Enhancements

- Deploy Suricata to collect network intrusion detection alerts.
- Integrate Suricata alerts into Splunk.
- Conduct controlled Atomic Red Team simulations.
- Integrate TheHive for incident tracking and case management.
- Add Cortex for observable analysis.
- Configure Shuffle SOAR for automated response actions.
- Expand monitoring to additional endpoints.
- Develop more advanced detection rules mapped to MITRE ATT&CK.

## 13. Conclusion

The project successfully established a basic SOC monitoring environment using Splunk Enterprise, Windows Sysmon, and Splunk Universal Forwarder.

Security logs from Windows and Ubuntu were collected centrally, analyzed through Splunk searches, and displayed through a five-panel monitoring dashboard.

The project provided practical experience in SIEM deployment, endpoint monitoring, log forwarding, security event analysis, detection development and alert configuration.

The completed implementation provides a foundation for future expansion into network intrusion detection, incident management and security orchestration.

## 14. Evidence Directory

Screenshots and configuration evidence are maintained in the project's Evidence directory.

Evidence includes:

- Splunk Enterprise running.
- Sysmon events received.
- Windows security event analysis.
- Ubuntu log collection and authentication monitoring.
- Failed-login monitoring.
- PowerShell activity and encoded-command indicators.
- Administrator group change detection.
- Sysmon network connection monitoring.
- Final SOC monitoring dashboard.

**Project Evidence Location:** `E:\SOC-Project\Evidence`

**Report Location:** `E:\SOC-Project\Reports`