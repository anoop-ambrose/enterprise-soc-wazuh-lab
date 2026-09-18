# Nmap Commands Reference

Nmap is used in this lab for network reconnaissance, host discovery, and
service enumeration during controlled security testing.

## 1. Basic Host Scan

$ nmap <TARGET>

## 2. Service Enumeration

$ nmap -sV TARGET

## 3. Default Script Scan

$ nmap -sC TARGET

## 4. Service and Script Enumeration

$ nmap -sC -sV TARGET

### 5. Lab Example
Nmap was used from OCTOPUS to perform reconnaissance against CITADEL:

$ nmap -sC -sV TARGET
