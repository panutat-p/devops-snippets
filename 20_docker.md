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
