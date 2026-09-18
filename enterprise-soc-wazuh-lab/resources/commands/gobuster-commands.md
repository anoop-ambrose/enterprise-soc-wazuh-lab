# Gobuster Commands Reference

This document contains commonly used Gobuster commands for controlled web
content discovery and directory enumeration during authorized security testing.

## 1. Basic Directory Enumeration

$ gobuster dir -u http://TARGET -w /usr/share/wordlists/dirb/common.txt

### Specify Extensions

$ gobuster dir -u http://TARGET -w /usr/share/wordlists/dirb/common.txt -x php,html,txt

### Use a Specific Wordlist

$ gobuster dir -u http://TARGET -w /path/to/wordlist.txt

## 2. Useful Enumeration Options
### Set Request Threads

$ gobuster dir -u http://TARGET -w /path/to/wordlist.txt -t 50

### Set Request Timeout

$ gobuster dir -u http://TARGET -w /path/to/wordlist.txt --timeout 10s

### Follow Redirects

$ gobuster dir -u http://TARGET -w /path/to/wordlist.txt -r

### Show Full Request URLs

$ gobuster dir -u http://TARGET -w /path/to/wordlist.txt -v

## 3. HTTP Status Code Filtering
### how Specific Status Codes

$ gobuster dir -u http://TARGET -w /path/to/wordlist.txt -s 200,204,301,302,307,401,403

### Exclude Specific Status Codes

$ gobuster dir -u http://TARGET -w /path/to/wordlist.txt -b 404

## 4. Authentication
### Basic HTTP Authentication

$ gobuster dir -u http://TARGET -w /path/to/wordlist.txt -U USERNAME -P PASSWORD
Only use credentials when authorized to test the target.

## 5.HTTPS Targets

$ gobuster dir -u https://TARGET -w /path/to/wordlist.txt

## 6. Directory Enumeration Used in the SOC Lab

$ gobuster dir -u http://TARGET -w /usr/share/wordlists/dirb/common.txt
