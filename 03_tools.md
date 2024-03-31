# Tools

## Basic

```sh
apt update
apt upgrade -y
```

```sh
apt install -y bash-completion lsb-release gpg gnupg apt-transport-https ca-certificates
```

```sh
apt install -y jq yq bzip2 alien curl wget git
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

## GitHub CLI

https://docs.github.com/en/copilot/github-copilot-in-the-cli/using-github-copilot-in-the-cli

```sh
mkdir -p -m 755 /etc/apt/keyrings && wget -qO- https://cli.github.com/packages/githubcli-archive-keyring.gpg | tee /etc/apt/keyrings/githubcli-archive-keyring.gpg > /dev/null \
&& chmod go+r /etc/apt/keyrings/githubcli-archive-keyring.gpg \
&& echo "deb [arch=$(dpkg --print-architecture) signed-by=/etc/apt/keyrings/githubcli-archive-keyring.gpg] https://cli.github.com/packages stable main" | tee /etc/apt/sources.list.d/github-cli.list > /dev/null \
&& apt update \
&& apt install gh -y
```

```sh
apt update
apt install gh
```

```sh
gh auth login --web -h github.com
```

```sh
gh extension install github/gh-copilot
gh extension upgrade gh-copilot
```

```sh
gh copilot explain 'go programming'
```
