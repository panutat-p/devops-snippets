# Tools

## Basic

```shell
apt install -y lsb-release curl gpg
```

## Network

```shell
apt install -y net-tools
```

## JSON

```shell
apt install -y jq
```

## TaskFile

https://taskfile.dev/installation

```shell
sh -c "$(curl --location https://taskfile.dev/install.sh)" -- -d -b /usr/local/bin
```

https://taskfile.dev/installation/#setup-completions

```shell
wget -O .taskfile.bash https://raw.githubusercontent.com/go-task/task/main/completion/bash/task.bash
```

## Redis

https://redis.io/docs/install/install-redis/install-redis-on-linux

```shell
curl -fsSL https://packages.redis.io/gpg | gpg --dearmor -o /usr/share/keyrings/redis-archive-keyring.gpg
echo "deb [signed-by=/usr/share/keyrings/redis-archive-keyring.gpg] https://packages.redis.io/deb $(lsb_release -cs) main" | tee /etc/apt/sources.list.d/redis.list

apt update
apt install -y redis
```

```shell
apt install -y redis-tools
```

```shell
redis-cli -h localhost -p 6379
```

```shell
redis-cli -h localhost -p 6379 -a password
```
