# Maize Kafka + AKHQ

A WME-ready single-node Apache Kafka 4.3.1 deployment with AKHQ 0.27.1. Compose project isolation owns container, network, and volume names.

## WME setup

Create a **Docker Compose from GitHub** processor definition with this repository, branch `main`, and no required data interfaces. The deployed Kafka broker is reachable by other services in this Compose project as `kafka:9092`, and externally through the configured host and port.

| Parameter | Default | Purpose |
|---|---:|---|
| `KAFKA_EXTERNAL_PORT` | `19092` | Host Kafka port |
| `AKHQ_EXTERNAL_PORT` | `18081` | Host AKHQ port |
| `KAFKA_ADVERTISED_HOST` | `localhost` | Worker host/IP advertised externally |
| `KAFKA_AUTO_CREATE_TOPICS_ENABLE` | `true` | Topic auto-creation |
| `KAFKA_NUM_PARTITIONS` | `3` | Default partition count |

Ports intentionally avoid the WME platform's common `9092` and `8081` bindings. When multiple manifests target the same worker, assign distinct external ports.

Validate with `docker compose config`; run with `docker compose up -d` and inspect AKHQ at `http://localhost:18081`.

Apache-2.0 licensed.
