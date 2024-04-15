# Runtimes

## Go

https://go.dev/doc/install

```sh
rm -rf /usr/local/go
wget -O go.tar.gz https://go.dev/dl/go1.22.2.linux-amd64.tar.gz
tar -C /usr/local -xvf go.tar.gz
```

Ubuntu
```sh
export PATH=$PATH:/usr/local/go/bin
```

MacOS
```sh
export PATH=$PATH:$HOME/go/bin
```

## Node.js

https://github.com/nodesource/distributions

Ubuntu script
```sh
wget -O node21.sh https://deb.nodesource.com/setup_21.x
chmod +x node21.sh
./node21.sh
apt install -y nodejs
```

Ubuntu manual
```sh
apt update
apt install -y ca-certificates curl gnupg
mkdir -p /etc/apt/keyrings
curl -fsSL https://deb.nodesource.com/gpgkey/nodesource-repo.gpg.key | gpg --dearmor -o /etc/apt/keyrings/nodesource.gpg
NODE_MAJOR=21
echo "deb [signed-by=/etc/apt/keyrings/nodesource.gpg] https://deb.nodesource.com/node_$NODE_MAJOR.x nodistro main" | tee /etc/apt/sources.list.d/nodesource.list
apt update
apt install -y nodejs
```

```sh
npm i -g npm@latest
npm i -g typescript
npm i -g tsx
npm i -g ts-node
npm i -g vite-node
```

```sh
npm i -g prettier
npm i -g husky
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

## Java

Ubuntu
```sh
wget -O java21.deb 'https://corretto.aws/downloads/latest/amazon-corretto-21-x64-linux-jdk.deb'
dpkg -i java21.deb
```

MacOS ARM
```sh
wget -O java21.pkg 'https://corretto.aws/downloads/latest/amazon-corretto-21-aarch64-macos-jdk.pkg'
open java21.pkg
```

## bun

## Python
