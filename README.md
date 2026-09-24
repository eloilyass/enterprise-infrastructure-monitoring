# Enterprise Infrastructure Monitoring

Dockerized infrastructure monitoring environment built with Prometheus, Node Exporter and Grafana on Ubuntu Linux.

## Overview

This project demonstrates the deployment of a complete infrastructure monitoring environment using open-source monitoring technologies.

The environment was deployed on Ubuntu Linux running inside VMware Workstation, with the monitoring stack containerized using Docker Compose.

The objective is to monitor infrastructure resources, collect system metrics and visualize them through an interactive Grafana dashboard.

## Architecture

```text
                    Ubuntu Linux
                 VMware Workstation
                         |
                         v
                  Docker Compose
                         |
          +--------------+--------------+
          |              |              |
          v              v              v
     Prometheus     Node Exporter     Grafana
      :9090            Metrics         :3000
          |              |
          +-------+------+
                  |
                  v
          Monitoring Dashboard
Technologies
Technology	Purpose
Ubuntu Linux	Operating system
VMware Workstation	Virtualization
Docker	Container runtime
Docker Compose	Container orchestration
Prometheus	Metrics collection and storage
Node Exporter	System metrics
Grafana	Metrics visualization
PromQL	Monitoring query language
Monitoring Dashboard

The Grafana dashboard monitors:

CPU utilization
Memory utilization
Disk utilization
Network traffic
Download traffic
Upload traffic
PromQL Queries
CPU Usage
100 - (avg by(instance) (rate(node_cpu_seconds_total{mode="idle"}[5m])) * 100)
Memory Usage
(1 - (node_memory_MemAvailable_bytes / node_memory_MemTotal_bytes)) * 100
Network Download
rate(node_network_receive_bytes_total{device!="lo"}[5m]) * 8
Network Upload
rate(node_network_transmit_bytes_total{device!="lo"}[5m]) * 8
Docker Environment

The monitoring environment is deployed using Docker Compose.

Main services:

Prometheus
Grafana
Nginx
Service Ports
Service	Port
Prometheus	9090
Grafana	3000
Nginx	8080
Deployment
Clone the repository
git clone https://github.com/eloilyass/enterprise-infrastructure-monitoring.git
cd enterprise-infrastructure-monitoring
Start the environment
docker compose up -d
Check running containers
docker ps
Access Prometheus
http://localhost:9090
Access Grafana
http://localhost:3000
Troubleshooting

During the deployment, a Docker volume mounting issue occurred with the Prometheus configuration file.

The issue was related to the host path being interpreted incorrectly as a directory instead of the expected configuration file.

The configuration structure was corrected and the containers were recreated:

docker compose down
docker compose up -d

The monitoring environment was then successfully deployed.

Project Structure
enterprise-infrastructure-monitoring/
|
├── prometheus/
│   └── prometheus.yml
|
├── grafana/
|
├── screenshots/
│   ├── monitoring-environment.png
│   ├── prometheus-query.png
│   └── ADMIN.png
|
├── docs/
│   └── Enterprise-Infrastructure-Monitoring.pdf
|
├── docker-compose.yml
└── README.md
Documentation

A complete technical report is included in this repository.

The documentation covers:

Infrastructure architecture
Docker deployment
Prometheus configuration
Node Exporter
Grafana dashboard
PromQL queries
Troubleshooting
Monitoring environment
Skills Demonstrated
Linux Administration
Docker
Docker Compose
Prometheus
Node Exporter
Grafana
PromQL
Infrastructure Monitoring
System Monitoring
Network Monitoring
Troubleshooting
VMware Workstation
Future Improvements
Add Alertmanager
Configure CPU and memory alerts
Add disk-space alerts
Monitor multiple Linux servers
Add Docker container metrics
Implement infrastructure alerting
Add centralized logging
Monitor network devices using SNMP
Add Grafana alert rules
Author

Ilyass El Ouarrari

Junior Systems & Network Administrator

Marrakech, Morocco

Technologies

Linux Docker Prometheus Node Exporter Grafana PromQL VMware

Feel free to explore the repository and provide feedback.
