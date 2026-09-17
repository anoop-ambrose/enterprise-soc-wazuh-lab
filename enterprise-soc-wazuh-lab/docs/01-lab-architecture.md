# 01 — SOC Lab Architecture

## 1. Overview

This project implements an enterprise-style Security Operations Center (SOC) lab using VirtualBox and Wazuh.

The lab simulates a controlled security environment consisting of an attacker machine, a monitored Ubuntu endpoint, and a centralized Wazuh security monitoring server.

The environment demonstrates the complete security monitoring lifecycle:

**Attack → Telemetry → Detection → Investigation → MITRE ATT&CK**

The lab is designed to demonstrate how offensive security activity can generate endpoint and application telemetry that is collected, processed, detected, and investigated through a centralized SIEM platform.

---

## 2. Lab Architecture

The SOC lab consists of three virtual machines and one host machine used to access the monitoring interface.

### Virtual Machines

| Machine | Operating System | Role |
|---|---|---|
| **OCTOPUS** | Kali Linux | Attacker / Security Testing |
| **CITADEL** | Ubuntu | Monitored Endpoint |
| **SENTINEL** | Ubuntu | Wazuh Server / SIEM |

### Host Machine

The Windows host machine is used to run the VirtualBox environment and access the Wazuh Dashboard through a web browser.

**The Windows host is not configured as a Wazuh Agent.**

---

### Architecture Diagram

![Security Monitoring Architecture](../assets/architecture/security-monitoring-architecture.png)

**Architecture Flow:**

**OCTOPUS → CITADEL → Wazuh Agent → SENTINEL → Wazuh Dashboard**

The Windows host accesses the Wazuh Dashboard through a web browser but does not participate as a monitored Wazuh endpoint.

---

## 3. Machine Roles

### 3.1 OCTOPUS — Attacker

**Operating System:** Kali Linux

OCTOPUS is the attacker and security-testing machine used to generate controlled reconnaissance and attack activity against the authorized lab environment.

The machine is used to simulate activities that generate observable security events on the monitored endpoint.

### Tools Used

- Nmap
- Nikto
- Gobuster
- Hydra
- cURL

### Primary Activities

- Network reconnaissance
- Service enumeration
- Web reconnaissance
- Directory enumeration
- SSH authentication testing
- HTTP request generation

OCTOPUS represents the offensive side of the lab and provides the activity that the defensive monitoring environment must detect and investigate.

---

### 3.2 CITADEL — Monitored Endpoint

**Operating System:** Ubuntu

CITADEL is the monitored endpoint in the SOC environment.

The system runs the Wazuh Agent and provides endpoint and application telemetry to the centralized Wazuh Manager.

### Components

- Wazuh Agent
- Apache HTTP Server
- SSH

### Primary Activities

- Generate endpoint security telemetry
- Record SSH authentication events
- Record Apache web-server activity
- Generate system security logs
- Provide logs for investigation
- Forward security events to SENTINEL

CITADEL acts as the primary monitored endpoint where attack activity is observed and recorded.

---

### 3.3 SENTINEL — Wazuh Server

**Operating System:** Ubuntu

SENTINEL is the centralized security monitoring server for the lab.

It receives security telemetry from CITADEL through the Wazuh Agent and processes the events using Wazuh.

### Components

- Wazuh Manager
- Wazuh Dashboard
- Alert processing
- Security-event monitoring
- MITRE ATT&CK visibility

### Primary Functions

- Receive endpoint telemetry
- Process security events
- Generate security alerts
- Provide centralized event visibility
- Support alert investigation
- Provide MITRE ATT&CK contextualization

SENTINEL acts as the central point for security monitoring and investigation.

---

### 3.4 Windows Host — Dashboard Access

**Operating System:** Windows

The Windows machine is the physical host system running the VirtualBox environment.

It is used primarily for:

- Running the VirtualBox environment
- Accessing the Wazuh Dashboard through a web browser
- Viewing security alerts and events
- Performing SOC analysis through the dashboard

### Important

The Windows host is **not a Wazuh Agent** in this lab.

The monitored endpoint is:

**CITADEL — Ubuntu**

The Windows host only provides browser-based access to the Wazuh Dashboard hosted on SENTINEL.

---

## 4. Security Monitoring Architecture

The security monitoring process follows the flow from attack activity to centralized detection and investigation.

![Security Monitoring Architecture](../assets/architecture/security-monitoring-architecture.png)

### Monitoring Flow

**1. OCTOPUS — Attack Activity**

OCTOPUS performs controlled reconnaissance and security-testing activities against CITADEL.

↓

**2. CITADEL — Endpoint Telemetry**

CITADEL receives the activity and generates relevant authentication, web-server, and system logs.

↓

**3. Wazuh Agent — Event Collection**

The Wazuh Agent running on CITADEL collects relevant endpoint security telemetry.

↓

**4. SENTINEL — Event Processing**

The Wazuh Manager receives and processes the events from CITADEL.

↓

**5. Wazuh Dashboard — Security Monitoring**

The Wazuh Dashboard provides centralized visibility into:

- Security alerts
- Security events
- Event details
- Detection rules
- MITRE ATT&CK mappings

↓

**6. Analyst Investigation**

The analyst reviews the available telemetry and alerts to understand the activity, identify the affected endpoint and source, and document the findings.

---

## 5. Security Monitoring Components

| Component | Machine | Purpose |
|---|---|---|
| Kali Linux | OCTOPUS | Attack and reconnaissance |
| Ubuntu | CITADEL | Monitored endpoint |
| Wazuh Agent | CITADEL | Endpoint telemetry collection |
| Apache HTTP Server | CITADEL | Web-server monitoring |
| SSH | CITADEL | Authentication monitoring |
| Wazuh Manager | SENTINEL | Event processing and detection |
| Wazuh Dashboard | SENTINEL | Security monitoring and investigation |
| Windows Host | Host Machine | Browser access to Wazuh Dashboard |
| MITRE ATT&CK | SENTINEL / Dashboard | Attack-technique contextualization |

---

## 6. Project Objectives

The main objectives of this lab are:

- Deploy a centralized Wazuh SIEM environment.
- Configure an Ubuntu endpoint for centralized monitoring.
- Integrate the CITADEL endpoint with Wazuh.
- Monitor SSH authentication activity.
- Monitor Apache web-server activity.
- Perform network reconnaissance.
- Perform service enumeration.
- Perform web reconnaissance.
- Perform directory enumeration.
- Simulate controlled security attacks.
- Detect suspicious activity through Wazuh.
- Investigate security alerts.
- Analyze endpoint and application logs.
- Map detected activity to MITRE ATT&CK.
- Document the complete SOC investigation workflow.

---

## 7. Security Monitoring Workflow

The lab is organized around the following security monitoring workflow:

```text
Reconnaissance
      ↓
Service Enumeration
      ↓
SSH Brute-Force Simulation
      ↓
Apache / Web Monitoring
      ↓
Web Enumeration
      ↓
Wazuh Detection
      ↓
Alert Investigation
      ↓
MITRE ATT&CK Mapping
      ↓
Security Findings
