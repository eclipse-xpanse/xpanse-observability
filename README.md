# xpanse-observability

We aim to provide observability to xpanse project with flexibility at its core. This is similar to all other features in
the xpanse ecosystem.

The main element in the xpanse observability feature is the use of [openTelemetry](https://opentelemetry.io/) to
generate
data. We use all instrumentation provided by openTelemetry to generate
traces, metrics and logs.

## Components

1. openTelemetry SDK - This is running with the application being observed. It generates all traces, metrics and logs
   and forwards it to the collector.
2. openTelemetry Collector - This is an independent process that receives all data exported from the openTelemetry SDKs
   and forwards to other systems as required.
   The collector need not be the
   official [openTelemetry collector](https://opentelemetry.io/docs/collector/getting-started/) from openTelemetry
   always but can be any system such as Jaeger, Grafana stack, etc that have the OLTP (OpenTelemetry Protocol)
   implemented to receive data.
3. Backend - This is also one or many independent system(s) that can store the generated data and provide ways to
   visualize, report, etc with the data captured.

## Reference Implementation

Similar to our other components, we provide a reference implementation for observability too. This can be found
under [grafana-stack](grafana-stack) folder.
This implementation uses the following components.

1. openTelemetry Collector container
2. Grafana Tempo - For collecting Traces
3. Grafana Prometheus - For collecting Metrics
4. Grafana Loki - For collecting logs
5. Grafana UI - For viewing all data collected

This implementation uses basic configurations such as local backend to store data and single containers to host all
components. The components can be scaled and re-configured as necessary. 

### Start Reference Implementation
The complete reference implementation stack can be started using the below commands

```shell
cd grafana-stack
docker compose up
```

This command will start 5 containers and the granfana UI can be accessed on port 4000.