# 01 — SOC Lab Architecture

## 1. Architecture Overview

This project implements an enterprise-style Security Operations Center (SOC) lab using VirtualBox and Wazuh.

The lab consists of three primary virtual machines:

- **OCTOPUS** — Kali Linux attacker machine
- **CITADEL** — Ubuntu monitored endpoint
- **SENTINEL** — Ubuntu Wazuh SIEM server

The architecture demonstrates the complete flow from attack activity and endpoint telemetry to centralized detection, investigation, and MITRE ATT&CK mapping.

---
# 3. Machine Roles
## 3.1 OCTOPUS — Attacker

Operating System: Kali Linux

OCTOPUS is the security testing machine used to generate controlled reconnaissance and attack activity against the authorized lab environment.

Tools Used
Nmap
Nikto
Gobuster
Hydra
cURL
Primary Activities
Network reconnaissance
Service enumeration
Web reconnaissance
Directory enumeration
SSH authentication testing
HTTP request generation

---

## 3.2 CITADEL — Monitored Endpoint

Operating System: Ubuntu

CITADEL is the monitored endpoint in the SOC environment.

Components
Wazuh Agent
Apache HTTP Server
SSH

The endpoint generates authentication, web-server, and system security logs.

The Wazuh Agent collects relevant security telemetry and forwards it to the Wazuh Manager running on SENTINEL.

Primary Activities
Generate endpoint telemetry
Record SSH authentication events
Record Apache web-server activity
Provide logs for security investigation
Forward security events to Wazuh

---

## 3.3 SENTINEL — Wazuh Server

Operating System: Ubuntu

SENTINEL acts as the centralized security monitoring and analysis server.

Components
Wazuh Manager
Wazuh Dashboard
Alert processing
Security-event monitoring
MITRE ATT&CK visibility

SENTINEL receives security telemetry from CITADEL, processes the events through Wazuh, and provides the analyst with a centralized interface for detection and investigation.

---

# 4. Security Monitoring Architecture

## 4. Security Monitoring Architecture

## 4. Security Monitoring Architecture

The monitoring process follows this sequence:

<table>
<tr>
<td align="center" width="25%">

### OCTOPUS

**Kali Linux**

Attacker

</td>

<td align="center" width="10%">

→

</td>

<td align="center" width="25%">

### CITADEL

**Ubuntu**

Wazuh Agent  
Apache HTTP Server  
SSH

</td>

<td align="center" width="10%">

→

</td>

<td align="center" width="25%">

### SENTINEL

**Ubuntu**

Wazuh Manager  
Wazuh Dashboard

</td>
</tr>
</table>

### Monitoring Flow

**OCTOPUS**  
Attack & Reconnaissance Activity  
↓  
**CITADEL**  
Endpoint Logs & Security Telemetry  
↓  
**Wazuh Agent**  
Event Collection & Forwarding  
↓  
**SENTINEL**  
Wazuh Manager & Alert Processing  
↓  
**Wazuh Dashboard**

### Security Visibility

| Security Alerts | Security Events | MITRE ATT&CK |
|:---:|:---:|:---:|
| Detection & Alerting | Event Monitoring & Investigation | Technique Mapping |

## 5. Project Objectives

The main objectives of this lab are:

- Deploy a centralized Wazuh SIEM environment.
- Integrate an Ubuntu endpoint with Wazuh.
- Monitor SSH authentication activity.
- Monitor Apache web-server activity.
- Perform network and web reconnaissance.
- Simulate controlled security attacks.
- Detect suspicious activity through Wazuh.
- Investigate security alerts.
- Map detected activity to MITRE ATT&CK.
- Document the complete SOC investigation workflow.
