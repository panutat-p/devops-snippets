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

```sh
gcloud init
```

## Identity and Access Management (IAM)

https://cloud.google.com/sdk/gcloud/reference/auth/login

```sh
gcloud auth login
```

```sh
gcloud auth list
```

## GKE

https://cloud.google.com/kubernetes-engine/docs/how-to/cluster-access-for-kubectl

```sh
gcloud components install gke-gcloud-auth-plugin
```

```sh
gcloud container clusters get-credentials gke_cluster_name --region region_name --project project_name
```

```sh
kubectl config get-contexts
```

```sh
kubectl config use-context gke_cluster_name
```
