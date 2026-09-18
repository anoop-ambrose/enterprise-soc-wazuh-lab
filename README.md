# 🛡️ SOC Projects

### Hands-On Security Monitoring, Detection & Investigation

This repository contains my hands-on SOC security work, starting with an **Enterprise SOC Lab with Wazuh** built in a virtualized home-lab environment.

The project focuses on generating security activity, collecting endpoint and service telemetry, detecting suspicious behavior with Wazuh, investigating the resulting events, and documenting the findings.

> **Attack → Telemetry → Detection → Investigation → Evidence → Documentation**

---

# 🔎 Featured Project

## Enterprise SOC Lab with Wazuh

A hands-on SOC environment built to practice the workflow of monitoring security events, analyzing alerts, investigating suspicious activity, and documenting findings.

### What I Built

The lab consists of three virtual machines with distinct roles:

| System              | Role               | Purpose                                         |
| ------------------- | ------------------ | ----------------------------------------------- |
| **SENTINEL**        | Wazuh Server       | SIEM, security monitoring and alert analysis    |
| **CITADEL**         | Monitored Endpoint | Generates Linux endpoint and service telemetry  |
| **OCTOPUS**         | Attacker           | Controlled reconnaissance and attack simulation |
| **Windows 11 Host** | Management Host    | Used to access and manage the lab environment   |

The environment was built using **VirtualBox** with Ubuntu and Kali Linux systems.

---

# 🚨 Detection Scenarios

The lab uses controlled activity from the attacker machine to generate security events that can be observed and investigated through Wazuh.

### 01 — SSH Authentication Attacks

**Activity**

Repeated SSH authentication attempts were generated against the monitored Ubuntu endpoint.

**Detection**

Wazuh collected the resulting authentication events and surfaced the failed login activity for analysis.

**Investigation**

The investigation focused on the authentication events, source activity, affected account, timestamps, and repeated failure pattern.

**MITRE ATT&CK**

`T1110 — Brute Force`

---

### 02 — Web Authentication Failures

**Activity**

Repeated failed authentication activity was generated against the Apache-hosted web service.

**Detection**

The resulting web authentication events were collected and analyzed through Wazuh.

**Investigation**

The investigation examined the generated web events and authentication failure activity to understand the observed behavior.

---

### 03 — Directory Enumeration

**Activity**

Directory enumeration activity was performed against the web server from the Kali attacker machine.

**Detection**

The resulting web access activity was collected as security telemetry.

**Investigation**

The investigation examined requested paths and the resulting web activity to identify reconnaissance behavior.

---

### 04 — Network Reconnaissance

**Activity**

Network reconnaissance was performed from the Kali attacker machine using Nmap.

**Detection & Analysis**

The reconnaissance activity was correlated with the available lab telemetry and investigated as part of the reconnaissance phase.

**Investigation Focus**

* Source system
* Target system
* Discovered services
* Open ports
* Reconnaissance activity

---

### 05 — Suspicious Command / Process Activity

The lab also includes endpoint activity involving command execution.

Wazuh endpoint telemetry was used to observe process-related security events and investigate the activity generated on the monitored system.

---

# 🧠 How I Investigated the Activity

Each scenario was approached using a repeatable analyst workflow rather than simply running an attack and recording the result.

```text
┌─────────────────────────┐
│   Generate Activity     │
│   Kali / Lab Scenario   │
└────────────┬────────────┘
             ↓
┌─────────────────────────┐
│   Generate Telemetry    │
│   Logs / Endpoint Data  │
└────────────┬────────────┘
             ↓
┌─────────────────────────┐
│   Wazuh Detection       │
│   Alert / Event         │
└────────────┬────────────┘
             ↓
┌─────────────────────────┐
│      Alert Triage       │
│  What happened?         │
└────────────┬────────────┘
             ↓
┌─────────────────────────┐
│     Investigation       │
│  Who / What / When /    │
│  Where / How            │
└────────────┬────────────┘
             ↓
┌─────────────────────────┐
│  MITRE ATT&CK Mapping   │
└────────────┬────────────┘
             ↓
┌─────────────────────────┐
│ Evidence & Documentation│
└─────────────────────────┘
```

For each investigation, I aim to answer:

* **What happened?**
* **What generated the event?**
* **Which system was affected?**
* **When did the activity occur?**
* **What evidence supports the finding?**
* **What technique or behavior does it represent?**

---

# 🛠️ Technologies Used

### SIEM & Security Monitoring

* **Wazuh**

### Operating Systems

* Ubuntu Linux
* Kali Linux
* Windows 11

### Network & Security Tools

* Nmap
* Wireshark
* Kali Linux security tooling

### Services

* Apache
* SSH

### Virtualization

* VirtualBox

### Security Framework

* MITRE ATT&CK

---

# 📊 Security Evidence

The project is supported by actual lab evidence collected during the scenarios.

Evidence includes:

* Wazuh agent status and monitoring
* Wazuh security alerts
* Authentication events
* Endpoint process activity
* Web server activity
* Network reconnaissance activity
* Detection results
* Investigation screenshots
* MITRE ATT&CK mappings
* Command-line evidence
* Lab architecture documentation

### Example Evidence Flow

```text
Attack Activity
      ↓
Security Event
      ↓
Wazuh Alert
      ↓
Event Details
      ↓
Investigation
      ↓
MITRE ATT&CK
      ↓
Documented Finding
```

The detailed evidence and investigation screenshots are available inside the project documentation.

---

# 📁 Project Documentation

The Wazuh project is organized into investigation and documentation sections covering:

| Section               | Focus                           |
| --------------------- | ------------------------------- |
| Architecture          | SOC lab design and components   |
| Agent Integration     | Wazuh endpoint integration      |
| SSH Brute Force       | Authentication attack detection |
| Web Login Failures    | Web authentication monitoring   |
| Directory Enumeration | Web reconnaissance activity     |
| Investigation         | Analysis of detected events     |
| Lessons Learned       | Observations and improvements   |

➡️ **[Explore the complete Enterprise SOC Lab with Wazuh](./)**

---

# 📌 Key Takeaways

Through this project, I practiced:

* Building a multi-system SOC lab
* Deploying and working with Wazuh
* Integrating a monitored Linux endpoint
* Generating controlled security activity
* Collecting and analyzing security telemetry
* Investigating authentication events
* Investigating web activity
* Analyzing endpoint process activity
* Performing network reconnaissance
* Mapping observed activity to MITRE ATT&CK
* Documenting technical findings with supporting evidence

---

# 👨‍💻 About

I'm **Anoop Ambrose**, a cybersecurity professional developing hands-on experience in **SOC operations, SIEM, security monitoring, threat detection, log analysis, incident investigation, and penetration testing**.

My current focus is building practical defensive-security skills through lab environments where I can **generate security activity, analyze telemetry, investigate alerts, and document findings**.

### Current Focus

`SOC Operations` · `SIEM` · `Security Monitoring` · `Threat Detection`

`Log Analysis` · `Incident Investigation` · `Linux Security` · `Network Security`

---

# 📫 Connect

* 🌐 **Portfolio:** [anoopambrose.com](https://anoopambrose.com)
* 💼 **LinkedIn:** [linkedin.com/in/anoop-ambrose](https://linkedin.com/in/anoop-ambrose)
* 🐙 **GitHub:** [github.com/anoop-ambrose](https://github.com/anoop-ambrose)

---

## ⭐ Project Philosophy

> **Build it. Generate the activity. Detect it. Investigate it. Document the evidence.**

This repository will grow as I complete additional hands-on SOC projects and investigations.
