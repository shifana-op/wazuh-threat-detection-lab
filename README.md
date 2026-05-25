# WAZUH-VT-THREATATTACK
### An Integrated Framework for Automated Threat Intelligence Incident Response

*Prepared by:* Shifana Sherin O P

This repository documents how I deployed and configured Wazuh, an open-source Security Information and Event Management (SIEM) platform, within a Kali Linux environment. My goal for this project was to establish a centralized security monitoring hub that doesn't just collect logs, but actively enriches them and automatically blocks threats.

## Core Setup & Features
* *SIEM Core:* Single-node Wazuh stack (Manager, Indexer, Dashboard) running v4.14.0 via Docker Engine.
* *Integrations:* VirusTotal API (for automated malware hash scanning) and AlienVault OTX (for checking bad network IPs).
* *Framework Mapping:* Alerts mapped directly to the MITRE ATT&CK Matrix.
* *Automation:* Active Response rules that trigger local endpoint firewall blocks automatically.

---

## My Deployment Log & Screenshots

### 1. Downloading the Setup Files
I updated my packages and pulled down the official Wazuh docker configuration files using Git.
```bash
sudo apt update && sudo apt install docker.io docker-compose git -y
git clone [https://github.com/wazuh/wazuh-docker.git](https://github.com/wazuh/wazuh-docker.git) -b v4.14.0
