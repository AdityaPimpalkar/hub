# VictoriaMetrics

Send the metrics of OpenEverest database instances to a VMAgent run by the
[VictoriaMetrics Operator](https://github.com/VictoriaMetrics/operator).
An OpenEverest **integration** (area: monitoring).

## How it fits

- **Class.** The chart installs the `victoriametrics` `MonitoringClass` and its
  controller. The class is **ExtensionManaged** and requires metrics: providers
  only expose metrics endpoints (natively or through an exporter sidecar).
- **Destination.** A `MonitoringDestination` of the class says how the
  generated VMPodScrapes are labelled and how often they are scraped.
- **Instance entry.** Listing the destination under
  `spec.monitoring.destinations[]` of an Instance makes the controller render
  one `VMPodScrape` per database component, which your VMAgent picks up
  through its `podScrapeSelector`.

## Prerequisites

- OpenEverest `2.0.0-dev.5` or later (monitoring API).
- The VictoriaMetrics Operator (`v0.75.x`) and a VMAgent that selects the
  generated VMPodScrapes.

## Source

- **Repo:** https://github.com/openeverest/monitoring-victoriametrics
- **Chart:** `oci://ghcr.io/openeverest/charts/monitoring-victoriametrics`

## Install (manual)

```bash
helm install monitoring-victoriametrics \
  oci://ghcr.io/openeverest/charts/monitoring-victoriametrics \
  --version 0.1.0 \
  --namespace everest-system
```

See the [repo README](https://github.com/openeverest/monitoring-victoriametrics#readme)
for destination parameters and chart values.
