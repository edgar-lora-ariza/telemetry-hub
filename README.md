# Observability Stack with Grafana

This repository contains the Docker Compose configuration needed to implement a complete observability stack using Grafana, Prometheus, Loki, Tempo, and OpenTelemetry Collector. This setup is designed to provide a comprehensive monitoring system with visualization of metrics, logs, and traces.

## Components

- **Grafana**: Dashboard and visualization
- **Prometheus**: Metrics storage and querying
- **Loki**: Log storage and querying
- **Tempo**: Trace storage and querying
- **OpenTelemetry Collector**: Telemetry collection and export

## Requirements

- Docker
- Docker Compose
- Minimum of 4GB RAM available

## Repository Structure

```
.
├── docker-compose.yml
├── grafana/
│   └── provisioning/
│       └── datasources/
│           └── datasources.yaml
├── loki/
│   └── local-config.yaml
├── prometheus/
│   └── prometheus.yml
├── tempo/
│   └── tempo-local.yaml
└── otel-collector-config.yml
```

## Installation and Execution

1. Clone this repository
2. Run the stack with Docker Compose:

```bash
docker-compose up -d
```

3. Access Grafana at http://localhost:3000 (username: admin, password: admin)

## Component Configuration

### Service Configuration

Each component of the stack has its own configuration:

- **Grafana**: Configured with pre-established datasources
- **Prometheus**: Configured to collect metrics from the OTEL collector and applications
- **Loki**: Configured for local log storage
- **Tempo**: Configured to receive traces via OTLP
- **OpenTelemetry Collector**: Configured as a central collection point

## Available Endpoints

- **Grafana**: http://localhost:3000
- **Prometheus**: http://localhost:9090
- **Loki**: http://localhost:3100
- **Tempo**: http://localhost:3200
- **OpenTelemetry Collector**: http://localhost:4318 (OTLP HTTP)

## Volumes

The stack uses the following volumes for persistence:

- `grafana-storage`: Grafana configuration and data
- `prometheus-data`: Metrics stored by Prometheus
- `loki-chunks`, `loki-index`, etc.: Loki data
- `tempo-data`: Traces stored by Tempo

## Troubleshooting

### Common issues:

1. **Container startup failure**: Check logs with `docker-compose logs [service]`
2. **No data in Grafana**: Verify that datasources are correctly configured
3. **Connectivity issues**: Verify that the `monitoring-network` is working properly
4. **Tempo errors**: Ensure the service is healthy before sending traces

## License

MIT