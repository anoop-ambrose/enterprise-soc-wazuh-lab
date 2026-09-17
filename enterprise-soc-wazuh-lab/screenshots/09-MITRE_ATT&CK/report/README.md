# Wazuh MITRE ATT&CK Report

This report documents the MITRE ATT&CK activity observed during the
Enterprise SOC Lab using Wazuh.

## Overview

The report was generated from the Wazuh MITRE ATT&CK module and covers
security alerts mapped to adversary tactics and techniques during the
lab monitoring period.

The report includes:

- Alerts evolution over time
- Attacks by MITRE technique
- Top tactics by agent
- MITRE techniques by agent
- Alert summary with rule IDs, descriptions, severity levels, and counts

## Key Observations

The generated report contains detections related to:

- SSH authentication failures and brute-force activity
- Web server attack activity
- XSS attempts
- SQL injection attempts
- Shellshock activity
- Authentication failures
- Suspicious URL access
- Apache security events

Notable Wazuh detections include SSH brute-force activity (Rule 5763),
maximum authentication attempts exceeded (Rule 5758), SQL injection
attempts (Rule 31103), and multiple web-attack detections.

## Evidence

This report is supporting evidence for the **MITRE ATT&CK Mapping**
phase of the SOC lab. It complements the Wazuh dashboard screenshots
and individual alert investigations.

**Generated using:** Wazuh MITRE ATT&CK module  
**Monitoring period:** 16–17 September 2026

