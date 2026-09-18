# 07 — Lessons Learned

# 1. Overview

Building the Enterprise SOC Lab provided practical experience across both offensive security and defensive monitoring.

The project combined Kali Linux security testing, an Ubuntu monitored endpoint, Apache web-server telemetry, SSH authentication monitoring, and centralized Wazuh SIEM analysis.

The lab demonstrated how security activity generated on an endpoint can be collected, analyzed, and investigated from a centralized SOC monitoring platform.

---
# 2. Project Objectives Achieved

The project was designed to provide hands-on experience with:

- SOC monitoring
- Security-event collection
- Endpoint monitoring
- Log analysis
- Web-server monitoring
- SSH authentication monitoring
- Security-event investigation
- Web reconnaissance
- Directory enumeration
- Alert analysis
- MITRE ATT&CK contextualization

The completed environment provided a controlled platform for performing these activities and examining their resulting security telemetry.

---
# 3. Lab Architecture Lessons

One of the main lessons from the project was the importance of separating security-testing systems from monitored systems and the SIEM infrastructure.

The lab used three dedicated virtual machines:

| System | Role |
|---|---|
| OCTOPUS | Attacker / Security Testing |
| CITADEL | Monitored Endpoint |
| SENTINEL | Wazuh SIEM Server |

The Windows 11 host was used to run the VirtualBox environment and access the Wazuh Dashboard.

This separation made it possible to generate controlled activity from OCTOPUS, observe the resulting telemetry on CITADEL, and investigate the events centrally through SENTINEL.

---
# 4. Endpoint Monitoring Lessons

Installing the Wazuh Agent on CITADEL demonstrated the importance of endpoint telemetry in a SOC environment.

The monitored endpoint provided telemetry from multiple sources, including:

- SSH authentication logs
- Apache access logs
- System logs
- Security-related events

The Wazuh Agent provided a centralized method of forwarding these events to the Wazuh infrastructure.

A key lesson was that effective monitoring depends on the availability, quality, and correct configuration of the underlying log sources.

---
# 5. Apache Monitoring Lessons

The Apache monitoring phase demonstrated how application-level telemetry can provide useful security visibility.

Apache access logs contain information such as:

- Source IP address
- Timestamp
- HTTP method
- Requested resource
- HTTP response code
- User-Agent

These fields can provide valuable context during investigation.

For example, the directory-enumeration investigation exposed a request containing:

### GET /externalization HTTP/1.1

and the User-Agent:

### gobuster/3.8.2

This demonstrated how application logs can help correlate security-testing activity with SIEM events.

---
# 6. SSH Monitoring Lessons

The SSH brute-force exercise demonstrated how repeated authentication failures can become detectable security events.

The investigation showed that authentication activity can be analyzed using:

- Source IP address
- Authentication result
- Timestamp
- Affected endpoint
- Wazuh rule information
- Event frequency

The lab also demonstrated the importance of distinguishing between an individual failed authentication attempt and a larger pattern of repeated authentication failures.

---
# 7. Directory Enumeration Lessons

The directory-enumeration exercise demonstrated that reconnaissance activity can generate a significant amount of application telemetry.

Gobuster generated multiple HTTP requests against the Apache server.

Apache recorded those requests, and Wazuh collected the resulting access-log events.

The investigation demonstrated that individual HTTP events can contain useful indicators such as:

- Requested URI
- HTTP method
- HTTP response
- Source IP
- User-Agent

The presence of the Gobuster User-Agent in the raw Apache event provided a useful correlation point during investigation.

---
# 8. Log Analysis Lessons

A major lesson from the project was the importance of examining the original event data rather than relying only on the alert description.

A Wazuh alert provides detection context through fields such as:

#### rule.description
#### rule.id
#### rule.level

However, the underlying event can provide additional information through:

#### full_log

and other parsed fields.

During investigation, reviewing the raw event helped establish what actually occurred and provided additional context that was not necessarily visible from the rule description alone.

---
# 9. Event Correlation Lessons

Individual alerts do not always provide the complete picture.

A SOC investigation can require correlation between multiple telemetry sources.

For example:

| Activity                    | Supporting Telemetry                         |
| --------------------------- | -------------------------------------------- |
| SSH authentication activity | SSH authentication logs + Wazuh              |
| Apache web activity         | Apache access logs + Wazuh                   |
| Directory enumeration       | Gobuster output + Apache access logs + Wazuh |
| Incident investigation      | Wazuh alert + raw event + related events     |

Comparing timestamps, source addresses, affected endpoints, and application information can help determine whether events are related.

---
# 10. Importance of Accurate Evidence

The project also demonstrated the importance of documenting only what can be supported by actual evidence.

During security investigations, the following information should be taken directly from the observed event whenever possible:

- Agent name
- Agent IP
- Source IP
- Timestamp
- Requested resource
- Rule ID
- Rule level
- Rule description
- Raw log
- MITRE ATT&CK mapping

Detection rules should not automatically be described as detecting a specific attack technique unless the evidence and rule context support that interpretation.

This approach helps maintain accuracy in SOC documentation and incident reports.

---
# 11. MITRE ATT&CK Lessons

MITRE ATT&CK provided a standardized way of adding behavioral context to security events.

For example, the SSH brute-force investigation included:

#### MITRE ATT&CK ID: T1110
#### Tactic: Credential Access
#### Technique: Brute Force

The mapping helped describe the behavior using a standardized security framework.

However, MITRE ATT&CK information should be considered alongside the underlying event data rather than used as a replacement for investigation.

---
# 12. Investigation Lessons

The incident-investigation phase demonstrated a structured approach to analyzing security events.

