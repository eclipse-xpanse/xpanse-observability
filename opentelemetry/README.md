# OpenTelemetry Collector

For testing and debugging purposes, we can run this `OpenTelemetry` collector which only writes all received
traces, metrics and logs to stdout.

Run the below command to start the collector container.

```shell
docker run -d -p 127.0.0.1:4317:4317 -p 127.0.0.1:55679:55679 -v otel-collector-basic.yaml:/etc/otelcol-contrib/config.yaml ghcr.io/open-telemetry/opentelemetry-collector-releases/opentelemetry-collector-contrib:0.89.0
```