# SIEM & SOC Telemetry Lab

## Project Overview
This project demonstrates the deployment, configuration, and operational use of a Wazuh Security Information and Event Management (SIEM) system. The objective was to architect a multi-node virtualized environment, simulate real-world cyber attacks, and analyze the resulting telemetry to identify indicators of compromise (IoCs) mapped to the MITRE ATT&CK framework.

## Architecture & Topology
* **SIEM Manager:** Wazuh Dashboard/Manager (Host Machine)
* **Target Server:** Ubuntu Server (VirtualBox)
* **Attacking Machine:** Parrot OS
* **Network Protocol:** Bridged Adapter routing for isolated host-to-guest telemetry.

## 🛠️ Tools & Technologies
* **Infrastructure:** VirtualBox, Linux (Ubuntu/Parrot), UFW (Uncomplicated Firewall)
* **Security & SIEM:** Wazuh Agent, Wazuh Manager
* **Reconnaissance & Attack:** Nmap, UDPx, Netcat, SSH Brute-Forcing

## 🚀 Methodology & Execution

### 1. Infrastructure Engineering & Network Bridging
* Transitioned the target VM from a standard NAT framework to a Bridged Adapter to ensure proper IP allocation on the local network.
* Configured host-based firewalls (`ufw`) on the target server to explicitly allow inbound communication on specific logging and authentication ports (TCP/UDP 1514, TCP 1515).
* Successfully registered the Wazuh agent and forced manual handshakes to resolve manager-agent mapping conflicts.

### 2. Attack Simulation & Telemetry Generation
Conducted external network probing and authentication attacks against the target server to generate live security telemetry:
* **Reconnaissance:** Executed aggressive stealth scans (`nmap -sS -T5`) and UDP probing (`udpx`) to enumerate active services and OS fingerprint data.
* **Initial Access:** Simulated an automated SSH credential stuffing/brute-force attack. 

### 3. Detection & Log Analysis
Utilized the Wazuh Manager to ingest, parse, and analyze raw JSON event logs from the target server.
* Detected and correlated the rapid SSH authentication failures.
* Mapped the observed malicious behaviors to **MITRE ATT&CK Technique T1110 (Brute Force)**.

## 📸 Proof of Concept (Screenshots)
*(Insert a screenshot of your Wazuh dashboard showing the T1110 Brute Force alerts here)*

*(Insert a screenshot of the Nmap/UDPx alerts here)*