A practical investigation sequence is:

- Identify the relevant alert.
- Review the event timestamp.
- Identify the affected endpoint.
- Examine the source information.
- Review the detection rule.
- Examine the raw event.
- Correlate related events.
- Review available MITRE ATT&CK context.
- Document the evidence and findings.

This workflow provides a repeatable process for investigating security events in a SOC environment.

---
# 13. Challenges Encountered

The project also highlighted several practical challenges that can occur when building a home SOC lab.

Network Changes

Virtual machine IP addresses can change depending on the VirtualBox network configuration.

This means IP addresses should be verified before performing an investigation or documenting an attack path.

Agent Connectivity

Wazuh Agent connectivity depends on correct configuration and communication between the monitored endpoint and Wazuh server.

An agent appearing disconnected requires verification of:

- Agent service status
- Network connectivity
- Wazuh configuration
- Registration information
- Server availability
- Log Availability

Security monitoring depends on the relevant log source being available and correctly configured.

For Apache monitoring, the relevant source was:

#### /var/log/apache2/access.log

For SSH monitoring, authentication logs provided the relevant telemetry.

Alert Interpretation

A Wazuh alert does not necessarily describe the complete security activity.

The rule description, rule ID, severity, parsed fields, and raw log should be considered together during investigation.

---
# 14. Defensive Security Lessons

The lab demonstrated that effective security monitoring requires visibility across multiple layers.

Useful telemetry can originate from:

- Operating-system logs
- Authentication services
- Web servers
- Network activity
- Security applications
- SIEM detection rules

Centralizing these events allows analysts to investigate activity from a common monitoring platform.

The quality of the investigation is therefore strongly influenced by the quality and completeness of the telemetry being collected.

---
# 15. Skills Practiced

The project provided hands-on practice with the following technologies and concepts:

## Security Monitoring
- Wazuh
- Wazuh Dashboard
- Wazuh Agent
- Security event analysis
- Alert investigation
## Linux
- Ubuntu administration
- Kali Linux
- System services
- Log files
- SSH
- Apache
## Web Security
- HTTP
- Apache access logs
- Web reconnaissance
- Directory enumeration
- Gobuster
- Nikto
## Offensive Security
- Nmap
- Gobuster
- Nikto
- Hydra
- Controlled attack simulation
## SOC Analysis
- Log analysis
- Event correlation
- Source and target analysis
- Timeline analysis
- Detection analysis
- MITRE ATT&CK contextualization

---
# 16. Improvements for Future Versions

The current lab can be expanded with additional monitoring and detection capabilities.

Potential improvements include:

- Adding a Windows endpoint with Sysmon telemetry.
- Adding additional Linux monitored endpoints.
- Integrating network monitoring tools.
- Creating custom Wazuh detection rules.
- Building additional correlation rules.
- Monitoring authentication and privilege-escalation activity.
- Adding more web-server detection scenarios.
- Creating automated incident-response actions.
- Integrating additional security telemetry sources.
- Developing more structured incident-response playbooks.

These improvements would increase the amount and variety of telemetry available for SOC investigation.

---
# 17. Key Takeaways

The main lessons from the project were:

- Security monitoring starts with good telemetry.

Logs must be available, correctly collected, and sufficiently detailed to support investigation.

- Detection and investigation are different activities.

A detection identifies potentially relevant activity, while investigation determines what the event represents by examining its context and supporting evidence.

- Raw logs are important.

Parsed Wazuh fields and rule descriptions provide useful context, but the original event can contain additional information required for accurate analysis.

- Correlation provides context.

Connecting attacker activity, application logs, endpoint telemetry, and SIEM events can provide a clearer understanding of an incident.

- Accurate documentation matters.

Security findings should be based on observed evidence rather than assumptions about what a detection rule represents.

- SOC monitoring requires multiple telemetry sources.

Authentication, application, system, and security events can complement each other during investigation.

---
# 18. Final Project Outcome

The Enterprise SOC Lab provided a controlled environment for practicing both offensive security activity and defensive security monitoring.

The completed lab demonstrated:

- Deployment of a Wazuh monitoring environment.
- Integration of a monitored Ubuntu endpoint.
- Collection of SSH and Apache telemetry.
- Detection of security-relevant activity.
- Investigation of individual Wazuh events.
- Correlation of offensive activity with endpoint telemetry.
- Use of MITRE ATT&CK for security-event context.
- Centralized security monitoring through the Wazuh Dashboard.

The project established a practical foundation for continued development of SOC monitoring, detection engineering, incident investigation, and defensive security skills.

---
# 19. Project Documentation

The complete project documentation is organized into the following phases:

| Document                                | Focus                                    |
| --------------------------------------- | ---------------------------------------- |
| `01-lab-architecture.md`                | Lab architecture and system roles        |
| `02-agent-integration.md`               | Wazuh Agent deployment and integration   |
| `03-ssh-brute-force-detection.md`       | SSH brute-force monitoring and detection |
| `04-web-login-failure-detection.md`     | Web authentication failure monitoring    |
| `05-directory-enumeration-detection.md` | Directory enumeration monitoring         |
| `06-incident-investigation.md`          | Security-event investigation             |
| `07-lessons-learned.md`                 | Project lessons and future improvements  |
---
# 20. Conclusion

This project provided practical experience in building and operating a small-scale SOC monitoring environment.

The combination of controlled security testing, endpoint telemetry, application logging, centralized Wazuh monitoring, event correlation, and incident investigation demonstrates the complete lifecycle from security activity generation to defensive analysis.

The lab can serve as a foundation for future work involving detection engineering, threat hunting, incident response, SIEM administration, and SOC operations.

---


