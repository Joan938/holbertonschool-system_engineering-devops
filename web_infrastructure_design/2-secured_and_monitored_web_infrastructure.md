# 2. Secured and Monitored Web Infrastructure

**Diagram**:  
[View Diagram](https://imgur.com/a/S56ddvj)

## ✅ Components and Their Purpose

### 🔒 Firewalls (3)
- Safeguard public entry points and backend servers.
- Filter traffic to allow only required connections (e.g., port 443 for HTTPS, port 3306 for MySQL access).
    - First firewall positioned before the Load Balancer.
    - Second firewall protecting the application servers.
    - Third firewall securing the MySQL database servers.

### 🛡️ SSL Certificate
- Implemented on the Load Balancer to provide `https://www.foobar.com`.
- Secures communication between user browsers and servers, maintaining data privacy and integrity.

### 📊 Monitoring Clients (3)
- Gather system performance and health data.
- Deployed across all web/application servers.
- Send logs and metrics to monitoring platforms such as **Sumo Logic**, **Datadog**, or **Prometheus**.

---

## 🔍 Core Concepts Overview

### 🔥 Purpose of Firewalls
- Regulate network traffic according to predefined security rules.
- Shield infrastructure components from unauthorized intrusion or harmful traffic.

### 🌐 Benefits of HTTPS Traffic
- Secures the communication channel between users and web servers.
- Guards against eavesdropping, data interception, and content modification.
- Critical for maintaining security and user confidence.

### 📈 Role of Monitoring
- Identifies system failures, performance issues, or traffic anomalies.
- Supports alerting mechanisms and automated scaling/recovery operations.

### 📋 Monitoring Data Collection Methods
- Monitoring software operates on servers to:
    - Capture log files (e.g., Nginx access/error logs).
    - Record system performance (CPU, memory, storage, network usage).
    - Transmit information to centralized services using HTTPS or TCP protocols.

### ❓ Tracking QPS (Queries Per Second)
- Activate Nginx or application server request logging.
- Utilize monitoring tools such as:
    - `GoAccess` for live log analysis.
    - `Prometheus` + `Grafana` for QPS visualization.
    - Configure monitoring agents to parse QPS data from logs or system metrics.

---

## ⚠️ Infrastructure Limitations

### 🔐 SSL Termination at Load Balancer Level
- **Issue**: SSL decryption occurs at the Load Balancer, leaving backend communication unencrypted.
- **Vulnerability**: Internal network traffic remains exposed to potential interception.
- **Resolution**: Implement **end-to-end encryption** (re-encrypt backend traffic) or deploy internal TLS certificates.

### 🗄️ Single MySQL Primary Node
- **Issue**: Write operations are restricted to one database node.
- **Vulnerability**: Primary node failure prevents all write operations.
- **Resolution**: Implement automated failover mechanisms or configure multi-master replication (with proper conflict handling).

### 📦 Combined Server Functions (App + DB)
- **Issue**: Database, application, and web services operate on shared servers.
- **Vulnerability**: Tight coupling complicates scaling efforts and performance isolation.
- **Resolution**: Deploy dedicated database infrastructure and separate service layers (microservices or tiered architecture).

---