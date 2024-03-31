# gcloud

## Install

https://cloud.google.com/sdk/docs/install#mac

Ubuntu
```sh
apt update
apt install -y apt-transport-https ca-certificates gnupg curl
curl https://packages.cloud.google.com/apt/doc/apt-key.gpg | gpg --dearmor -o /usr/share/keyrings/cloud.google.gpg
echo "deb [signed-by=/usr/share/keyrings/cloud.google.gpg] https://packages.cloud.google.com/apt cloud-sdk main" |  tee -a /etc/apt/sources.list.d/google-cloud-sdk.list
apt update
apt install -y google-cloud-cli
```

MacOS Intel
```sh
wget -O gcloud.tar.gz https://dl.google.com/dl/cloudsdk/channels/rapid/downloads/google-cloud-cli-470.0.0-darwin-x86_64.tar.gz
```

MacOS ARM
```sh
wget -O gcloud.tar.gz https://dl.google.com/dl/cloudsdk/channels/rapid/downloads/google-cloud-cli-470.0.0-darwin-arm.tar.gz
```

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

## IAM

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
gke-gcloud-auth-plugin --version
```

```sh
gcloud container clusters get-credentials gke_cluster_name --region asia-southeast1-a --project project_name
```

```sh
kubectl config get-contexts
```

```sh
kubectl config use-context gke_cluster_name
```
