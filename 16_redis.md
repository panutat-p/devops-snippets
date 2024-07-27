# Redis

## Redis CLI

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
