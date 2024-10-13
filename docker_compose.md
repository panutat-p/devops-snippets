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
    image: ubuntu:noble
    command: tail -f /dev/null
    restart: on-failure

  debian:
    image: debian:bookworm
    command: tail -f /dev/null
    restart: on-failure

  alpine:
    image: alpine:3
    command: tail -f /dev/null
    restart: on-failure

  busybox:
    image: busybox:1.37
    command: tail -f /dev/null
    restart: on-failure
```
