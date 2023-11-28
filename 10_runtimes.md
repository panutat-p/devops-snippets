# Runtimes

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
echo 'export PATH=$PATH:/usr/local/go/bin' >> ~/.bashrc
```

## Install Node.js

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
