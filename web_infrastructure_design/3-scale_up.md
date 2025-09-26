# 3. Scale Up - Web vs Application Servers

**Diagram**:  
![Infrastructure Diagram](https://imgur.com/a/rypbq6j)

## ✅ System Architecture Overview

This configuration showcases a well-scaled and decoupled web infrastructure:

### 🔄 Load Balancer Cluster (HAProxy)
- Two HAProxy nodes deployed in **Active-Passive** configuration.
- Primary instance manages traffic distribution; secondary acts as a hot backup.
- Guarantees **high availability** when one load balancer experiences failure.

### 🌐 Web Servers (Nginx)
- Serve **static resources** (HTML, CSS, JavaScript, images).
- Route dynamic requests to application servers.
- Deploying multiple Nginx instances enhances performance and provides redundancy.

### ⚙️ Application Servers
- Execute application business logic (e.g., Python Flask, Node.js, Django).
- Interface with the backend database system.
- Decoupled from web servers to enable independent scaling.

### 🛢️ Database Server (MySQL)
- Centralized data management and storage.
- All application servers communicate with a **dedicated MySQL instance** (expandable to Master-Replica architecture later).

---

## 💡 Rationale for These Components

### ➕ Extra Server
- Boosts system capacity and overall performance.
- Separates responsibilities and strengthens fault tolerance.

### ➕ Secondary Load Balancer
- Eliminates **Single Point of Failure (SPOF)** in request distribution.
- Delivers **redundancy** and smooth failover through HA configuration.

### ⚙️ Separated Web/App/DB Servers
- Enhances **scalability**: Web and application tiers can expand independently.
- Strengthens **security**: Layer-specific access controls (e.g., database isolation from internet).
- Enables **performance optimization**: Each server type can be fine-tuned for its designated role.

---

## 🆚 Web Server vs Application Server

| Component          | Function                                   | Examples              |
|---------------------|-------------------------------------------|-----------------------|
| **Web Server**      | Processes HTTP requests, delivers static content | Nginx, Apache         |
| **Application Server** | Executes backend logic, produces dynamic responses | Gunicorn, uWSGI, Node.js |

---

## ✅ Important Insights

- Load balancers boost **reliability** and **request distribution**.
- Web servers concentrate on **content delivery** and **request forwarding**.
- Application servers manage **business logic processing**.
- Role separation achieves **superior architecture**, **component isolation**, and **horizontal scalability**.