# 04 — Web Login Failure Detection

# 1. Overview

This phase demonstrates the detection and investigation of repeated failed web login activity against the Apache web application hosted on the monitored endpoint, **CITADEL**.

HTTP requests were generated against the web service to simulate unsuccessful authentication activity.

Apache recorded the requests in its web-server logs, while the Wazuh Agent collected the relevant telemetry and forwarded it to the Wazuh Manager running on **SENTINEL**.

The resulting security events were reviewed through the Wazuh Dashboard to demonstrate centralized web-application monitoring and investigation.

---

# 2. Objective

The objective of this exercise was to:

- Monitor Apache web-server activity
- Generate controlled failed web-login activity
- Collect web-server authentication telemetry
- Detect repeated failed login attempts
- Investigate the resulting Wazuh event
- Identify the source and target of the activity
- Analyze the available event details
- Document the detection and investigation process

---

# 3. Lab Environment

| System | Operating System | Role |
|---|---|---|
| **OCTOPUS** | Kali Linux | Security Testing / Attack Simulation |
| **CITADEL** | Ubuntu | Apache Web Server / Monitored Endpoint |
| **SENTINEL** | Ubuntu | Wazuh Manager / SIEM |
| **Windows 11 Host** | Windows 11 | Wazuh Dashboard Access |

The web application and Apache HTTP Server are hosted on CITADEL.

OCTOPUS is used to generate controlled HTTP requests against the web service.

The Wazuh Agent on CITADEL collects relevant log activity and forwards the events to SENTINEL for centralized monitoring.

---

# 4. Apache Web Server

Apache HTTP Server was configured on CITADEL as the monitored web service.

The Apache service was verified before generating web activity.

### Verify Apache Service

Run on CITADEL: $ sudo systemctl status apache2

The service status was checked to confirm that Apache was running correctly.

---
# 5. Web Login Activity

Controlled HTTP requests were generated against the web application to simulate unsuccessful login activity.

The requests generated web-server events that could be observed through the Apache logs.

The testing activity was performed against the authorized lab environment.

The purpose of the activity was to generate realistic web authentication telemetry for monitoring and detection.

---
# 6. Apache Log Monitoring

Apache records web requests and server activity in its log files.

The primary log locations used during the exercise were: 

# /var/log/apache2/access.log
# /var/log/apache2/error.log

The access log can be monitored using: 

# $ sudo tail -f /var/log/apache2/access.log

The error log can be monitored using:

# sudo tail -f /var/log/apache2/error.log

These logs provide visibility into HTTP requests, response status codes, client addresses, requested resources, and server-side errors.

---
## 7. Wazuh Monitoring

The Wazuh Agent running on CITADEL monitors configured log sources and forwards relevant events to the Wazuh Manager on SENTINEL.

Apache web-server logs provide telemetry that can be used to identify unusual or repeated web activity.

The Wazuh Dashboard was used to review the resulting security events.

The investigation focused on:

Source IP address
Target endpoint
Requested resource
HTTP activity
Authentication-related information
Detection rule
Alert level
Event frequency
Raw log information

---
## 8. Wazuh Detection

The generated web-login activity was reviewed through the Wazuh Dashboard.

The alert details were examined to determine whether the event contained sufficient information to identify the activity and affected endpoint.

Detection Information

Record the values shown in your actual Wazuh alert:

| Field                  |             Observed Value                    |
| ---------------------- | --------------------------------------------- |
| **Agent**              | CITADEL                                       |
| **Agent IP**           | `192.168.x.xxx`                               |
| **Source IP**          | `192.168.x.xxx`                               |
| **Rule ID**            | `30305`                                       |
| **Rule Level**         | `5`                                           |
| **Rule Description**   | `Attempt to acces forbiden file or directory` |
| **Event / Log Source** | Apache                                        |
| **HTTP Request**       | `GET`                                         |
---
## 9. Alert Investigation

The Wazuh alert was expanded to review the complete event information.

The following fields were examined where available:

agent.name
agent.ip
data.srcip
data.url
data.http
rule.id
rule.level
rule.description
full_log

The full_log field was used to review the original event information and provide additional context for the investigation.

---
# 10. Source and Target Analysis

The investigation focused on determining:

Source

The source IP represents the system that generated the HTTP request.

If the source IP corresponds to OCTOPUS, it can be documented as the security-testing system used during the lab exercise.

