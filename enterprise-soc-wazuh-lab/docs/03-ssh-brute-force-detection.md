# 03 — SSH Brute-Force Detection

## 1. Overview

This phase demonstrates the simulation, detection, and investigation of an SSH brute-force attack within the SOC lab environment.

Controlled SSH authentication attempts were generated from **OCTOPUS**, the Kali Linux security-testing machine, against **CITADEL**, the monitored Ubuntu endpoint.

The Wazuh Agent on CITADEL collected the resulting authentication events and forwarded them to **SENTINEL**, where the Wazuh Manager generated a security alert.

The alert was then investigated through the Wazuh Dashboard and mapped to the corresponding MITRE ATT&CK technique.

---

## 2. Objective

The objective of this exercise was to:

- Simulate repeated SSH authentication attempts
- Generate failed SSH authentication events
- Collect authentication telemetry using the Wazuh Agent
- Detect excessive authentication attempts using Wazuh
- Investigate the resulting security alert
- Identify the source and target of the activity
- Map the activity to MITRE ATT&CK
- Document the investigation and security response

---

## 3. Lab Environment

| System | Operating System | Role |
|---|---|---|
| **OCTOPUS** | Kali Linux | Attacker / Security Testing |
| **CITADEL** | Ubuntu | SSH Target / Monitored Endpoint |
| **SENTINEL** | Ubuntu | Wazuh Manager / SIEM |
| **Windows 11 Host** | Windows 11 | Wazuh Dashboard Access |

The attack activity was generated from OCTOPUS against the SSH service running on CITADEL.

CITADEL's Wazuh Agent collected the resulting authentication events and forwarded them to SENTINEL for centralized detection and investigation.

---

## 4. Attack Simulation

The SSH brute-force activity was simulated from OCTOPUS using **Hydra**.

The attack attempted multiple password combinations against the SSH service running on CITADEL.

Example command: $ hydra -l citadel -P /usr/share/wordlists/rockyou.txt ssh://<CITADEL-IP> -V

---
# Command Parameters
| Parameter     | Description                           |
| ------------- | ------------------------------------- |
| `-l citadel`  | Specifies the target username         |
| `-P`          | Specifies the password wordlist       |
| `rockyou.txt` | Password dictionary used for the test |
| `ssh://`      | Specifies SSH as the target protocol  |
| `-V`          | Displays individual login attempts    |

The activity was performed in the controlled lab environment against the authorized CITADEL endpoint.

---
# 5. SSH Authentication Activity

The repeated authentication attempts generated failed SSH authentication events on CITADEL.

These events were recorded by the SSH service and made available through the system authentication logs.

The authentication activity provides the underlying telemetry used by Wazuh for detection.

Example log location on Ubuntu: 

 /var/log/auth.log
 
The authentication log can be reviewed using:

   sudo tail -f /var/log/auth.log

The resulting entries can be used to identify repeated authentication failures and the source of the connection attempts.

---
# 6. Wazuh Detection

The Wazuh Agent on CITADEL collected the authentication activity and forwarded the events to the Wazuh Manager running on SENTINEL.

Wazuh identified the repeated authentication activity and generated an alert indicating that the maximum number of authentication attempts had been exceeded.

| Field                | Value                                    |
| -------------------- | ---------------------------------------- |
| **Agent**            | CITADEL                                  |
| **Agent IP**         | 192.168.x.xxx                            |
| **Source IP**        | 192.168.x.xxx                            |
| **Rule ID**          | 5758                                     |
| **Rule Level**       | 8                                        |
| **Rule Description** | Maximum authentication attempts exceeded |
| **Fired Times**      | 15                                       |
| **MITRE ID**         | T1110                                    |
| **Tactic**           | Credential Access                        |
| **Technique**        | Brute Force                              |

The alert indicates repeated authentication activity against the monitored SSH service.

---
# 7. Wazuh Alert Investigation

The generated alert was investigated using the Wazuh Dashboard.

The alert details provide information about the monitored endpoint, source of the authentication attempts, detection rule, and MITRE ATT&CK classification.

Key Investigation Fields

The following fields were reviewed during the investigation:

agent.name
agent.ip
data.srcip
rule.id
rule.level
rule.description
rule.firedtimes
rule.mitre.id
rule.mitre.tactic
rule.mitre.technique
full_log

These fields help establish the relationship between the source system, targeted endpoint, detection rule, and observed authentication activity.

---
# 8. Source and Target Analysis

The Wazuh alert identified:

Target Endpoint: 
  CITADEL
192.168.x.xxx

Source IP : 192.168.x.xxx

The source IP should correspond to OCTOPUS, the Kali Linux attack machine, based on the network configuration used during the exercise.

The full_log field provides additional context regarding the excessive authentication attempts.

