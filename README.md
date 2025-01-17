# OTEL Collector Images

A collection of otel collector images to be used for processing telemetry.

## Creating the registry

```shell
scw registry namespace create name=otel-collector-images
```

## Set the SCW secret to push images from github workflows

```shell
gh secret set \
    SCW_SECRET_KEY \
    --repo "github.com/IrrelevantElephant/otel-collector-images" \
    --app actions \
    --body $SCW_SECRET_KEY
```

## Build and push
```shell
docker build -f rabbitexporter/Dockerfile -t rg.fr-par.scw.cloud/otel-collector/rabbitexporter:latest ./rabbitexporter/
docker push rg.fr-par.scw.cloud/otel-collector/rabbitexporter:latest
```