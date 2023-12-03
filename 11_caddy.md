# Caddy

## Install

https://caddyserver.com/docs/install#debian-ubuntu-raspbian

## Image

https://hub.docker.com/_/caddy

```shell
mkdir ~/caddy && touch ~/caddy/Caddyfile
```

```shel
docker volume create caddy_config
```

`compose.yaml`
```yaml
version: "3.9"

services:
  caddy:
    image: caddy:2.7
    restart: unless-stopped
    cap_add:
      - NET_ADMIN
    ports:
      - "80:80"
      - "443:443"
      - "443:443/udp"
    volumes:
      - type: bind
        source: ~/caddy/Caddyfile
        target: /etc/caddy/Caddyfile
      - type: volume
        source: caddy_data
        target: /data
      - type: volume
        source: caddy_config
        target: /config

volumes:
  caddy_data:
    external: true
  caddy_config:
    external: false
```

## Config

https://caddyserver.com/docs/getting-started

https://caddyserver.com/docs/caddyfile

```
:80 {
    handle_path /api/* {
        rewrite * /hello{path}
        reverse_proxy http://kafka-ui.app.svc:8080
    }
}
```
