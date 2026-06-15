# 🛡️ Web Application Security Monitoring Using Wazuh SIEM

## 📖 Introduction

Security Information and Event Management (SIEM) systems play a critical role in modern cybersecurity by collecting, analyzing, and correlating security logs from multiple sources in real time. These platforms help organizations detect threats, monitor security events, investigate incidents, and maintain compliance requirements.

This project demonstrates the deployment and configuration of the **Wazuh SIEM Platform** using **Docker containers** in a **Kali Linux** environment. The implementation includes setting up the Wazuh Manager, Wazuh Indexer (OpenSearch), and Wazuh Dashboard while addressing deployment challenges such as SSL certificate management, OpenSearch connectivity issues, and container troubleshooting.

The project provides hands-on experience in deploying enterprise-level security monitoring infrastructure and understanding centralized log management, threat detection, and security event monitoring.

---

# 🎯 Project Objectives

- Install and configure Docker in Kali Linux
- Deploy Wazuh SIEM using Docker Compose
- Configure Wazuh Manager, Wazuh Indexer, and Wazuh Dashboard
- Understand SSL certificate generation and management
- Troubleshoot OpenSearch deployment issues
- Verify dashboard accessibility and functionality
- Learn centralized security monitoring concepts
- Understand threat detection and event correlation mechanisms

---

# 🏗️ Project Architecture

```text
                    +----------------------+
                    |   Wazuh Dashboard    |
                    |  (Web Interface)     |
                    +----------+-----------+
                               |
                               |
                    +----------v-----------+
                    |    Wazuh Indexer     |
                    |    (OpenSearch)      |
                    +----------+-----------+
                               |
                               |
                    +----------v-----------+
                    |    Wazuh Manager     |
                    | Threat Detection     |
                    +----------+-----------+
                               |
                               |
                    +----------v-----------+
                    | Security Logs/Events |
                    +----------------------+
```

---

# 🛠️ Technologies Used

| Technology | Purpose |
|------------|---------|
| Kali Linux | Security Testing Operating System |
| Oracle VirtualBox | Virtualization Platform |
| Docker | Containerization Platform |
| Docker Compose | Multi-Container Deployment |
| Wazuh SIEM | Security Monitoring Platform |
| OpenSearch | Log Storage and Indexing |
| Linux Terminal | Command Execution |
| Mozilla Firefox | Dashboard Access |

---

# 💻 System Requirements

## Hardware Requirements

- Minimum 4 GB RAM
- Dual-Core Processor
- 80 GB Storage
- Stable Internet Connection

## Software Requirements

- Oracle VirtualBox
- Kali Linux
- Docker
- Docker Compose
- Git
- Wazuh Docker Repository

---

# 🚀 Installation and Deployment

## Step 1: Update Kali Linux

```bash
sudo apt update
sudo apt upgrade -y
```

---

## Step 2: Install Docker and Docker Compose

```bash
sudo apt install docker.io docker-compose -y
```

Verify installation:

```bash
docker --version
docker-compose --version
```

---

## Step 3: Enable Docker Services

```bash
sudo systemctl enable docker
sudo systemctl start docker
sudo systemctl status docker
```

---

## Step 4: Clone Wazuh Docker Repository

```bash
git clone https://github.com/wazuh/wazuh-docker.git
```

Navigate to deployment folder:

```bash
cd wazuh-docker/single-node
```

---

## Step 5: Verify Wazuh Configuration

Check dashboard configuration:

```bash
cat docker-compose.yml | grep wazuh-dashboard
```

Validate Docker Compose configuration:

```bash
docker-compose config
```

---

## Step 6: Configure Wazuh Version

Verify configured version:

```bash
cat docker-compose.yml | grep 4.9.0
```

The deployment uses **Wazuh Version 4.9.0** for improved compatibility and stability.

---

## Step 7: Verify Directory Structure

```bash
find . -type d
```

---

## Step 8: Fix Certificate Permissions

```bash
sudo chmod -R 755 ./config
sudo chown -R 1000:1000 ./config
```

Verify certificates:

```bash
ls -l ./config/wazuh_indexer/certs
```

---

## Step 9: Generate SSL Certificates

Remove old certificates:

```bash
sudo rm -rf ./config/wazuh_indexer_ssl_certs
```

Generate new certificates:

```bash
docker compose -f generate-indexer-certs.yml run --rm generator
```

Verify generated certificates:

```bash
file ./config/wazuh_indexer_ssl_certs/*
```

---

## Step 10: Deploy Wazuh Containers

Start all services:

```bash
docker compose up -d
```

Verify running containers:

```bash
docker ps
```

---

