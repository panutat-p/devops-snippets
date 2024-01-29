# `kubectl`

## Ubuntu

```shell
kubectl run ubuntu --image ubuntu:22.04 --command -- sleep infinity
```

```shell
kubectl exec -it pod/ubuntu -- /bin/bash
```

## Curl

```shell
kubectl run curl --image curlimages/curl:latest --command -- sleep infinity
```

```shell
kubectl exec pod/curl -- curl https://example.com
```
