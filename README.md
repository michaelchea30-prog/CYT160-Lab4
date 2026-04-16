# CYT160 – IoT Security Labs & Final Project

This repository contains my lab work and final project for **CYT160 – Security for Cloud and Internet of Things**.  
The focus of this course is building, monitoring, and securing MQTT‑based IoT pipelines using industry‑standard tools such as **Suricata**, **Docker**, **Filebeat**, and the **Elastic (ELK) Stack**.

All work was completed in a controlled lab environment for educational purposes.

---

## 🔹 Lab 4 – Containerizing the Security Stack

**Objective:**  
Containerize an IoT security monitoring stack using Docker, based on earlier manual deployments.

**Key Components:**
- **Mosquitto MQTT Broker**
- **Suricata IDS** (custom MQTT detection rules)
- **Filebeat** for log shipping
- **Elasticsearch** (host‑based)

**What This Lab Demonstrates:**
- Docker Compose orchestration of multiple security services
- Monitoring MQTT traffic on port 1883
- Detecting malformed payloads and suspicious shell patterns
- Shipping Suricata `eve.json` logs into Elasticsearch
- Verifying end‑to‑end flow:  
  `MQTT message → Suricata alert → Filebeat → Elasticsearch`

---

## 🔹 Project 2 – MQTT Attack Detection & Rule Analysis

**Objective:**  
Design and test custom Suricata rules to detect malicious MQTT activity.

**Focus Areas:**
- MQTT flood detection using `threshold` rules
- Payload inspection using `content`, `depth`, and `offset`
- Comparing plaintext MQTT (1883) vs TLS‑encrypted MQTT (8883)
- Understanding IDS vs IPS behavior

**Attacks Simulated:**
- Excessive publish rate (DoS‑style flood)
- Malformed payload injection
- Suspicious shell command patterns

---

## 🔹 Project 3 – IoT Security Pipeline with ELK Stack (Final Project)

**Objective:**  
Build a complete IoT security monitoring pipeline with real‑time visualization and analysis.

**Architecture Overview:**
- Raspberry Pi (sensor telemetry publisher)
- MQTT over port 1883
- AWS EC2 hosting:
  - Mosquitto
  - Suricata IDS
  - Filebeat
  - Logstash
  - Elasticsearch
  - Kibana

**Key Features:**
- Separate Elasticsearch indices for telemetry and security events
- Custom Suricata rules for:
  - MQTT flood attacks
  - Malicious payload inspection
- Logstash parsing and field enrichment
- Kibana dashboards for:
  - Sensor data
  - Attack spikes
  - Event counts and trends
- AWS CloudWatch alarm integration for CPU spikes during attacks

**Attacks Simulated:**
- MQTT connection flood (DoS)
- Malformed payload / command injection attempt

---

## 🔹 Technologies Used

- Docker & Docker Compose
- Mosquitto MQTT
- Suricata IDS
- Filebeat & Logstash
- Elasticsearch & Kibana
- AWS EC2 & CloudWatch
- Python (MQTT publishers and attack scripts)

---

## ⚠️ Disclaimer

This repository is for **educational purposes only**.  
All attacks were performed in isolated lab environments against systems intentionally configured for testing.

---

## 👤 Author

**Michael Chea**  
CYT160 – Security for Cloud and Internet of Things  
