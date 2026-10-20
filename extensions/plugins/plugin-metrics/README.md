# Metrics

An OpenEverest generic plugin that adds a **Metrics** tab to database cluster
detail pages, so users can take a quick look at an instance's metrics without
switching to Grafana.

**Features:**
- A small dashboard per provider (CPU, memory and engine-specific panels) with
  a *Last hour / Last 24 hours* switch
- Search any other metric the instance exposes and chart it for the session
- Reads from Prometheus (via the instance's PodMonitors/ServiceMonitors) or
  PMM (via the instance's `MonitoringConfig`)
- Custom or replacement dashboards through chart values or a ConfigMap,
  applied without a restart

Built-in dashboards cover Milvus, Valkey, MariaDB, MSSQL, Cassandra,
CloudNativePG, TiDB, Percona Server for MongoDB, Percona PostgreSQL and
Percona XtraDB Cluster. Users only see metrics of instances they are allowed
to read.

## Requirements

- For Prometheus: the [Prometheus Operator](https://prometheus-operator.dev)
  and a Prometheus that selects the instances' monitors, with Prometheus
  monitoring enabled on the instance.
- For PMM: PMM 3 and a Percona provider with monitoring enabled on the
  instance through a `MonitoringConfig`.

## Source

- **Plugin repo:** https://github.com/openeverest/plugin-metrics
- **Chart:** `oci://ghcr.io/openeverest/charts/plugin-metrics`

## Install (manual)

```bash
helm upgrade plugin-metrics \
  oci://ghcr.io/openeverest/charts/plugin-metrics \
  --version 0.2.0 \
  --namespace everest-system \
  --set prometheus.url=http://kube-prometheus-stack-prometheus.monitoring.svc:9090 \
  --install
```

Set `prometheus.url` to your in-cluster Prometheus HTTP API. See the
[plugin README](https://github.com/openeverest/plugin-metrics#readme) for all
values and custom dashboards.
