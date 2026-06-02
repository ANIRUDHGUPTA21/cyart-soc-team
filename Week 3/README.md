# Week 3 - SOC Simulation and Incident Response

## Project Overview
This project demonstrates a complete Security Operations Center (SOC) workflow using Kali Linux, Metasploit, Wazuh SIEM, Docker, and CrowdSec.

## Tools Used
- Kali Linux
- Metasploit Framework
- Wazuh SIEM
- Docker
- CrowdSec
- Metasploitable2
- SHA256 Hashing

## Workflow Steps

### 1. Lab Setup
Configured Kali Linux and Metasploitable2 inside VirtualBox using Host-Only networking.

### 2. Vulnerability Identification
Identified Samba vulnerability using Nmap and Metasploit.

### 3. Exploitation
Executed Samba usermap script exploit and gained reverse shell access.

### 4. SIEM Deployment
Installed Wazuh SIEM using Docker containers.

### 5. Security Monitoring
Analyzed security alerts and event logs using Wazuh dashboard.

### 6. Threat Intelligence
Integrated MITRE ATT&CK framework for threat mapping.

### 7. Incident Containment
Used CrowdSec to block malicious IP addresses.

### 8. Evidence Preservation
Generated SHA256 hashes for forensic integrity verification.

## Project Outcome
Successfully demonstrated attack simulation, SIEM monitoring, incident response, and forensic evidence handling inside a controlled SOC environment.
