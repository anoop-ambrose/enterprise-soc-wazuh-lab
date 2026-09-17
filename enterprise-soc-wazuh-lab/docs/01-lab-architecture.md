# 01 — SOC Lab Architecture

## 1. Architecture Overview

This project implements an enterprise-style Security Operations Center (SOC) lab using VirtualBox and Wazuh.

The lab consists of three primary virtual machines:

- **OCTOPUS** — Kali Linux attacker machine
- **CITADEL** — Ubuntu monitored endpoint
- **SENTINEL** — Ubuntu Wazuh SIEM server

The architecture demonstrates the complete flow from attack activity and endpoint telemetry to centralized detection, investigation, and MITRE ATT&CK mapping.

---

## 2. Lab Architecture

```text
                         ┌───────────────────────┐
                         │       OCTOPUS         │
                         │      Kali Linux       │
                         │       Attacker        │
                         └───────────┬───────────┘
                                     │
                       Reconnaissance & Attack
                                     │
                                     ▼
                         ┌───────────────────────┐
                         │       CITADEL         │
                         │        Ubuntu         │
                         │                       │
                         │    Wazuh Agent        │
                         │    Apache HTTP Server  │
                         │    SSH Service         │
                         └───────────┬───────────┘
                                     │
                              Security Events
                                     │
                                     ▼
                         ┌───────────────────────┐
                         │       SENTINEL        │
                         │        Ubuntu         │
                         │                       │
                         │     Wazuh Manager     │
                         │     Wazuh Dashboard   │
                         └───────────┬───────────┘
                                     │
                                     ▼
                         ┌───────────────────────┐
                         │    SOC Monitoring     │
                         │                       │
                         │  Alerts | Events      │
                         │  MITRE ATT&CK         │
                         └───────────────────────┘

---
