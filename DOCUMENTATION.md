# SOC Build-Out – Technical Documentation

## 1. Project Information

| Field | Details |
|---|---|
| Project | Security Operations Center Build-Out |
| Domain | Cybersecurity |
| SIEM Platform | Splunk Enterprise |
| Windows Endpoint | Windows 11 |
| Linux Endpoint | Ubuntu Server 24.04.5 |
| Monitoring Tool | Sysmon |
| Log Forwarding | Splunk Universal Forwarder |

## 2. System Architecture

The SOC environment uses a centralized log monitoring architecture.

**Data flow:**

1. Windows endpoint generates system and security events.
2. Sysmon collects detailed Windows process and network activity.
3. Windows Universal Forwarder forwards Windows logs.
4. Ubuntu Server generates system and authentication logs.
5. Ubuntu Universal Forwarder forwards Linux logs.
6. Splunk Enterprise receives and indexes the forwarded events.
7. Splunk Search and dashboards provide centralized monitoring and analysis.

Refer to `SOC-Architecture.png` for the architecture diagram. The editable source is available as `SOC-Architecture.drawio`.

## 3. Data Sources

### Windows Endpoint

Windows monitoring includes:

- Windows Security Event Logs.
- Sysmon Operational Event Logs.
- Process creation activity.
- Network connection activity.
- Authentication events.
- Administrator group modification events.

### Ubuntu Server

Linux monitoring includes:

- `/var/log/syslog`
- `/var/log/auth.log`

These files provide system activity and authentication-related information.

## 4. Network and Port Configuration

| Component | Port | Purpose |
|---|---:|---|
| Splunk Web | 8000 | Web interface and dashboard access |
| Splunk Receiving Port | 9997 | Receives forwarded log data |

The Windows and Ubuntu Universal Forwarders send collected events to the Splunk receiving service.

## 5. Event Monitoring and Detection

The following event types were monitored during testing:

| Event ID | Source | Monitoring purpose |
|---|---|---|
| 4625 | Windows Security | Failed login attempts |
| 4732 | Windows Security | Member added to a security-enabled local group |
| 1 | Sysmon | Process creation |
| 3 | Sysmon | Network connection activity |

### MITRE ATT&CK Mapping

| Technique | ID | Use case |
|---|---|---|
| Brute Force | T1110 | Repeated failed authentication |
| PowerShell | T1059.001 | PowerShell activity monitoring |
| Account Manipulation | T1098 | Administrator group modification |
| System Network Connections Discovery | T1049 | Network activity monitoring |

These mappings describe the detection use cases and monitored activities.

## 6. Splunk Dashboard

The SOC dashboard contains five monitoring panels:

1. Windows Failed Login Activity
2. Ubuntu Authentication Activity
3. PowerShell Process Activity
4. Administrator Group Changes
5. Network Connection Activity

The dashboard definition is included in `SOC-Dashboard.xml`.

## 7. Alert Configuration

A scheduled Splunk alert was configured:

**Alert name:** SOC - Multiple Failed Windows Logins

- Data source: Windows Security Events
- Event ID: 4625
- Threshold: Five or more matching events
- Search window: Previous 24 hours
- Schedule: Hourly

The alert configuration was enabled. Successful automatic triggering was not independently verified.

## 8. Testing and Validation

The following controlled tests were performed:

| Test | Validation |
|---|---|
| Windows failed-login activity | Events observed in Splunk |
| PowerShell process activity | Sysmon process events observed |
| Harmless encoded PowerShell test | Related activity detected |
| Administrator group modification | Event ID 4732 observed |
| Sysmon network monitoring | Event ID 3 events observed |
| Ubuntu authentication monitoring | Authentication logs received |

Evidence screenshots are available in the `Evidence` files.

## 9. API Documentation

This project does not implement a custom REST API or expose application API endpoints.

Log collection and communication are performed through Splunk Universal Forwarders and the Splunk receiving service.

## 10. Implementation Limitations

The implemented environment focuses on endpoint monitoring and centralized SIEM log analysis.

The following components were not deployed:

- Suricata
- Atomic Red Team
- TheHive
- Cortex
- Shuffle SOAR

These are potential future enhancements.

## 11. Future Enhancements

- Integrate Suricata for network intrusion detection.
- Expand MITRE ATT&CK detection coverage.
- Add Atomic Red Team testing.
- Integrate TheHive and Cortex for incident management.
- Implement Shuffle SOAR automation.
- Expand endpoint monitoring.

## 12. Project Author

**GitHub:** [Harshavadhan25](https://github.com/Harshavadhan25)

**Repository:** SOC-Build-Out-Splunk

**Project:** Security Operations Center Build-Out
