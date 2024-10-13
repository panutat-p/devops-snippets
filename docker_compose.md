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
