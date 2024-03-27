# gcloud

## MacOS

https://cloud.google.com/sdk/docs/install#mac

Intel
```sh
wget -O gcloud.tar.gz https://dl.google.com/dl/cloudsdk/channels/rapid/downloads/google-cloud-cli-470.0.0-darwin-x86_64.tar.gz
```

ARM
```sh
wget -O gcloud.tar.gz https://dl.google.com/dl/cloudsdk/channels/rapid/downloads/google-cloud-cli-470.0.0-darwin-arm.tar.gz
```

---

```sh
tar -C $HOME -xvf gcloud.tar.gz
```

```sh
./$HOME/google-cloud-sdk/install.sh
```

```sh
gcloud init
```

```sh
export CLOUDSDK_PYTHON=python3.11
```

## Identity and Access Management (IAM)

https://cloud.google.com/docs/authentication/gcloud

```sh
gcloud auth login
```

```sh
gcloud auth list
```

```sh
gcloud auth application-default login
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