---
# 9. MITRE ATT&CK Mapping

The detected activity was mapped by Wazuh to:
| MITRE ATT&CK Field | Value             |
| ------------------ | ----------------- |
| **Technique ID**   | T1110             |
| **Technique**      | Brute Force       |
| **Tactic**         | Credential Access |

MITRE ATT&CK T1110 — Brute Force covers techniques involving repeated attempts to obtain access by guessing or trying multiple credentials.

The Wazuh alert therefore provides both detection information and ATT&CK context for the observed authentication activity.

---
# 10. Detection Evidence
## Screenshot 01 — SSH Brute-Force Attack

This screenshot shows the controlled SSH authentication attack being generated from OCTOPUS using Hydra.

Evidence to highlight:

Hydra command
Target SSH service
Target IP address
Username
Password wordlist
Repeated authentication attempts

Screenshot:

01-ssh-brute-force-attack.png

Location:  screenshots/03-ssh-brute-force/01-ssh-brute-force-attack.png

---
## Screenshot 02 — Failed SSH Authentication Logs

This screenshot shows the authentication failures recorded on CITADEL.

Evidence to highlight:

Failed authentication entries
SSH service
Source IP address
Target username
Repeated authentication activity

Screenshot:

02-failed-ssh-authentication-logs.png

Location:  screenshots/03-ssh-brute-force/02-failed-ssh-authentication-logs.png

---
## Screenshot 03 — Wazuh SSH Brute-Force Alert

This screenshot demonstrates the Wazuh detection generated from the authentication activity.

Evidence to highlight:

Agent: CITADEL
Agent IP: 192.168.0.103
Source IP: 192.168.0.102
Rule ID: 5758
Rule level: 8
Rule description
Fired times

Screenshot:

03-wazuh-ssh-brute-force-alert.png

Location:  screenshots/03-ssh-brute-force/03-wazuh-ssh-brute-force-alert.png

---
## Screenshot 04 — Wazuh Alert Investigation

This screenshot shows the expanded Wazuh alert containing the detailed event information.

Evidence to highlight:

agent.name
agent.ip
data.srcip
rule.id
rule.level
rule.description
rule.firedtimes
rule.mitre.id
rule.mitre.tactic
rule.mitre.technique
full_log

Screenshot:

04-wazuh-alert-investigation.png

Location:   screenshots/03-ssh-brute-force/04-wazuh-alert-investigation.png

---
# 11. Detection Analysis

The detection process demonstrated the following sequence:

Repeated SSH authentication attempts were generated from OCTOPUS.
CITADEL recorded the resulting authentication failures.
The Wazuh Agent collected the authentication telemetry.
The events were forwarded to SENTINEL.
Wazuh generated an alert after the authentication threshold was exceeded.
The alert identified the source and monitored endpoint.
The event was mapped to MITRE ATT&CK T1110 — Brute Force.
The alert was investigated through the Wazuh Dashboard.

This demonstrates the ability of the SOC lab to collect authentication telemetry and provide centralized detection and investigation.

---
# 12. Security Recommendations

The following controls can help reduce exposure to SSH brute-force activity:

- Use strong and unique authentication credentials.
- Prefer SSH key-based authentication where appropriate.
- Disable password authentication when operationally feasible.
- Restrict SSH access to trusted networks or management hosts.
- Implement rate limiting or intrusion-prevention controls.
- Monitor repeated authentication failures.
- Review SSH configuration and authentication policies.
- Investigate unusual source IP addresses and repeated authentication attempts.
- Maintain centralized security logging and alerting.

---
# 13. Investigation Summary
| Investigation Element | Observed Value                           |
| --------------------- | ---------------------------------------- |
| Activity              | Repeated SSH authentication attempts     |
| Source                | OCTOPUS / `192.168.0.102`                |
| Target                | CITADEL / `192.168.0.103`                |
| Service               | SSH                                      |
| Detection Rule        | `5758`                                   |
| Rule Level            | `8`                                      |
| Detection Description | Maximum authentication attempts exceeded |
| Fired Times           | `15`                                     |
| MITRE Technique       | `T1110`                                  |
| MITRE Tactic          | Credential Access                        |
| Technique             | Brute Force                              |

---
# 14. Phase Outcome

The SSH brute-force simulation successfully generated authentication activity against the CITADEL endpoint.

The Wazuh Agent collected the resulting authentication telemetry and the Wazuh Manager generated a security alert identifying excessive authentication attempts.

The alert provided source, target, detection-rule, and MITRE ATT&CK information that enabled further investigation through the Wazuh Dashboard.

This phase demonstrates the complete workflow of attack simulation → telemetry collection → detection → alert investigation → MITRE ATT&CK mapping within the SOC lab.