Target

The target endpoint was: CITADEL

CITADEL hosted the Apache web service and was the monitored endpoint receiving the HTTP requests.

The source and target information allows the analyst to establish which system generated the activity and which monitored endpoint received it.

---
# 11. Detection Evidence
## Screenshot 01 — Apache Service Running

This screenshot demonstrates that the Apache HTTP Server was running on CITADEL before the testing activity.

Evidence to highlight:

apache2 service
Active/running status
CITADEL hostname

Screenshot:

01-apache-service-running.png

Location: screenshots/04-web-login-failure/01-apache-service-running.png

---
## Screenshot 02 — Apache Web Logs

This screenshot demonstrates the web-server activity recorded by Apache.

Evidence to highlight:

HTTP requests
Source IP
Requested resource
HTTP response information
Authentication-related requests where visible

Screenshot:

02-apache-web-login-logs.png

Location: screenshots/04-web-login-failure/02-apache-web-login-logs.png

---
## Screenshot 03 — Wazuh Web Login Detection

This screenshot demonstrates the security event detected and displayed in the Wazuh Dashboard.

Evidence to highlight:

Agent name
Agent IP
Source IP
Rule ID
Rule level
Rule description
Event information

Screenshot:

03-wazuh-web-login-alert.png

Location:  screenshots/04-web-login-failure/03-wazuh-web-login-alert.png

---
## Screenshot 04 — Wazuh Alert Investigation

This screenshot shows the expanded alert and detailed event information used during the investigation.

Evidence to highlight:

Agent information
Source IP
Rule information
HTTP/web event fields
full_log
Relevant timestamps

Screenshot:

04-wazuh-web-login-investigation.png

Location:  screenshots/04-web-login-failure/04-wazuh-web-login-investigation.png

---
# 12. Investigation Process

The investigation followed a structured workflow:

- Apache was verified as running on CITADEL.
- Controlled web-login activity was generated against the application.
- Apache recorded the resulting HTTP activity.
- The Wazuh Agent collected the configured telemetry.
- Events were forwarded to SENTINEL.
- The Wazuh Dashboard was used to review the resulting event.
- Source and target information were examined.
- Detection-rule information was reviewed.
- The raw event data was examined for additional context.
- The activity was documented as part of the SOC investigation.

----
# 13. Detection Analysis

The exercise demonstrates how web-server telemetry can provide visibility into authentication-related activity.

Apache logs provide useful information about HTTP requests received by the server.

When these logs are collected centrally by Wazuh, the analyst can correlate web activity with other endpoint and security events.

The resulting visibility can assist with identifying:

- Repeated login failures
- Suspicious source addresses
- Unusual request patterns
- Authentication-related activity
- Web application reconnaissance
- Potential attack activity

The actual detection rule and alert severity should be interpreted using the information shown in the Wazuh event.

---
# 14. Security Recommendations

The following controls can help improve web-application security monitoring:

- Implement strong authentication controls.
- Apply rate limiting to authentication endpoints.
- Monitor repeated failed login attempts.
- Use secure session management.
- Validate and sanitize user input.
- Restrict administrative interfaces.
- Maintain centralized web-server logging.
- Monitor unusual source IP addresses.
- Investigate abnormal authentication patterns.
- Keep Apache and application components updated.
- Use appropriate WAF and intrusion-prevention controls where applicable.

---
# 15. Investigation Summary

| Investigation Element     |                     Observed Value                 |
| ------------------------- | -------------------------------------------------- |
| **Activity**              | Repeated web-login failures                        |
| **Source**                | `192.168.x.xxx`                                    |
| **Target**                | CITADEL                                            |
| **Service**               | Apache HTTP Server                                 |
| **Event Source**          | Apache logs                                        |
| **Detection Rule**        | `30305`                                            |
| **Rule Level**            | `5`                                                |
| **Detection Description** | `Attempt to access forbiden file or directory`     |
| **HTTP Request**          | `GET`                                              |
---
# 17. Phase Outcome

The web-login failure scenario demonstrated the collection and centralized monitoring of Apache web-server activity.

Controlled authentication-related web activity generated server-side telemetry on CITADEL, which was made available to the Wazuh monitoring infrastructure for detection and investigation.

The exercise demonstrated the SOC workflow of web activity generation → log collection → Wazuh monitoring → alert investigation → security analysis.

---


