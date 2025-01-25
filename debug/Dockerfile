FROM otel/opentelemetry-collector-builder:0.117.0 AS builder

WORKDIR /build
RUN wget https://raw.githubusercontent.com/open-telemetry/opentelemetry-collector-releases/refs/tags/v0.118.0/distributions/otelcol-contrib/manifest.yaml
RUN ocb --config=./manifest.yaml

FROM ubuntu:24.04 AS final
WORKDIR /ocb
COPY --from=builder ["/build/_build/otelcol-contrib", "./ocb"]
ENTRYPOINT [ "./bin/bash" ]
EXPOSE 8080
