# Wazuh Server Commands Reference

This document contains commonly used commands for managing and troubleshooting the Wazuh server components used in the Enterprise SOC Lab.

## 1. Wazuh Manager

### Check Status

$ sudo systemctl status wazuh-manager

### Start

$ sudo systemctl start wazuh-manager

### Stop

$ sudo systemctl stop wazuh-manager

### Restart

$ sudo systemctl restart wazuh-manager

### Enable at Boot

$ sudo systemctl enable wazuh-manager

### Check Manager Logs

$ sudo tail -f /var/ossec/logs/ossec.log

## 2. Wazuh Indexer

### Check Status

$ sudo systemctl status wazuh-indexer

### Start

$ sudo systemcctl start wazuh-indexer

### Stop 

$ sudo systemctl stop wazuh-indexer

### Restart

$ sudo systemctl restart wazuh-indexer

### Enable at Boot

$ sudo systemctl enable wazuh-indexer

## 3. Wazuh Dashboard

### Check Status

$ sudo systemctl status wazuh-dashboard

### Start 

$ sudo systemctl start wazuh-dashboard

### Stop 

$ sudo systemctl stop wazuh-dashboard

### Restart 

$ sudo systemctl restart wazuh-dashboard

### Enable at Boot

$ sudo systemctl enable wazuh-dashboard

## 4. Troubleshooting

### Check Failed Services

$ systemctl --failed

### View Manager Service Logs

$ sudo journalctl -u wazuh-manager

### View Indexer Service Logs

$ sudo journalctl -u wazuh-indexer

### View Dashboard Service Logs

$ sudo journalctl -u wazuh-dashboard

### Follow Recent Manager Logs

$ sudo journalctl -u wazuh-manager -f

### Follow Recent Indexer Logs

$ sudo journalctl -u wazuh-indexer -f

### Follow Recent Dashboard Logs

$ sudo journalctl -u wazuh-dashboard -f

## 5. Useful Wazuh Manager Commands

### List Agents

$ sudo /var/ossec/bin/agent_control -l

### Show Connected Agents

$ sudo /var/ossec/bin/agent_control -lc

### Check Manager Configuration

$ sudo /var/ossec/bin/wazuh-control info

##
