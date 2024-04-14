# Tools

## TaskFile

https://taskfile.dev/installation

https://taskfile.dev/installation/#setup-completions

Ubuntu
```sh
sh -c "$(curl --location https://taskfile.dev/install.sh)" -- -d -b /usr/local/bin
wget -O /etc/task_completion.bash https://raw.githubusercontent.com/go-task/task/main/completion/bash/task.bash
echo 'source /etc/task_completion.bash' >> ~/.bashrc
```

MacOS
```sh
brew install go-task
wget -O /usr/local/share/zsh/site-functions/_task https://raw.githubusercontent.com/go-task/task/main/completion/zsh/_task
```

## GitHub CLI

https://docs.github.com/en/copilot/github-copilot-in-the-cli/using-github-copilot-in-the-cli

Ububtu
```sh
mkdir -p -m 755 /etc/apt/keyrings && wget -qO- https://cli.github.com/packages/githubcli-archive-keyring.gpg | tee /etc/apt/keyrings/githubcli-archive-keyring.gpg > /dev/null
chmod go+r /etc/apt/keyrings/githubcli-archive-keyring.gpg
echo "deb [arch=$(dpkg --print-architecture) signed-by=/etc/apt/keyrings/githubcli-archive-keyring.gpg] https://cli.github.com/packages stable main" | tee /etc/apt/sources.list.d/github-cli.list > /dev/null
apt update
apt install gh -y
```

MacOS
```sh
brew install gh
```

```sh
gh auth login --web -h github.com
```

```sh
gh extension install github/gh-copilot
gh extension upgrade gh-copilot
```

```sh
echo 'eval "$(gh copilot alias -- zsh)"' >> ~/.zshrc
```

```sh
ghce 'go programming'
```

```sh
ghcs 'list running port numbers in MacOS'
```

```sh
ghcs -t git 'delete files/dirs that are not tracked'
```

```sh
ghcs -t git 'discard all local changes'
```

```sh
ghcs -t git 'discard all local changes'
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
