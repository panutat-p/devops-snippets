# Runtimes

## Docker engine

https://docs.docker.com/engine/install

```sh
for pkg in docker.io docker-doc docker-compose docker-compose-v2 podman-docker containerd runc; do apt remove $pkg; done
```

```sh
apt install ca-certificates curl gnupg
```

```sh
install -m 0755 -d /etc/apt/keyrings
```

```sh
curl -SL https://download.docker.com/linux/ubuntu/gpg | gpg --dearmor -o /etc/apt/keyrings/docker.gpg
```

```sh
chmod a+r /etc/apt/keyrings/docker.gpg
```

```sh
echo \
  "deb [arch=$(dpkg --print-architecture) signed-by=/etc/apt/keyrings/docker.gpg] https://download.docker.com/linux/ubuntu \
  $(. /etc/os-release && echo "$VERSION_CODENAME") stable" | \
  tee /etc/apt/sources.list.d/docker.list > /dev/null
```

```sh
apt update
```

```sh
apt install docker-ce docker-ce-cli containerd.io docker-buildx-plugin docker-compose-plugin
```

## Caddy

https://caddyserver.com/docs/install

```sh
apt install -y debian-keyring debian-archive-keyring apt-transport-https
```

```sh
curl -1SL 'https://dl.cloudsmith.io/public/caddy/stable/gpg.key' | gpg --dearmor -o /usr/share/keyrings/caddy-stable-archive-keyring.gpg
```

```sh
curl -1SL 'https://dl.cloudsmith.io/public/caddy/stable/debian.deb.txt' | tee /etc/apt/sources.list.d/caddy-stable.list
```

```sh
apt update
```

```sh
apt install caddy
```

## Go

https://go.dev/doc/install

```sh
rm -rf /usr/local/go
```

```sh
wget -O go.tar.gz https://go.dev/dl/go1.22.2.linux-amd64.tar.gz
```

```sh
tar -C /usr/local -xvf go.tar.gz
```

```sh
export PATH=$PATH:/usr/local/go/bin
```

## Node.js

https://github.com/nodesource/distributions?tab=readme-ov-file#debian-and-ubuntu-based-distributions

```sh
apt update
apt install -y ca-certificates curl gnupg
mkdir -p /etc/apt/keyrings
curl -fsSL https://deb.nodesource.com/gpgkey/nodesource-repo.gpg.key | gpg --dearmor -o /etc/apt/keyrings/nodesource.gpg
```

```sh
NODE_MAJOR=21
echo "deb [signed-by=/etc/apt/keyrings/nodesource.gpg] https://deb.nodesource.com/node_$NODE_MAJOR.x nodistro main" | tee /etc/apt/sources.list.d/nodesource.list
```

```sh
apt update
apt install -y nodejs
```

```sh
npm i -g npm@latest
```

```sh
npm i -g prettier
```

```sh
npm i -g husky
```

```sh
npm i -g @commitlint/cli @commitlint/config-conventional
```

```sh
npm list -g --depth=0
```

Manually source PATH
```sh
export PATH=$PATH:/usr/local/bin/node
export PATH=$PATH:/usr/local/bin/npm
```

## bun

## Python

## Java
