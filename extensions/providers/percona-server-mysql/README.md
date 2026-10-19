# Percona Server for MySQL

Highly available MySQL clusters managed by the
[Percona Operator for MySQL based on Percona Server for MySQL](https://github.com/percona/percona-server-mysql-operator),
wrapped as an OpenEverest **provider**. Supports asynchronous replication and
MySQL Group Replication topologies.

## Source

- **Provider repo:** https://github.com/openeverest/provider-percona-server-mysql
- **Chart:** `oci://ghcr.io/openeverest/charts/provider-percona-server-mysql`

## Install (manual)

> The OpenEverest CLI install path (`everestctl extension install`) ships in
> Phase 2. Until then, use Helm directly:

```bash
helm install provider-percona-server-mysql \
  oci://ghcr.io/openeverest/charts/provider-percona-server-mysql \
  --version 0.2.0 \
  --namespace everest-system \
  --create-namespace
```

