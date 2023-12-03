# Runtimes

## Docker engine

https://docs.docker.com/engine/install/ubuntu

```shell
sudo -i
```

```shell
for pkg in docker.io docker-doc docker-compose docker-compose-v2 podman-docker containerd runc; do sudo apt remove $pkg; done
```

```shell
apt install ca-certificates curl gnupg
```

```shell
install -m 0755 -d /etc/apt/keyrings
```

```shell
curl -fsSL https://download.docker.com/linux/ubuntu/gpg | gpg --dearmor -o /etc/apt/keyrings/docker.gpg
```

```shell
chmod a+r /etc/apt/keyrings/docker.gpg
```

```shell
echo \
  "deb [arch=$(dpkg --print-architecture) signed-by=/etc/apt/keyrings/docker.gpg] https://download.docker.com/linux/ubuntu \
  $(. /etc/os-release && echo "$VERSION_CODENAME") stable" | \
  tee /etc/apt/sources.list.d/docker.list > /dev/null
```

```shell
apt update
```

```shell
apt install docker-ce docker-ce-cli containerd.io docker-buildx-plugin docker-compose-plugin
```

## Install Go

https://go.dev/doc/install

```shell
rm -rf /usr/local/go
```

```shell
wget -O go.tar.gz https://go.dev/dl/go1.21.4.linux-amd64.tar.gz
```

```shell
tar -C /usr/local -xvf go.tar.gz
```

```shell
export PATH=$PATH:/usr/local/go/bin
```

## Install Node.js

```shell
export PATH=$PATH:/usr/local/bin/node
export PATH=$PATH:/usr/local/bin/npm
```

## Install bun

## Install Python

## Install Java

## TaskFile

https://taskfile.dev/installation

```shell
sh -c "$(curl --location https://taskfile.dev/install.sh)" -- -d -b /usr/local/bin
```

https://taskfile.dev/installation/#setup-completions

```shell
wget -O .taskfile.bash https://raw.githubusercontent.com/go-task/task/main/completion/bash/task.bash
```
