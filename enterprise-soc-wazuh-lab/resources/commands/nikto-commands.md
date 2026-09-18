# Nikto Commands Reference

Nikto is a web server scanner used in this lab to identify common web server
misconfigurations, exposed resources, and security-related findings.

## Basic Web Server Scan

$ nikto -h http://TARGET

### Specify a Port

$ nikto -h http://TARGET:8080

### Save Scan Results

$ nikto -h http://TARGET -o nikto-results.txt

### Lab Example
Nikto was used against the Apache web server running on CITADEL:

$ nikto -h http://TARGET
