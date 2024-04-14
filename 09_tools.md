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
