# Kong + Konga + Grafana + Loki + Prometheus Monitoring Stack

This is a Docker Compose setup for managing an API Gateway and monitoring/logging stack.

## 🔧 Stack Includes

| Service       | Description                       | Port(s)    |
| ------------- | --------------------------------- | ---------- |
| Kong          | API Gateway                       | 8000, 8001 |
| Konga         | GUI for managing Kong             | 1337       |
| Prometheus    | Metrics scraping system           | 9090       |
| Grafana       | Visual dashboard for metrics/logs | 3000       |
| Loki          | Log aggregation backend           | 3100       |
| Promtail      | Log forwarder to Loki             | —          |
| Node Exporter | Host system metrics               | 9100       |

## 📂 Project Structure

```
.
├── docker-compose.yaml
├── Dockerfile
├── loki-config.yaml
├── promtail-config.yaml
├── prometheus.yml
├── app.log
```

## 🚀 Getting Started

### Clone and Start

```bash
git clone https://github.com/yourname/kong-monitoring-stack.git
cd kong-monitoring-stack
docker-compose up -d
```

### Access URLs

| Component  | URL                   |
| ---------- | --------------------- |
| Kong Admin | http://localhost:8001 |
| Kong Proxy | http://localhost:8000 |
| Konga UI   | http://localhost:1337 |
| Grafana    | http://localhost:3000 |
| Prometheus | http://localhost:9090 |

> Grafana login: `admin / admin`

## ⚙️ Configurations

### Prometheus (`prometheus.yml`)

Scrapes metrics from Kong and Node Exporter.

### Loki (`loki-config.yaml`)

- Retains logs for 7 days
- Stores in local filesystem

### Promtail (`promtail-config.yaml`)

- Collects logs from containers and host logs
- Parses structured JSON logs

## 🧪 Troubleshooting

- **Check Kong status:** `curl http://localhost:8001/status`
- **Check container logs:** `docker logs kong` etc.
- **Fix Promtail issues:** Avoid duplicate `__path__` entries

## 🧹 Cleanup

```bash
docker-compose down -v
```

## 📜 License

MIT License
