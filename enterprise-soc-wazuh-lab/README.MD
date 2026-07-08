
# Enterprise SOC Lab with Wazuh
### Building, Monitoring, and Investigating Security Events in a Realistic Home Lab

![Status](https://img.shields.io/badge/Status-Completed-success)
![Platform](https://img.shields.io/badge/Platform-Wazuh-blue)
![Environment](https://img.shields.io/badge/Environment-Ubuntu%20%7C%20Windows%2011%20%7C%20Kali-red)
![License](https://img.shields.io/badge/License-MIT-green)

---

# Project Overview

This project demonstrates the design, deployment, and operation of an enterprise-style Security Operations Center (SOC) using **Wazuh SIEM** within a virtualized lab environment.

Instead of simply installing Wazuh, the objective was to understand how security monitoring works in practice by generating real attack activity from an attacker machine, collecting telemetry from monitored endpoints, and investigating alerts through the Wazuh Dashboard.

The project follows the complete SOC workflow:

- Build the monitoring infrastructure
- Connect monitored endpoints
- Generate attacker activity
- Detect malicious behavior
- Investigate security events
- Validate detections
- Document findings

This repository contains the project overview, while each implementation phase is documented separately with commands, screenshots, explanations, and results.

---

# Objectives

The primary objectives of this project were to:

- Deploy an enterprise-grade Wazuh SIEM server
- Configure Windows and Linux endpoints
- Generate realistic attack scenarios
- Validate security detections
- Understand the SOC investigation workflow
- Learn log collection and correlation
- Build practical blue-team experience
- Create professional documentation suitable for a cybersecurity portfolio

---

# Lab Architecture

```
                                                   ENTERPRISE SOC LAB ARCHITECTURE

┌────────────────────────────────────────────────────────────────────────────────────────────┐
│                               Windows 11 Host Machine                                      │
│                                                                                            │
│  ┌──────────────────────────────┐                                                          │
│  │        Web Browser           │                                                          │
│  │  Accesses Wazuh Dashboard    │                                                          │
│  │  https://<SENTINEL-IP>       │                                                          │
│  └───────────────┬──────────────┘                                                          │
│                  │                                                                         │
└──────────────────┼─────────────────────────────────────────────────────────────────────────┘
                   │
                   ▼
┌────────────────────────────────────────────────────────────────────────────────────────────┐
│                              Oracle VirtualBox Environment                                 │
│                                                                                            │
│  ┌──────────────────────┐       Attack Traffic        ┌──────────────────────────────┐     │
│  │  Kali Linux          │────────────────────────────►│ Ubuntu Wazuh Server          │     │
│  │      OCTOPUS         │                             │         SENTINEL             │     │
│  │                      │                             │                              │     │
│  │ Role: Attacker       │                             │ • Wazuh Manager              │     │
│  │                      │                             │ • Wazuh Indexer              │     │
│  │ • Nmap               │                             │ • Wazuh Dashboard            │     │
│  │ • Hydra              │                             │ • API                        │     │
│  │ • Gobuster           │                             │                              │     │
│  │ • SSH Attacks        │                             │ Central SIEM Platform        │     │
│  └──────────────────────┘                             └──────────────┬───────────────┘     │
│                                                                     ▲                      │
│                                                                     │                      │
│                                              Wazuh Agent Logs       │                      │
│                                         (TCP 1514 / TCP 1515)       │                      │
│                                                                     │                      │
│                                                       ┌─────────────┴─────────────┐        │
│                                                       │ Ubuntu Desktop            │        │
│                                                       │       CITADEL             │        │
│                                                       │                           │        │
│                                                       │ Role: Victim Machine      │        │
│                                                       │                           │        │
│                                                       │ • Apache Web Server       │        │
│                                                       │ • SSH Service             │        │
│                                                       │ • Wazuh Agent             │        │
│                                                       │ • Log Collection          │        │
│                                                       │ • Security Events         │        │
│                                                       └───────────────────────────┘        │
└────────────────────────────────────────────────────────────────────────────────────────────┘


Attack Flow
───────────

OCTOPUS (Kali Linux)
        │
        │  Reconnaissance
        │  SSH Brute Force
        │  Directory Enumeration
        │  HTTP Requests
        ▼
CITADEL (Ubuntu Victim)
        │
        │  Apache Logs
        │  SSH Authentication Logs
        │  System Security Events
        ▼
Wazuh Agent
        │
        │  Forwards Logs & Events
        ▼
SENTINEL (Ubuntu Wazuh Server)
        │
        │  Wazuh Manager
        │  Event Correlation
        │  Rule Matching
        │  Alert Generation
        ▼
Windows 11 Host Machine
        │
        │  Browser (HTTPS)
        ▼
Wazuh Dashboard
        │
        ▼
SOC Investigation & Alert Analysis
```

---

# Technologies Used

| Category          | Technologies                                                      |
| ----------------- | ----------------------------------------------------------------- |
| SIEM              | Wazuh 4.14                                                        |
| Operating Systems | Ubuntu Server, Ubuntu Desktop, Windows 11, Kali Linux             |
| Monitoring        | Wazuh Manager, Wazuh Dashboard, Wazuh Agent,                      |
| Offensive Tools   | Nmap, Hydra, Gobuster                                             |
| Services          | Apache2, OpenSSH                                                  |
| Virtualization    | Oracle VirtualBox                                                 |
| Logging           | Linux Authentication Logs, Apache Access Logs |


---

# Attack Chain Summary

The following attack scenarios were executed to validate detection capabilities:

| Attack | Detection |
|---------|-----------|
| SSH Brute Force | ✅ Detected |
| Failed SSH Logins | ✅ Detected |
| Web Login Failures | ✅ Detected |
| Directory Enumeration | ✅ Detected |
| Web Server Log Monitoring | ✅ Detected |
| Windows Security Events | ✅ Collected |
| Linux Authentication Events | ✅ Collected |

Each attack was intentionally performed from the Kali Linux attacker machine and validated through the Wazuh Dashboard.

---

# Skills Demonstrated

This project demonstrates practical experience with:

- SIEM Deployment
- Security Monitoring
- Log Analysis
- Event Correlation
- Threat Detection
- Windows Event Monitoring
- Linux Log Monitoring
- SOC Investigation
- Incident Validation
- MITRE ATT&CK Mapping
- Virtual Lab Design
- Attack Simulation
- Documentation
- Security Operations

---

# Project Documentation

Each phase contains detailed implementation steps, screenshots, attack execution, detection analysis, and lessons learned.

| Phase | Description |
|--------|-------------|
| 📄 Phase 1 | Wazuh Deployment & Lab Architecture |
| 📄 Phase 2 | Windows & Ubuntu Agent Integration |
| 📄 Phase 3 | SSH Brute Force Detection |
| 📄 Phase 4 | Web Server Monitoring & Failed Login Detection |
| 📄 Phase 5 | Directory Enumeration Detection |
| 📄 Phase 6 | Incident Investigation |
| 📄 Phase 7 | Lesson Learned |

> Each phase is documented separately to keep the repository organized and easy to navigate.

---

# MITRE ATT&CK Coverage

| Technique | ATT&CK ID |
|-----------|-----------|
| Brute Force | T1110 |
| Valid Accounts | T1078 |
| Active Scanning | T1595 |
| Network Service Discovery | T1046 |
| Exploit Public-Facing Application | T1190 |
| Credential Access Monitoring | T1003 *(Detection Focus)* |

The project emphasizes detection and monitoring rather than offensive exploitation.

---

# Repository Structure

```
Enterprise-SOC-Lab/
│
├── README.md
│
├── docs/
│  ├──01-lab architecture.md
│  ├──02-agent-integration.md
│  ├──03-SSH-brute-force-detection.md
│  ├──04-web-login-faliure-detection.md
│  ├──05-directory-enumeration-dectection.md
│  ├──06-incident-investigation.md
│  ├──07-lesson-learned.md
│
├── screenshots/
│  ├──architecture/
│  ├──phase1/
│  ├──phase2/
│  ├──phase3/
│  ├──phase4/
│  ├──phase5/
│  ├──phase6/
│
├──diagrams/
│
├──resources/
│
└── rules/
```

---

# Key Takeaways

Throughout this project I gained hands-on experience with:

- Deploying a SIEM from scratch
- Monitoring Windows and Linux systems
- Simulating real-world attacks
- Investigating security alerts
- Understanding SOC analyst workflows
- Mapping detections to MITRE ATT&CK
- Building repeatable security lab environments
- Creating professional technical documentation



---

# Author

**Anoop Ambrose**

Cybersecurity | SOC | Penetration Testing | Detection Engineering

This repository is part of my cybersecurity portfolio and documents my hands-on learning through practical security engineering projects.

---

> **Note:** This lab was built solely for educational purposes in an isolated virtual environment. All attack simulations were performed against systems owned and controlled within the lab.
