# helm-demo

helm demo for chartmuseum test

## helm create && push

* start chartmuseum

```bash

chartmuseum --debug --port=8089 \
  --storage="local" \
  --storage-local-rootdir="./chartstorage"

```

* helm add repo chartmuseum

```bash

helm repo add chartmuseum http://localhost:8089

```

* push repo

```bash

helm push gateway/ chartmuseum

```

* install

```bash

helm  install chartmuseum/gateway

```

## minio demo

* config minio s3

```bash
mkdir -p ~/.aws

touch credentials

[default]
aws_access_key_id = 7V9OLKA3W322WMJIE09R
aws_secret_access_key = gvNkB10T1xcINQsBmsX1CbGjmfuQ5vv/L4Vo8o6H

`note`: this is my local config you must change it with you server info

```

* start chartmuseum with  minio s3

```bash

chartmuseum --debug --port=8089 \
  --storage="amazon" \
  --storage-amazon-bucket="helm" \
  --storage-amazon-prefix="" \
  --storage-amazon-region="eu-west-1" \
  --storage-amazon-endpoint="http://127.0.0.1:9091"

```

* publish registry

```bash

helm repo add chartmuseum http://localhost:8089
helm push gateway/ chartmuseum

```