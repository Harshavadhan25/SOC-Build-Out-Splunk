# Individual Learning Reflection – SOC Build-Out

**Project:** Security Operations Center (SOC) Build-Out  
**Technology:** Splunk Enterprise, Sysmon, Windows 11, Ubuntu Server  
**Track:** Cybersecurity  
**Intern:** Harsha Vardhan

## 1. Work and Responsibilities

I worked on building a basic Security Operations Center monitoring environment using Splunk Enterprise as the SIEM platform.

My responsibilities included:

- Setting up Splunk Enterprise and configuring log collection.
- Installing and configuring Sysmon on Windows.
- Configuring Splunk Universal Forwarders on Windows and Ubuntu.
- Collecting Windows Event Logs, Sysmon events, and Ubuntu authentication and system logs.
- Creating SPL searches to investigate security-related activity.
- Building a dashboard with five monitoring panels.
- Configuring a Windows failed-login alert.
- Performing controlled testing and capturing evidence.
- Preparing technical documentation and the project report.

## 2. Skills Learned

Through this project, I developed practical knowledge of:

- SIEM concepts and centralized log monitoring.
- Windows security events and Sysmon telemetry.
- Linux authentication and system logs.
- Splunk searches and dashboard creation.
- Security event investigation and basic detection logic.
- Identifying authentication failures, PowerShell activity, account changes, and network connections.
- Technical documentation and evidence collection.

## 3. Challenges Faced

Some of the main challenges were configuring log forwarding correctly, identifying the right event fields, writing SPL queries, and presenting different security events clearly in a single dashboard.

I addressed these challenges by testing configurations, reviewing collected events, refining searches, and validating the dashboard using controlled activity.

## 4. Key Takeaways

I learned that effective security monitoring requires more than simply collecting logs. Analysts must understand event sources, identify meaningful patterns, create appropriate detection logic, and validate alerts.

This project also improved my confidence in working with Windows and Linux security logs and using SIEM tools.

## 5. Future Improvements

Given additional time and resources, I would extend the environment by integrating Suricata for network intrusion detection, conducting Atomic Red Team simulations, and connecting TheHive, Cortex, and Shuffle for case management and automated response.

These are planned improvements and were not implemented in the current project.

## 6. Conclusion

This project provided valuable hands-on exposure to SOC operations and SIEM-based security monitoring. It strengthened my foundational cybersecurity skills and gave me a clearer understanding of how security events are collected, analyzed, and investigated in a monitoring environment.