## Step 11: Verify OpenSearch Connectivity

```bash
curl -k -u admin:SecretPassword https://localhost:9200
```

Expected Result:

```json
{
  "name":"wazuh.indexer",
  "cluster_name":"wazuh-cluster",
  "version":"2.x"
}
```

---

## Step 12: Access Wazuh Dashboard

Open browser and visit:

```text
https://localhost
```

Login using administrator credentials configured during deployment.

---

# 🔧 Troubleshooting

## OpenSearch SSL Permission Error

Check logs:

```bash
docker logs single-node-wazuh.indexer --tail 30
```

Common Error:

```text
Permission denied while reading SSL certificates
```

Solution:

```bash
sudo chmod -R 755 ./config
sudo chown -R 1000:1000 ./config
```

---

## Dashboard Not Loading

Verify containers:

```bash
docker ps
```

Restart services:

```bash
docker compose restart
```

---

## Certificate Issues

Remove old certificates:

```bash
sudo rm -rf ./config/wazuh_indexer_ssl_certs
```

Regenerate:

```bash
docker compose -f generate-indexer-certs.yml run --rm generator
```

---

# 📊 Features Implemented

### ✅ Centralized Log Monitoring

Collects and analyzes logs from multiple systems.

### ✅ Security Event Correlation

Correlates events across various security sources.

### ✅ Threat Detection

Detects suspicious activities and security incidents.

### ✅ Vulnerability Assessment

Provides visibility into vulnerable systems.

### ✅ File Integrity Monitoring

Detects unauthorized file modifications.

### ✅ Compliance Monitoring

Supports compliance auditing and reporting.

### ✅ OpenSearch Integration

Stores and indexes security events efficiently.

### ✅ Dashboard Visualization

Provides a user-friendly interface for monitoring.

---

# 📸 Screenshots

Add your screenshots in a folder called:

```text
screenshots/
```

Example:

```text
screenshots/
│
├── virtualbox-setup.png
├── kali-running.png
├── docker-installation.png
├── docker-service.png
├── repository-clone.png
├── certificate-generation.png
├── deployment.png
├── dashboard-login.png
├── dashboard-home.png
└── opensearch-verification.png
```

---

# 🔍 Observations

- Docker containers were deployed successfully.
- SSL certificate permission issues affected initial deployment.
- Regenerating SSL certificates resolved OpenSearch communication issues.
- Wazuh Dashboard became accessible after successful configuration.
- OpenSearch API responded successfully over secure HTTPS.
- Centralized monitoring infrastructure was implemented successfully.
- Dashboard monitoring and threat hunting features were validated.

---

# 📈 Future Enhancements

### Endpoint Monitoring

Deploy Wazuh agents on multiple endpoints for real-time monitoring.

### Threat Intelligence Integration

Integrate external threat intelligence feeds.

### VirusTotal Integration

Automate malware reputation checking.

### Email Notifications

Configure automated alert emails.

### Webhook Integrations

Send alerts to external platforms.

### Multi-Node Architecture

Deploy Wazuh in clustered mode for scalability.

### Advanced Correlation Rules

Implement custom detection and response rules.

### Live Attack Simulation

Generate security events for testing alert mechanisms.

### Elastic Stack Integration

Enhance visualization and analytics capabilities.

---

# 📚 Learning Outcomes

Through this project, the following concepts were learned:

- Docker-based deployment
- Container orchestration
- SSL certificate management
- OpenSearch administration
- SIEM architecture
- Security event monitoring
- Threat detection workflows
- Dashboard configuration
- Troubleshooting security infrastructure
- Centralized log management

---

# 📂 Project Structure

```text
Web-Application-Security-Monitoring-Using-Wazuh-SIEM/
│
├── screenshots/
│   ├── dashboard-login.png
│   ├── dashboard-home.png
│   └── deployment.png
│
├── README.md
│
└── report/
    └── Web_Application_Security_Monitoring_Using_Wazuh_SIEM.pdf
```

---

# 📚 References

- Wazuh Official Documentation
- Docker Official Documentation
- OpenSearch Documentation
- Kali Linux Documentation
- Oracle VirtualBox Documentation
- Wazuh Docker GitHub Repository

---

# 👨‍💻 Author

## Anirudh Gupta

Cybersecurity Project

**Project Title:** Web Application Security Monitoring Using Wazuh SIEM

---

# ⭐ Support

If you found this project useful, consider giving it a ⭐ on GitHub.

---

# ⚠️ Disclaimer

This project was developed strictly for educational and learning purposes. The deployment environment was created in a controlled lab setup using Kali Linux and Docker containers. Do not use the techniques demonstrated here against systems without proper authorization.
