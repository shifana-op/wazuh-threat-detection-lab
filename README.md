🛡️ WAZUH Threat Detection Lab

📌 Project Overview

As part of my cybersecurity learning journey, I built a Wazuh-based SIEM lab on Kali Linux to gain practical experience in security monitoring, threat detection, threat intelligence integration, and incident response.

In this project, I deployed Wazuh using Docker and configured multiple security capabilities including File Integrity Monitoring (FIM), VirusTotal integration, AlienVault OTX threat intelligence, MITRE ATT&CK mapping, and Active Response. The environment was tested using different attack simulation scenarios to validate detection and response functionality.

---

🛠️ Technologies Used

- Wazuh SIEM
- Docker
- Kali Linux
- VirusTotal API
- AlienVault OTX
- MITRE ATT&CK Framework
- Linux Auditd
- Git

---

🔍 Key Features Implemented

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

📋 System Requirements

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

🏗️ Architecture

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

---

## 🚨 Threat Validation Results

| Test Scenario | Method | Result |
|---------------|----------|----------|
| File Integrity Monitoring (FIM) | Created, modified, and deleted files in a monitored directory | ✅ Real-time alerts generated |
| VirusTotal Integration | Uploaded an EICAR test file to the monitored directory | ✅ Malicious file detected and alert generated |
| AlienVault OTX Integration | Queried a suspicious IP using the OTX integration script | ✅ Threat intelligence data retrieved |
| MITRE ATT&CK Mapping | Simulated suspicious activities and monitored alerts | ✅ Events mapped to MITRE ATT&CK techniques |
| Active Response | Triggered a VirusTotal detection event | ✅ Automated blocking action executed |
---

📁 Project Structure

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

---

🚀 Deployment Steps

Deploy Wazuh Stack

sudo apt update
sudo apt install docker.io docker-compose git -y

git clone https://github.com/wazuh/wazuh-docker.git -b v4.14.0

cd wazuh-docker/single-node

docker compose -f generate-indexer-certs.yml run --rm generator

docker-compose up -d

Install and Configure Wazuh Agent

sudo apt install wazuh-agent -y
sudo nano /var/ossec/etc/ossec.conf

Configure manager address:

<address>127.0.0.1</address>

Start the agent:

sudo systemctl enable wazuh-agent
sudo systemctl start wazuh-agent

---

🖥️ Access Dashboard

URL

http://127.0.0.1

Default Credentials

Username: admin
Password: SecretPassword

---

📸 Screenshots

Project screenshots demonstrating deployment, monitoring, alert generation, VirusTotal integration, MITRE ATT&CK mapping, and Active Response are available in the screenshots directory.

---

🧠 What I Learned

Through this project, I gained hands-on experience with:

- SIEM Deployment and Administration
- Security Monitoring
- Log Analysis
- Threat Detection
- Threat Intelligence Integration
- Incident Response Concepts
- Linux Administration
- Docker-Based Deployments

---

## Author

**Shifana Sherin OP**

Aspiring SOC Analyst focused on Security Monitoring, Threat Detection, and Incident Response.
