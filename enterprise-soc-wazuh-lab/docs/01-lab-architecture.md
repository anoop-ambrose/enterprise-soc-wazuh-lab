# 01 — SOC Lab Architecture

## Overview

This project implements an enterprise-style Security Operations Center (SOC) lab using VirtualBox and Wazuh.

The lab simulates an attacker, a monitored endpoint, centralized security monitoring, attack detection, investigation, and MITRE ATT&CK mapping.

## Lab Architecture

| Machine | Operating System | Role |
|---|---|---|
| OCTOPUS | Kali Linux | Attacker / Security Testing |
| CITADEL | Ubuntu | Monitored Endpoint / Wazuh Agent / Apache Server |
| SENTINEL | Ubuntu | Wazuh Manager / SIEM Server / Dashboard |

## Architecture Flow

```text



                    OCTOPUS
                  Kali Linux
                   Attacker
                      |
              Reconnaissance
             & Attack Activity
                      |
                      v
                   CITADEL
                    Ubuntu
          Wazuh Agent + Apache
                      |
              Security Events
                      |
                      v
                  SENTINEL
                    Ubuntu
             Wazuh Manager
                      |
                      v
              Wazuh Dashboard
                      |
          +-----------+-----------+
          |           |           |
       Alerts      Events      MITRE
                                ATT&CK


## Roles of Each Machine
### OCTOPUS — Attacker

OCTOPUS is the Kali Linux attack machine used to simulate security testing activity against the authorized lab environment.

Tools used include:

Nmap
Nikto
Gobuster
Hydra
Curl
## CITADEL — Monitored Endpoint

CITADEL is the Ubuntu endpoint monitored by Wazuh.

Services and components include:

Wazuh Agent
Apache HTTP Server
SSH

The endpoint generates authentication, web-server, and system security logs that are collected for centralized monitoring.

### SENTINEL — Wazuh Server

SENTINEL is the centralized security monitoring server.

It hosts:

Wazuh Manager
Wazuh Dashboard
Alert processing
Security-event monitoring
MITRE ATT&CK visibility
Project Objectives

## The main objectives of this lab are:

Deploy a centralized Wazuh SIEM environment.
Integrate an Ubuntu endpoint with Wazuh.
Monitor SSH authentication activity.
Monitor Apache web-server activity.
Perform network and web reconnaissance.
Simulate controlled security attacks.
Detect suspicious activity through Wazuh.
Investigate security alerts.
Map detected activity to MITRE ATT&CK.
Document the complete SOC investigation workflow.



## Security Monitoring Workflow

Reconnaissance
      ↓
Service Enumeration
      ↓
SSH Brute-Force Simulation
      ↓
Apache/Web Monitoring
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



## Lab Outcome

The completed environment provides an end-to-end SOC workflow demonstrating how security activity can be generated on an endpoint, collected by a Wazuh agent, analyzed by the Wazuh manager, investigated through the dashboard, and mapped to the MITRE ATT&CK framework.
