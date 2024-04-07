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

Remove all images
```sh
docker image prune -a -f
```

Remove all volumes
```sh
docker volume prune -a -f
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
docker run --rm -v ssh_key_data:/data -v ~/.ssh/id_ed25519:/tmp/id_ed25519 alpine:3 cp /tmp/id_ed25519 /data
```

```sh
docker run -it --rm -v ssh_key_data:/data alpine:3 sh
```
