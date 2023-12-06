# Caddy

https://hub.docker.com/_/caddy

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

## Reverse proxy for Kafka UI

`Caddyfile`
```
http://localhost:80 {
  reverse_proxy http://kafka-ui:8080
}
```

```shel
docker volume create caddy_data
```

```yaml
version: '3.9'

services:
  kafka0:
    hostname: kafka0
    container_name: kafka0
    image: 'bitnami/kafka:3.6'
    environment:
      KAFKA_ENABLE_KRAFT: yes
      KAFKA_CFG_NODE_ID: 0
      KAFKA_CFG_PROCESS_ROLES: controller,broker
      KAFKA_CFG_ADVERTISED_LISTENERS: PLAINTEXT://kafka0:9092
      KAFKA_CFG_LISTENERS: CONTROLLER://kafka0:9093,PLAINTEXT://kafka0:9092
      KAFKA_CFG_LISTENER_SECURITY_PROTOCOL_MAP: CONTROLLER:PLAINTEXT,PLAINTEXT:PLAINTEXT
      KAFKA_CFG_CONTROLLER_QUORUM_VOTERS: 0@kafka0:9093
      KAFKA_CFG_CONTROLLER_LISTENER_NAMES: CONTROLLER
    restart: always
  kafka-ui:
    hostname: kafka-ui
    container_name: kafka-ui
    depends_on:
      - kafka0
    image: 'provectuslabs/kafka-ui:latest'
    environment:
      DYNAMIC_CONFIG_ENABLED: 'true'
      KAFKA_CLUSTERS_0_NAME: local
      KAFKA_CLUSTERS_0_BOOTSTRAPSERVERS: kafka0:9092
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
