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