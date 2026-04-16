# CYT160 – IoT Security Labs & Final Project

This repository contains my lab work and final project for **CYT160 – Security for Cloud and Internet of Things**.  
The course focuses on building, monitoring, and securing MQTT‑based IoT pipelines using industry‑standard tools such as **Suricata**, **Docker**, **Filebeat**, and the **Elastic (ELK) Stack**, along with TLS hardening and traffic analysis.

All work was completed in a controlled lab environment for educational purposes.

---

## 🔹 Lab 4 – Containerizing the Security Stack

**Objective:**  
Containerize an IoT security monitoring stack using Docker, based on earlier manual deployments.

**Key Components:**
- Mosquitto MQTT broker
- Suricata IDS with custom MQTT rules
- Filebeat for log shipping
- Elasticsearch (running on the host)

**Key Outcomes:**
- Docker Compose orchestration of all services
- Suricata monitoring MQTT traffic on port 1883
- Detection of malformed payloads and suspicious shell patterns
- End‑to‑end log flow verification:  
  `MQTT → Suricata → Filebeat → Elasticsearch`

---

## 🔹 Lab 5 – Securing MQTT with TLS & Traffic Analysis

**Objective:**  
Harden the MQTT pipeline using TLS and analyze the security impact of encrypted vs plaintext traffic.

**Focus Areas:**
- MQTT over plaintext (**port 1883**) vs TLS (**port 8883**)
- Certificate‑based authentication using Mosquitto
- Packet capture (pcap) analysis using `tcpdump`
- Understanding IDS visibility limitations with encrypted traffic

**What This Lab Demonstrates:**
- Clear visibility of MQTT payloads in plaintext pcaps
- Encrypted and unreadable payloads when TLS is enabled
- Enforcement of mutual TLS using `require_certificate true`
- Rejection of clients without valid certificates
- Threat detection strategies for encrypted traffic based on metadata (IP, ports, timing, connection behavior)

---

## 🔹 Project 2 – MQTT Attack Detection & Rule Analysis

**Objective:**  
Design, test, and analyze custom Suricata rules for detecting malicious MQTT activity.

**Key Topics:**
- Threshold‑based detection for MQTT flood attacks
- Payload inspection using `content`, `depth`, and `offset`
- IDS vs IPS behavior and rule actions (`alert` vs `drop`)
- Plaintext vs TLS trade‑offs for detection

**Attacks Simulated:**
- Excessive publish‑rate flood (DoS‑style attack)
- Malformed payload injection
- Suspicious shell command patterns in MQTT messages

---

## 🔹 Project 3 – IoT Security Pipeline with ELK Stack (Final Project)

**Objective:**  
Build a complete IoT security monitoring pipeline with ingestion, analysis, and visualization.

**Architecture Overview:**
- Raspberry Pi publishing telemetry data
- MQTT broker on AWS EC2
- Suricata IDS monitoring MQTT traffic
- Filebeat and Logstash for log parsing and enrichment
- Elasticsearch for indexing
- Kibana dashboards for visualization
- AWS CloudWatch alarms for system impact monitoring

**Key Features:**
- Separate indices for telemetry and security events
- Custom Suricata MQTT rules
- Logstash field mapping and enrichment
- Detection of DoS floods and malicious payloads
- Visualization of attack spikes and event trends
- CloudWatch CPU alerts triggered during attack simulations

---

## 🔹 Technologies Used

- Docker & Docker Compose
- Mosquitto MQTT
- Suricata IDS
- Filebeat & Logstash
- Elasticsearch & Kibana
- AWS EC2 & CloudWatch
- Python (MQTT publishers and test scripts)
- tcpdump & packet capture analysis

---

## ⚠️ Disclaimer

This repository is for **educational purposes only**.  
All attacks and simulations were performed in isolated lab environments against systems intentionally configured for testing.

---

## 👤 Author

**Michael Chea**  
 
