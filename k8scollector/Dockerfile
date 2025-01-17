FROM otel/opentelemetry-collector-builder:0.117.0 AS build

WORKDIR /builder
RUN mkdir /builder/build
RUN mkdir /builder/build/otelcol-dev
COPY ["./otelcol-builder.yaml", "/builder/"]
RUN ocb --config=/builder/otelcol-builder.yaml

FROM alpine AS final

COPY --from=build ["/builder/build/", "/app/"]
# RUN chmod +x /app/otelcol-dev

ENTRYPOINT [ "/app/otelcol-dev/otelcol-custom" ]