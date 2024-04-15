# Docker

https://stackoverflow.com/a/72784095

If you had recently deleted Docker, you have to manually recreate the Docker folder
```sh
mkdir -p /Applications/Docker.app/Contents/Resources/cli-plugins
brew cleanup
```

## Colima

```sh
brew install colima
```

List available CPUs
```sh
qemu-system-aarch64 -cpu help
```

```sh
colima start --cpu 4 --memory 8 --network-address --very-verbose
```

```sh
colima status --very-verbose
```

```sh
colima stop --force
```

```sh
colima delete
```

## Docker

```sh
brew install docker
```

## Docker plugins

https://github.com/abiosoft/colima/discussions/273#discussioncomment-4959736

```sh
mkdir -p ~/.docker/cli-plugins
```

```sh
brew install docker-buildx
```

```sh
ln -sfn /opt/homebrew/opt/docker-buildx/bin/docker-buildx ~/.docker/cli-plugins/docker-buildx
```

https://github.com/docker/compose/issues/8630#issuecomment-1169537632

```sh
brew install docker-compose
```

```sh
ln -sfn /opt/homebrew/opt/docker-compose/bin/docker-compose ~/.docker/cli-plugins/docker-compose
```

## Lazy Docker

https://github.com/jesseduffield/lazydocker

```sh
brew install lazydocker
```

## Docker engine for Linux

https://docs.docker.com/engine/install

```sh
for pkg in docker.io docker-doc docker-compose docker-compose-v2 podman-docker containerd runc; do apt remove $pkg; done
```

```sh
apt install ca-certificates curl gnupg
```

```sh
install -m 0755 -d /etc/apt/keyrings
```

```sh
curl -SL https://download.docker.com/linux/ubuntu/gpg | gpg --dearmor -o /etc/apt/keyrings/docker.gpg
```

```sh
chmod a+r /etc/apt/keyrings/docker.gpg
```

```sh
echo \
  "deb [arch=$(dpkg --print-architecture) signed-by=/etc/apt/keyrings/docker.gpg] https://download.docker.com/linux/ubuntu \
  $(. /etc/os-release && echo "$VERSION_CODENAME") stable" | \
  tee /etc/apt/sources.list.d/docker.list > /dev/null
```

```sh
apt update
```

```sh
apt install docker-ce docker-ce-cli containerd.io docker-buildx-plugin docker-compose-plugin
```

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
