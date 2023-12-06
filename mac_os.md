# Mac OS

https://docs.docker.com/compose/install/linux/#install-the-plugin-manually

https://github.com/abiosoft/colima/discussions/273#discussioncomment-4959736

https://github.com/docker/compose/issues/8630#issuecomment-1169537632

## Colima

```shell
brew install colima
```

```shell
colima start --cpu-type qemu64 --cpu 4 --memory 8 --very-verbose
```

```shell
colima status
```

```shell
colima stop --force
```

```shell
colima delete
```

## Docker

```shell
brew install docker
```

```shell
brew install docker-buildx
```

```shell
brew install docker-compose
```

```shell
mkdir -p ~/.docker/cli-plugins
```

```shell
curl -SL \
  -o ~/.docker/cli-plugins/docker-compose \
  https://github.com/docker/compose/releases/download/v2.23.3/docker-compose-linux-x86_64
```

```shell
chmod +x ~/.docker/cli-plugins/docker-compose
```

```shell
ln -sfn /opt/homebrew/opt/docker-compose/bin/docker-compose ~/.docker/cli-plugins/docker-compose
```

```shell
docker version
```

```shell
docker buildx version
```

```shell
docker compose version
```
