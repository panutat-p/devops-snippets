# Caddy

## Install

https://caddyserver.com/docs/install#debian-ubuntu-raspbian

## Config

https://caddyserver.com/docs/getting-started

https://caddyserver.com/docs/caddyfile

`Caddyfile`
```
http://localhost:80

respond "Hello, world!"
```

`Caddyfile`
```
http://localhost:80 {
  reverse_proxy http://localhost:4000
}
```

`Caddyfile`
```
http://localhost:80

file_server browse

handle / {
  header Content-Type application/json
  respond `{"message": "Caddy is running"}` 200
}

handle_path /web {
  rewrite * /index
  reverse_proxy http://localhost:4000
}

handle_path /web/* {
  rewrite * /index{path}
  reverse_proxy http://localhost:4000
}
```

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
        source: $PWD/Caddyfile
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
