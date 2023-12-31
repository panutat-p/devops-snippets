# Redis

https://hub.docker.com/_/redis

https://redis.io/docs/management/persistence

```shell
docker volume create redis_data
```

## Enable only RDB

`compose.yaml`
```yaml
version: '3.9'

services:
  redis:
    image: redis:7
    ports:
      - '6379:6379'
    volumes:
      - type: volume
        source: redis_data
        target: /data
    restart: unless-stopped

volumes:
  redis_data:
    external: true
```

## Enable both RDB and AOF

`redis.conf`
```
# RDB snapshotting
save 900 1
save 300 5
save 60 1000

# AOF persistence
appendonly yes
```

`compose.yaml`
```yaml
version: '3.9'

services:
  redis:
    image: redis:7
    command: redis-server /usr/local/etc/redis/redis.conf
    ports:
      - '6379:6379'
    volumes:
      - type: volume
        source: redis_data
        target: /data
      - type: bind
        source: redis.conf
        target: /usr/local/etc/redis/redis.conf
    restart: unless-stopped

volumes:
  redis_data:
    external: true
```
