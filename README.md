# 🛡️ SOC Projects

## Enterprise SOC Lab with Wazuh

A hands-on Security Operations Center (SOC) lab built to simulate **security monitoring, threat detection, alert investigation, and incident analysis** in a realistic home-lab environment.

The project combines **Wazuh SIEM, Linux endpoints, attack simulation, security telemetry, detection analysis, and MITRE ATT&CK mapping** to demonstrate a practical SOC analyst workflow.

---

## 🎯 Project Overview

This project was built to understand and demonstrate how a SOC analyst can:

* Monitor security events from endpoints
* Identify suspicious activity
* Analyze security alerts
* Investigate authentication and system events
* Correlate attack activity with generated telemetry
* Map detected activity to MITRE ATT&CK
* Document investigation findings
* Validate detections through controlled attack simulations

The goal was to build a working SOC environment rather than simply install a SIEM platform.

---

## 🏗️ Lab Architecture

| Role               | System       | Purpose                                        |
| ------------------ | ------------ | ---------------------------------------------- |
| SIEM Server        | Ubuntu Linux | Wazuh server, indexer and dashboard            |
| Attacker           | Kali Linux   | Controlled attack and reconnaissance activity  |
| Monitored Endpoint | Ubuntu Linux | Generates endpoint and security telemetry      |
| Web Server         | Apache       | Generates web access and authentication events |
| Virtualization     | VirtualBox   | Isolated home-lab environment                  |

---

## 🔍 Security Scenarios

The lab includes controlled security scenarios covering:

* SSH authentication attacks
* Password-guessing activity
* Web authentication failures
* Directory enumeration
* Network reconnaissance
* Suspicious command execution
* Account-related security events
* Endpoint activity investigation

These scenarios were used to generate real security telemetry and validate the monitoring and detection workflow.

---

## 🧠 SOC Investigation Workflow

The project follows a structured workflow:

```text
Attack Simulation
        ↓
Security Event Generation
        ↓
Wazuh Detection
        ↓
Alert Triage
        ↓
Event Investigation
        ↓
MITRE ATT&CK Mapping
        ↓
Evidence Collection
        ↓
Findings & Documentation
```

This workflow demonstrates the transition from **security event to detection, investigation, and documented findings**.

---

## 🛠️ Technologies Used

* Wazuh
* Ubuntu Linux
* Kali Linux
* Apache
* SSH
* VirtualBox
* MITRE ATT&CK
* Linux security tools
* Network reconnaissance tools

---

## 📊 SOC Skills Demonstrated

| Skill Area          | Practical Application                       |
| ------------------- | ------------------------------------------- |
| SIEM                | Wazuh deployment and monitoring             |
| Security Monitoring | Endpoint and service activity monitoring    |
| Log Analysis        | Authentication, process and web events      |
| Alert Triage        | Reviewing and analyzing security alerts     |
| Threat Detection    | Detecting simulated attack activity         |
| Network Security    | Reconnaissance and network activity         |
| Linux Security      | Monitoring Linux endpoint activity          |
| Web Security        | Apache and web authentication monitoring    |
| Investigation       | Analyzing events and attack activity        |
| MITRE ATT&CK        | Mapping observed techniques                 |
| Documentation       | Investigation notes and technical reporting |

---

## 📸 Project Evidence

The project documentation includes practical evidence such as:

* SOC architecture
* Wazuh dashboard
* Agent monitoring
* Security alerts
* Authentication events
* Process activity
* Web security events
* Network reconnaissance
* Detection results
* Investigation evidence
* MITRE ATT&CK mappings
* Attack simulation results
* Technical documentation

The evidence is organized within the project documentation to show how each detection scenario was generated, detected, and investigated.

---

## 📂 Project Documentation

The complete project documentation covers:

1. **SOC Lab Architecture**
2. **Wazuh Deployment**
3. **Agent Integration**
4. **SSH Brute-Force Detection**
5. **Web Login Failure Detection**
6. **Directory Enumeration Detection**
7. **Security Event Investigation**
8. **Lessons Learned**

➡️ **[View the complete Enterprise SOC Lab](./)**

---

## 🔎 What I Learned

Building this lab provided practical experience with:

* Deploying and configuring a SIEM environment
* Integrating monitored endpoints
* Understanding security telemetry
* Investigating authentication events
* Analyzing suspicious activity
* Validating detections through attack simulation
* Using MITRE ATT&CK to classify observed behavior
* Documenting security investigations
* Thinking through events from a SOC analyst perspective

---

## 👨‍💻 About Me

I'm **Anoop Ambrose**, a cybersecurity professional developing hands-on experience in **SOC operations, SIEM, threat detection, security monitoring, incident investigation, and penetration testing**.

I'm currently focused on building practical SOC capabilities through security labs, attack simulations, detection analysis, and structured investigations.

### Current Focus

`SOC Operations`
`SIEM`
`Security Monitoring`
`Threat Detection`
`Log Analysis`
`Incident Investigation`
`Network Security`
`Linux Security`
`Web Security`
`MITRE ATT&CK`

---

## 📫 Connect With Me

* 🌐 **Portfolio:** [anoopambrose.com](https://anoopambrose.com)
* 💼 **LinkedIn:** [linkedin.com/in/anoop-ambrose](https://linkedin.com/in/anoop-ambrose)
* 🐙 **GitHub:** [github.com/anoop-ambrose](https://github.com/anoop-ambrose)

---

## ⭐ Project Objective

> **Build it. Break it. Detect it. Investigate it. Document it.**

This project represents my practical approach to learning Security Operations — combining **attack simulation with defensive monitoring and investigation** to understand the complete security event lifecycle.
