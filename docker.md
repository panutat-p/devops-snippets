# Docker

## Commands

```sh
docker container ls -a
```

```sh
docker image ls
```

Remove stopped containers
```sh
docker container prune -f
```

Remove all containers
```sh
docker rm -f $(docker ps -aq)
```

Remove unused images
```sh
docker image prune -f
```

Remove unused volumes
```sh
docker volume prune -f
```

Remove unused images, unused containers, unused volumes, unused networks, and caches
```sh
docker system prune -a -f --volumes
```

## Create a docker volume with a file

```sh
docker volume create ssh_key_data
```

```sh
docker run --rm -v ssh_key_data:/tmp -v ~/.ssh/id_ed25519:/tmp/id_ed25519 scratch
```

```sh
docker run --rm -v ssh_key_data:/tmp -v ~/.ssh/id_ed25519:/tmp/id_ed25519 busybox:stable
```
