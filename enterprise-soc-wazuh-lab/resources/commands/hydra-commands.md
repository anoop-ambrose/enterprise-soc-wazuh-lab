# Hydra Commands Reference

Hydra is a network authentication auditing tool used in this lab to generate
controlled SSH authentication attempts for security monitoring and detection.

## SSH Password Testing

### Basic SSH Authentication Testing

$ hydra -l USERNAME -P /path/to/wordlist.txt ssh://TARGET

### Verbose Mode

$ hydra -l USERNAME -P /path/to/wordlist.txt ssh://TARGET -V

### Specify the SSH Port

$ hydra -l USERNAME -P /path/to/wordlist.txt -s 22 ssh://TARGET

### Lab Example
The lab used Hydra against the SSH service running on CITADEL:

$ hydra -l citadel -P /usr/share/wordlists/rockyou.txt ssh://TARGET -V
