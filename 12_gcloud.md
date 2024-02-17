# gcloud

## MacOS

https://cloud.google.com/sdk/docs/install#mac

```sh
wget -O gcloud.tar.gz https://dl.google.com/dl/cloudsdk/channels/rapid/downloads/google-cloud-cli-464.0.0-darwin-arm.tar.gz
```

```sh
tar -C $HOME -xvf gcloud.tar.gz
```

```sh
$HOME/gcloud.tar.gz
```

## Auth

```shell
gcloud auth login
```

```shell
gcloud auth list
```

## GKE

https://cloud.google.com/kubernetes-engine/docs/how-to/cluster-access-for-kubectl

```shell
gcloud components install gke-gcloud-auth-plugin
```

```shell
gcloud container clusters get-credentials gke-cluster-name --region asia-southeast1 --project project-name
```

```shell
kubectl config get-contexts
```

```shell
kubectl config use-context gke-cluster-name
```
