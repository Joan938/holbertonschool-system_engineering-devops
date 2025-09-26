# 1. Distributed Web Infrastructure

## Diagram  
![Distributed Web Infrastructure](https://imgur.com/a/ztZOm8n)

## Infrastructure Elements
- **1 Load Balancer** (HAProxy)
- **2 Web/Application Servers**
    - Nginx
    - Application codebase
    - MySQL database (Master + Slave)

## Purpose of These Elements
- **Load Balancer**: Guarantees high availability and distributes incoming traffic.
- **Multiple Servers**: Offer redundancy and horizontal scaling capabilities.
- **Master-Slave MySQL**: Delivers data redundancy and separates read/write workloads.

## Load Balancer Configuration
- **Algorithm**: Round Robin — rotates requests between both servers sequentially.
- **Setup**: Active-Active — both servers process traffic concurrently.

## Database Replication Structure
- **Master Node**: Processes all write operations and data modifications.
- **Slave Node**: Receives synchronized data updates and handles read-only queries.
- Guarantees data persistence and workload distribution.

## Infrastructure Problems
- **Single Point of Failure (SPOF)**: Load balancer lacks redundancy or backup.
- **Security Gaps**: Missing firewall protection and HTTPS encryption.
- **No Monitoring**: Absence of server health tracking, traffic analysis, or alerting systems.