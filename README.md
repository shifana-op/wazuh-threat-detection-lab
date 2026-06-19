# 🛡️ WAZUH Threat Detection Lab

*Centralized Security Monitoring, Threat Intelligence, and Automated Incident Response*
---

## 📌 Project Overview

This project documents the deployment and configuration of a Wazuh-based SIEM environment on Kali Linux using Docker.

In this project, I deployed Wazuh using Docker and configured multiple security capabilities including File Integrity Monitoring (FIM), VirusTotal integration, AlienVault OTX threat intelligence, MITRE ATT&CK mapping, and Active Response. The environment was tested using different attack simulation scenarios to validate detection and response functionality.

---

### 🛠️ Technologies Used

- Wazuh SIEM
- Docker
- Kali Linux
- VirusTotal API
- AlienVault OTX
- MITRE ATT&CK Framework
- Linux Auditd
- Git

---

### 🔍 Key Features Implemented

🗂️ File Integrity Monitoring (FIM)

Configured Wazuh to monitor files and directories in real time and generate alerts whenever files were created, modified, or deleted.

🦠 VirusTotal Integration

Integrated VirusTotal with Wazuh to automatically analyze file hashes and identify potentially malicious files.

🌐 AlienVault OTX Integration

Configured AlienVault OTX threat intelligence lookups to enrich alerts with external reputation information for suspicious IP addresses.

🎯 MITRE ATT&CK Mapping

Mapped security events to MITRE ATT&CK techniques to improve visibility into attacker behavior and investigation workflows.

🚨 Active Response

Configured automated response actions to block suspicious activity when predefined alert conditions were triggered.

---

### 📋 System Requirements

Wazuh Stack

- Operating System: Linux
- CPU: Minimum 4 Cores
- RAM: Minimum 8 GB
- Storage: Minimum 50 GB

Wazuh Agent

- Operating System: Linux
- CPU: Minimum 2 Cores
- RAM: Minimum 1 GB
- Storage: Minimum 10 GB

---

### 🏗️ Architecture
```text
Kali Linux Host
       │
       ▼
  Wazuh Agent
       │
       ▼
 Wazuh Manager
       │
 ┌─────────────┬─────────────┬─────────────┐
 │             │             │
 ▼             ▼             ▼
VirusTotal   AlienVault    MITRE ATT&CK
               OTX
       │
       ▼
 Active Response
```
---

### 🚨 Threat Validation Results

The environment was tested using multiple security scenarios to verify detection and response capabilities.


| Test Scenario | Method | Result |
|---------------|----------|----------|
| File Integrity Monitoring (FIM) | Created, modified, and deleted files in a monitored directory | ✅ Real-time alerts generated |
| VirusTotal Integration | Uploaded an EICAR test file to the monitored directory | ✅ Malicious file detected and alert generated |
| AlienVault OTX Integration | Queried a suspicious IP using the OTX integration script | ✅ Threat intelligence data retrieved |
| MITRE ATT&CK Mapping | Simulated suspicious activities and monitored alerts | ✅ Events mapped to MITRE ATT&CK techniques |
| Active Response | Triggered a VirusTotal detection event | ✅ Automated blocking action executed |
---

### 📁 Project Structure
```text
wazuh-docker/
└── single-node/
    ├── docker-compose.yml
    ├── generate-indexer-certs.yml
    └── config/
        └── wazuh_cluster/
            └── wazuh_manager.conf

/var/ossec/
├── etc/
│   └── ossec.conf
│
└── integrations/
    └── custom-alienvault.py

Active Response/
└── firewall-drop

Key Components:
* wazuh_manager.conf → VirusTotal Integration, Active Response Rules
* ossec.conf → Agent Configuration, FIM, OTX Integration, Audit Monitoring
* custom-alienvault.py → Threat Intelligence Lookup
* firewall-drop → Automated Threat Blocking
```
---

### 🚀 Deployment Steps

#### Environment Setup
```text
sudo apt update && sudo apt upgrade -y
sudo apt install docker.io -y
sudo systemctl start docker && sudo systemctl enable docker
sudo usermod -aG docker $USER
sudo apt install docker-compose -y
```

#### Deploy Wazuh Stack
```text
cd wazuh-docker/single-node

# Generate SSL certificates
docker compose -f generate-indexer-certs.yml run --rm generator   

# Generate SSL certificates
docker-compose up -d   # Start containers
```

#### Install and Configure Wazuh Agent
```text
sudo apt install wazuh-agent -y
sudo nano /var/ossec/etc/ossec.conf   # Set <address>127.0.0.1</address>

#start the agent
sudo systemctl enable wazuh-agent && sudo systemctl start wazuh-agent  
```
---

### 🖥️ Access Dashboard
```text
URL

http://127.0.0.1

Default Credentials

Username: admin

Password: SecretPassword
```
---

### 📸 Screenshots

Project screenshots demonstrating deployment, monitoring, alert generation, VirusTotal integration, MITRE ATT&CK mapping, and Active Response are available in the screenshots directory.

---

### Author

**Shifana Sherin OP**

Aspiring SOC Analyst focused on Security Monitoring, Threat Detection, and Incident Response.
