# Runtimes

## Go

### Ubuntu

https://go.dev/doc/install

```sh
rm -rf /usr/local/go
wget -O go.tar.gz https://go.dev/dl/go1.24.1.linux-amd64.tar.gz
wget -O go.tar.gz https://go.dev/dl/go1.24.1.linux-arm64.tar.gz
tar -C /usr/local -xzf go.tar.gz
```

```sh
export PATH=$PATH:/usr/local/go/bin
```

### MacOS

```sh
brew install go
```

```sh
export PATH=$PATH:$HOME/go/bin
```

## Node.js

https://github.com/nodesource/distributions

Ubuntu
```sh
wget -O node23.sh https://deb.nodesource.com/setup_23.x
sudo -E bash node23.sh
sudo apt-get install -y nodejs
```

```sh
npm i -g npm@latest
npm i -g tsx
npm i -g prettier
```

```sh
npm i -g prettier
npm i -g husky
npm i -g @commitlint/cli @commitlint/config-conventional
```

```sh
npm list -g --depth=0
```

```sh
export PATH=$PATH:$(npm get prefix)/bin
```

## bun

Linux
```sh
curl -fsSL https://bun.sh/install | bash
```

MacOS
```sh
brew install oven-sh/bun/bun
```

```sh
bun upgrade
bun --version
```

## Java

Ubuntu
```sh
wget -O java21.deb https://corretto.aws/downloads/latest/amazon-corretto-21-x64-linux-jdk.deb
dpkg -i java21.deb
```

MacOS x64
```sh
wget -O java21.pkg https://corretto.aws/downloads/latest/amazon-corretto-21-x64-macos-jdk.pkg
open java21.pkg
```

MacOS ARM
```sh
wget -O java21.pkg https://corretto.aws/downloads/latest/amazon-corretto-21-aarch64-macos-jdk.pkg
open java21.pkg
```

## Python
