# Tools

## Basic

```sh
apt update
apt upgrade -y
```

```sh
apt install -y bash-completion lsb-release gpg alien curl wget git
```

## Utilities

```sh
apt install -y jq yq
```

## TaskFile

https://taskfile.dev/installation

```sh
sh -c "$(curl --location https://taskfile.dev/install.sh)" -- -d -b /usr/local/bin
```

https://taskfile.dev/installation/#setup-completions

```sh
wget -O /etc/task_completion.bash https://raw.githubusercontent.com/go-task/task/main/completion/bash/task.bash
```

```sh
source /etc/task_completion.bash
```

## Redis

https://redis.io/docs/install/install-redis/install-redis-on-linux

```sh
curl -fsSL https://packages.redis.io/gpg | gpg --dearmor -o /usr/share/keyrings/redis-archive-keyring.gpg
echo "deb [signed-by=/usr/share/keyrings/redis-archive-keyring.gpg] https://packages.redis.io/deb $(lsb_release -cs) main" | tee /etc/apt/sources.list.d/redis.list
apt update
apt install -y redis
```

https://docs.redis.com/latest/rs/references/cli-utilities/redis-cli

```sh
redis-cli -h localhost -p 6379
```

```sh
redis-cli -h localhost -p 6379 -a password -n 0
```
