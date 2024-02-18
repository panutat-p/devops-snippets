# Runtimes

## Docker engine

https://docs.docker.com/engine/install

```shell
for pkg in docker.io docker-doc docker-compose docker-compose-v2 podman-docker containerd runc; do apt remove $pkg; done
```

```shell
apt install ca-certificates curl gnupg
```

```shell
install -m 0755 -d /etc/apt/keyrings
```

```shell
curl -SL https://download.docker.com/linux/ubuntu/gpg | gpg --dearmor -o /etc/apt/keyrings/docker.gpg
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

## Caddy

https://caddyserver.com/docs/install

```shell
apt install -y debian-keyring debian-archive-keyring apt-transport-https
```

```shell
curl -1SL 'https://dl.cloudsmith.io/public/caddy/stable/gpg.key' | gpg --dearmor -o /usr/share/keyrings/caddy-stable-archive-keyring.gpg
```

```shell
curl -1SL 'https://dl.cloudsmith.io/public/caddy/stable/debian.deb.txt' | tee /etc/apt/sources.list.d/caddy-stable.list
```

```shell
apt update
```

```shell
apt install caddy
```

## Go

https://go.dev/doc/install

```shell
rm -rf /usr/local/go
```

```shell
wget -O go.tar.gz https://go.dev/dl/go1.22.0.linux-amd64.tar.gz
```

```shell
tar -C /usr/local -xvf go.tar.gz
```

```shell
export PATH=$PATH:/usr/local/go/bin
```

## Node.js

https://github.com/nodesource/distributions?tab=readme-ov-file#debian-and-ubuntu-based-distributions

```shell
apt update
apt install -y ca-certificates curl gnupg
mkdir -p /etc/apt/keyrings
curl -fsSL https://deb.nodesource.com/gpgkey/nodesource-repo.gpg.key | gpg --dearmor -o /etc/apt/keyrings/nodesource.gpg
```

```shell
NODE_MAJOR=21
echo "deb [signed-by=/etc/apt/keyrings/nodesource.gpg] https://deb.nodesource.com/node_$NODE_MAJOR.x nodistro main" | tee /etc/apt/sources.list.d/nodesource.list
```

```shell
apt update
apt install -y nodejs
```

```shell
npm i -g npm@latest
```

```shell
npm i -g prettier
```

```shell
npm i -g husky
```

```shell
npm i -g @commitlint/cli @commitlint/config-conventional
```

```shell
npm list -g --depth=0
```

Manually source PATH
```shell
export PATH=$PATH:/usr/local/bin/node
export PATH=$PATH:/usr/local/bin/npm
```

## bun

## Python

## Java
