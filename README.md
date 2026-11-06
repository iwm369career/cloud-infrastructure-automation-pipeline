# Cloud Infrastructure Automation & CI/CD Pipeline

Repositori ini berisi infrastruktur terautomasi di AWS yang dibangun menggunakan Terraform, dikemas dalam Docker container, di-deploy otomatis melalui GitHub Actions, serta dipantau dengan Prometheus dan Grafana.

## 🏗️ Diagram Arsitektur

```mermaid
graph TD
    User([Pengguna / Internet]) -->|HTTP Port 80| SG[AWS Security Group]
    SG --> EC2[AWS EC2 Instance - Ubuntu]
    
    subgraph EC2 Instance
        App[Docker Container: Web App]
        Exporter[Node Exporter: Metrik System]
        Prometheus[Prometheus Server]
        Grafana[Grafana Dashboard - Port 3000]
    end
    
    Prometheus -->|Scrape Metrics| Exporter
    Grafana -->|Query Data| Prometheus