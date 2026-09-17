# 02 — Agent Integration

## 1. Overview

This phase documents the integration of the monitored Ubuntu endpoint, **CITADEL**, with the centralized Wazuh infrastructure running on **SENTINEL**.

The Wazuh Agent installed on CITADEL collects endpoint and application security telemetry and forwards the collected events to the Wazuh Manager.

Successful agent integration provides the endpoint visibility required for centralized security monitoring, alert generation, investigation, and MITRE ATT&CK analysis.

---

## 2. Lab Environment

| System | Operating System | Role |
|---|---|---|
| **CITADEL** | Ubuntu | Wazuh Agent / Monitored Endpoint |
| **SENTINEL** | Ubuntu | Wazuh Manager / SIEM Server |
| **Windows 11 Host** | Windows 11 | VirtualBox Host / Dashboard Access |

CITADEL is the monitored endpoint in this phase.

SENTINEL hosts the centralized Wazuh infrastructure used to receive, process, store, and display security events.

The Windows 11 host is used to access the Wazuh Dashboard through a web browser and is **not configured as a Wazuh Agent**.

---

## 3. Wazuh Agent Installation

The Wazuh Agent was installed on the **CITADEL** Ubuntu endpoint.

The agent provides endpoint telemetry collection and forwards relevant security events to the Wazuh Manager running on SENTINEL.

After installation, the Wazuh Agent service was enabled and started.

### Verify Wazuh Agent Service

Run the following command on CITADEL:  $ sudo systemctl status wazuh-agent
 
The service status was checked to confirm that the Wazuh Agent was running correctly.

---
## 4. Agent Registration

After installing the Wazuh Agent, CITADEL was registered with the Wazuh Manager running on SENTINEL.

Agent registration allows the Wazuh Manager to identify CITADEL as a monitored endpoint and receive telemetry from it.

The Wazuh Agent configuration was updated with the address of the Wazuh Manager.

After applying the configuration, the agent service was restarted.

# $ sudo systemctl restart wazuh-agent

The agent configuration and service state were then verified before continuing with the integration validation.

---
## 5. Agent Connectivity Verification

The Wazuh Agent service was first verified locally on CITADEL.

$ sudo systemctl status wazuh-agent

The Wazuh Manager was then checked from SENTINEL to verify that the registered agent was visible.

$ sudo /var/ossec/bin/agent_control -l

The command displays the agents registered with the Wazuh Manager.

The expected result is for CITADEL to appear in the registered-agent list.

---
## 6. Agent Status in Wazuh Dashboard

The Wazuh Dashboard was accessed from the Windows 11 host using a web browser.

The Agents section was used to verify the integration status of CITADEL.

The following information was reviewed:

Agent name
Agent status
Agent IP address
Operating system
Last Keep Alive

CITADEL appearing as Active confirms that the Wazuh Agent is communicating with the Wazuh Manager.

--- 
## 7. Agent Integration Evidence
### Screenshot 01 — Wazuh Agent Service

This screenshot demonstrates that the Wazuh Agent service is installed and running on CITADEL.

Evidence to highlight:

wazuh-agent service
Active/running status
CITADEL hostname

Screenshot:

01-wazuh-agent-service.png

Location: screenshots/02-agent-integration/01-wazuh-agent-service.png

---
### Screenshot 02 — Agent Registration

This screenshot demonstrates that CITADEL has been registered with the Wazuh Manager.

Evidence to highlight:

CITADEL agent entry
Agent ID
Agent status
Registration information

Screenshot:

02-agent-registration.png

Location: screenshots/02-agent-integration/02-agent-registration.png

---
### Screenshot 03 — Active Agent in Wazuh Dashboard

This screenshot provides visual confirmation that CITADEL is successfully communicating with the Wazuh Manager.

Evidence to highlight:

Agent name: CITADEL
Status: Active
Agent IP address
Operating system
Last Keep Alive

Screenshot:

03-agent-active-dashboard.png

Location: screenshots/02-agent-integration/03-agent-active-dashboard.png

---
## 8. Telemetry Collection

Once the Wazuh Agent is active, CITADEL can provide security and application telemetry to the Wazuh Manager.

The lab uses multiple telemetry sources to support the detection scenarios implemented in later phases.

Endpoint Telemetry
System logs
Authentication events
SSH activity
Process activity
Security events
Application Telemetry
Apache access logs
Apache error logs
Web-server activity

These telemetry sources provide the event data required for centralized monitoring and security detection.

---
## 9. Agent Integration Validation

The integration was validated using the following checks:
| Validation                            | Expected Result |
| ------------------------------------- | --------------- |
| Wazuh Agent installed                 | Successful      |
| Wazuh Agent service running           | Active          |
| CITADEL registered with Wazuh Manager | Successful      |
| CITADEL visible in agent list         | Yes             |
| Agent communication                   | Active          |
| CITADEL visible in Dashboard          | Yes             |
| Endpoint telemetry available          | Yes             |

Successful completion of these checks confirms that CITADEL is integrated into the Wazuh monitoring environment.

---
## 10. Troubleshooting

Agent connectivity can be affected by changes to the VirtualBox network configuration, Wazuh Manager address, or agent configuration.

The following checks can be used when troubleshooting the integration.

Check Wazuh Agent Service
$ sudo systemctl status wazuh-agent

Restart Wazuh Agent
$ sudo systemctl restart wazuh-agent

Check Registered Agents

Run on SENTINEL: $sudo /var/ossec/bin/agent_control -l

Check Wazuh Agent Logs

Run on CITADEL: $ sudo tail -f /var/ossec/logs/ossec.log

These checks help identify issues related to the agent service, registration, configuration, or communication with the Wazuh Manager.

---
11. Integration Outcome

CITADEL was successfully integrated with the Wazuh monitoring infrastructure running on SENTINEL.

The completed integration provides centralized visibility into endpoint and application security activity generated on CITADEL.

The monitored endpoint can now provide telemetry for:

SSH authentication activity
Apache web-server activity
System events
Security events
Process activity
Other configured endpoint telemetry

This telemetry forms the foundation for the detection and investigation scenarios documented in the following phases.

---
## 12. Evidence Summary
| Screenshot                      | Evidence                                                |
| ------------------------------- | ------------------------------------------------------- |
| `01-wazuh-agent-service.png`    | Wazuh Agent service running on CITADEL                  |
| `02-agent-registration.png`     | CITADEL registered with the Wazuh Manager               |
| `03-agent-active-dashboard.png` | CITADEL shown as an active agent in the Wazuh Dashboard |
---
## 13. Phase Result

CITADEL was successfully integrated with the centralized Wazuh monitoring infrastructure.

The Wazuh Agent provides endpoint telemetry to SENTINEL, where security events can be processed, monitored, investigated, and correlated with MITRE ATT&CK techniques.

The completed agent integration establishes the monitoring foundation required for the subsequent reconnaissance, attack simulation, detection, and investigation phases.
