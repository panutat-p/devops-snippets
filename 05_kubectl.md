# `kubectl`

## Ubuntu

```sh
kubectl run ubuntu --image ubuntu:22.04 --command -- sleep infinity
```

```sh
kubectl exec -it pod/ubuntu -- /bin/bash
```

## Curl

```sh
kubectl run curl --image curlimages/curl:latest --command -- sleep infinity
```

```sh
kubectl exec pod/curl -- curl https://example.com
```

## Files

```sh

```

```sh

```
