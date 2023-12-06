# Mac OS

https://docs.docker.com/compose/install/linux/#install-the-plugin-manually

https://github.com/docker/compose/issues/8630#issuecomment-1169537632


## Docker

```shell
brew install colima
```

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
curl \
  -SL https://github.com/docker/compose/releases/download/v2.23.3/docker-compose-linux-x86_64 \
  -o ~/.docker/cli-plugins/docker-compose
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
