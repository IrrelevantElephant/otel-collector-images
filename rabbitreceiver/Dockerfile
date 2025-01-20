FROM otel/opentelemetry-collector-builder:0.117.0 AS builder

WORKDIR /build
COPY ["./builder-config.yaml", "."]
RUN ocb --config=./builder-config.yaml

FROM alpine:3.21.2 AS final
RUN adduser -D nonrootuser
USER nonrootuser
WORKDIR /ocb
COPY --from=builder ["/tmp/dist/otelcol-custom", "./ocb"]
ENTRYPOINT [ "./ocb" ]
EXPOSE 8080