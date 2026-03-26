# Monitorer et Observer les VMs multipass

> Proof of Concept : installer [Prometheus](https://prometheus.io/) et [Grafana](https://grafana.com/) avec [Docker compose](https://docs.docker.com/compose/) pour monitorer des VMs Ubuntu [Multipass](https://canonical.com/multipass)

## Stack

- Ubuntu Multipass
- Docker Compose
- Container Prometheus v3.10.0
- Grafana 12.3.6-security-01

## Architecture

```bash
Monitoring_Multipass/
├─ README.md
├─ compose.yml
└─ prometheus/
   └─ prometheus.yml
```

## 1. Installation

### prometheus-node-exporter dans les VMs

```shell
multipass exec multipass-vm-1 -- sudo apt install -y prometheus-node-exporter
```

!!! A voir automatisation de cette tache !!!

## 2. Prometheus & Grafana

``Penser à configuer prometheus.yml``

```shell
docker compose up -d
```

Prometheus : `http://localhost:9090`

Grafana : `http://localhost:3000`

- Login : Admin
- Password : Admin

Le lien de Grafana à Prometheus est fait grace a ce fichier :
`/grafana/provisioning/datasources/prometheus.yml`

## Sources

<https://blog.stephane-robert.info/docs/observabilite/>

<https://discourse.ubuntu.com/t/enhancing-multipass-metrics-with-prometheus-node-exporter/47663>

<https://agfianf.github.io/blog/2025/03/02/task-11-monitoring-server-memory-usage-with-prometheus-node-exporter/>
