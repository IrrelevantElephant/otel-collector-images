
```shell
docker run -v "$(pwd)/otelcol-builder.yaml:/build/builder-config.yaml" -v "$(pwd)/output:/build/otelcol-dev" otel/opentelemetry-collector-builder:0.117.0
```