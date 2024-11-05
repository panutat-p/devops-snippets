# Docker Compose

https://docs.docker.com/compose/intro/compose-application-model

## OS

https://hub.docker.com/_/ubuntu

https://hub.docker.com/_/debian

https://hub.docker.com/_/alpine

https://hub.docker.com/_/busybox

```yaml
services:
  ubuntu:
    container_name: ubuntu
    image: ubuntu:noble
    command: tail -f /dev/null
    restart: on-failure

  debian:
    container_name: debian
    image: debian:bookworm
    command: tail -f /dev/null
    restart: on-failure

  alpine:
    container_name: alpine
    image: alpine:3
    command: tail -f /dev/null
    restart: on-failure

  busybox:
    container_name: busybox
    image: busybox:1.37
    command: tail -f /dev/null
    restart: on-failure
```

## Database

https://hub.docker.com/_/mysql

https://hub.docker.com/_/redis

https://redis.io/docs/latest/operate/oss_and_stack/management/config-file

`redis.conf`
```
# Snapshotting
# Dump the dataset to disk every 30s if at least 100 keys changed.
save 30 100

# Append-only file
appendonly yes
```

```yaml
services:

  mysql8:
    container_name: mysql8
    image: mysql:8.4
    environment:
      MYSQL_ROOT_PASSWORD: 1234
    ports:
      - '3306:3306'
    volumes:
      - type: volume
        source: mysql8_data
        target: /var/lib/mysql
    restart: on-failure

  redis7:
    container_name: redis7
    image: redis:7.4
    ports:
      - '6379:6379'
    volumes:
      - type: volume
        source: redis7_data
        target: /var/lib/mysql
      - type: bind
        source: redis.conf
        target: /usr/local/etc/redis.conf
    command: ["redis-server", "/usr/local/etc/redis/redis.conf"]
    restart: on-failure

volumes:
  mysql8_data:
    driver: local
    external: true
  redis7_data:
    driver: local
    external: true
```
