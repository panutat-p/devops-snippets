# Mac OS

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

## Docker plugins

https://github.com/abiosoft/colima/discussions/273#discussioncomment-4959736

```shell
mkdir -p ~/.docker/cli-plugins
```

```shell
brew install docker-buildx
```

```shell
ln -sfn /opt/homebrew/opt/docker-buildx/bin/docker-buildx ~/.docker/cli-plugins/docker-buildx
```

https://github.com/docker/compose/issues/8630#issuecomment-1169537632

```shell
brew install docker-compose
```

```shell
ln -sfn /opt/homebrew/opt/docker-compose/bin/docker-compose ~/.docker/cli-plugins/docker-compose
```
