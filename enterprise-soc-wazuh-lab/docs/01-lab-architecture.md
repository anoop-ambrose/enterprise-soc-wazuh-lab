# 01 — SOC Lab Architecture

## 1. Architecture Overview

This project implements an enterprise-style Security Operations Center (SOC) lab using VirtualBox and Wazuh.

The lab consists of three primary virtual machines:

- **OCTOPUS** — Kali Linux attacker machine
- **CITADEL** — Ubuntu monitored endpoint
- **SENTINEL** — Ubuntu Wazuh SIEM server

The architecture demonstrates the complete flow from attack activity and endpoint telemetry to centralized detection, investigation, and MITRE ATT&CK mapping.

---
