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

### Upload

```sh
kubectl cp $HOME/script default/ubuntu:/root/script
```

## Download

```sh
kubectl cp default/ubuntu:/root/script $HOME/script
```

## Port forwarding

```sh

```

## Proxy

```sh
kubectl proxy --port 4000
```

```sh
curl http://localhost:4000/api/v1/nodes
```

```sh
curl http://localhost:4000/apis/apps/v1/namespaces/default/deployments
```

```sh
curl http://localhost:4000/api/v1/namespaces/default/pods
```

```sh
curl http://localhost:4000/apis/networking.k8s.io/v1/namespaces/default/ingresses
```

