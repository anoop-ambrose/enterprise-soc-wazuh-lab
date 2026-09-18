# Apache Log Commands Reference

This document contains commonly used Apache commands for service management, log monitoring, troubleshooting, and security event investigation.

## 1. Apache Service Management

### Check Apache Status

$ sudo systemctl status apache2

### Start Apache

$ sudo systemctl start apache2

### Stop Apache

$ sudo systemctl stop apache2

### Restart Apache 

$ sudo systemctl restart apache2

### Reload Apache Configuration

$ sudo systemctl reload apache2

### Enable Apache at Boot

$ sudo systemctl enable apache2

### Disable Apache at Boot

$ sudo systemctl disable apache2

## 2. Apache Access Logs

### View Recent Access Logs

$ sudo tail /var/log/apache2/access.log

### Follow Access Logs in Real Time

$ sudo tail -f /var/log/apache2/access.log

### View the Last 50 Requests

$ sudo tail -n 50 /var/log/apache2/access.log

### Search Access Logs

$ sudo grep "GET" /var/log/apache2/access.log

### Search for a Specific IP

$ sudo grep "192.168.0.102" /var/log/apache2/access.log

### Search for HTTP 404 Responses

$ sudo grep '" 404 ' /var/log/apache2/access.log

### Search for HTTP 403 Responses

$ sudo grep '" 403 ' /var/log/apache2/access.log

### Search for HTTP 400 Responses
 
$ sudo grep '" 400 ' /var/log/apache2/access.log

## 3. Apache Error Logs
### View Recent Error Logs

$ sudo tail /var/log/apache2/error.log

### Follow Error Logs in Real Time

$ sudo tail -f /var/log/apache2/error.log

### View the Last 50 Errors

$ sudo tail -n 50 /var/log/apache2/error.log

## 4. Log Analysis
### Find Requests to a Specific Path

$ sudo grep "/admin" /var/log/apache2/access.log

### Find Requests Containing a Keyword

$ sudo grep -i "login" /var/log/apache2/access.log

### Find Requests from a User-Agent

$ sudo grep -i "gobuster" /var/log/apache2/access.log

### Count Requests from an IP

$ sudo grep "192.168.0.102" /var/log/apache2/access.log | wc -l

### Count 404 Responses

 $ sudo grep '" 404 ' /var/log/apache2/access.log | wc -l

 ### Count 403 Responses

 $ sudo grep '" 403 ' /var/log/apache2/access.log | wc -l

 ## 5. Monitoring Enumeration Activity
 ### Monitor Access Logs During Testing

 $ sudo tail -f /var/log/apache2/access.log
