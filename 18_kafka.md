# Kafka Image

https://github.com/provectus/kafka-ui/blob/master/documentation/compose/DOCKER_COMPOSE.md

## Expose only Kafka UI

`compose.yaml`
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
    depends_on:
      - kafka0
    container_name: kafka-ui
    image: 'provectuslabs/kafka-ui:latest'
    ports:
      - "8080:8080"
    environment:
      DYNAMIC_CONFIG_ENABLED: 'true'
      KAFKA_CLUSTERS_0_NAME: local
      KAFKA_CLUSTERS_0_BOOTSTRAPSERVERS: kafka0:9092
```

## Expose both Kafka UI and Kafka broker

`compose.yaml`
```yaml
version: '3.9'

services:
  kafka0:
    hostname: kafka0
    container_name: kafka0
    image: 'bitnami/kafka:3.6'
    ports:
      - '9092:9092'
    environment:
      KAFKA_ENABLE_KRAFT: yes
      KAFKA_CFG_NODE_ID: 0
      KAFKA_CFG_PROCESS_ROLES: controller,broker
      KAFKA_CFG_LISTENER_SECURITY_PROTOCOL_MAP: CONTROLLER:PLAINTEXT,INTERNAL:PLAINTEXT,EXTERNAL:PLAINTEXT
      KAFKA_CFG_ADVERTISED_LISTENERS: INTERNAL://kafka0:29092,EXTERNAL://localhost:9092
      KAFKA_CFG_LISTENERS: CONTROLLER://kafka0:29093,INTERNAL://kafka0:29092,EXTERNAL://0.0.0.0:9092
      KAFKA_CFG_CONTROLLER_QUORUM_VOTERS: 0@kafka0:29093
      KAFKA_CFG_CONTROLLER_LISTENER_NAMES: CONTROLLER
      KAFKA_CFG_INTER_BROKER_LISTENER_NAME: INTERNAL
    restart: always
  kafka-ui:
    depends_on:
      - kafka0
    container_name: kafka-ui
    image: 'provectuslabs/kafka-ui:latest'
    ports:
      - "8080:8080"
    environment:
      DYNAMIC_CONFIG_ENABLED: 'true'
      KAFKA_CLUSTERS_0_NAME: local
      KAFKA_CLUSTERS_0_BOOTSTRAPSERVERS: kafka0:29092
```

## Expose only Kafka UI via Spring config

`kafka-ui.yaml`
```yaml
server:
  port: 80
  servlet:
    contextPath: /ui

kafka:
  clusters:
    - name: local
      bootstrapServers: kafka0:9092
```

`compose.yaml`
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
    ports:
      - '80:80'
      - '8080:8080'
    environment:
      SPRING_CONFIG_ADDITIONAL-LOCATION: /etc/kafkaui/config.yaml
    volumes:
      - type: bind
        source: $PWD/kafka-ui.yaml
        target: /etc/kafkaui/config.yaml
```

## Expose only Kafka UI via Spring config with auth SASL_SCRAM

https://docs.kafka-ui.provectus.io/configuration/authentication/sasl_scram

`kafka-ui.yaml`
```yaml
server:
  port: 80
  servlet:
    contextPath: /ui

kafka:
  clusters:
    - name: local
      bootstrapServers: kafka0:9092
      properties:
        security.protocol: SASL_SSL
        sasl.mechanism: SCRAM-SHA-512        
        sasl.jaas.config: org.apache.kafka.common.security.scram.ScramLoginModule required username="<KAFKA_USERNAME>" password="<KAFKA_PASSWORD>";
```

`compose.yaml`
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
    ports:
      - '80:80'
      - '8080:8080'
    environment:
      SPRING_CONFIG_ADDITIONAL-LOCATION: /etc/kafkaui/config.yaml
    volumes:
      - type: bind
        source: $PWD/kafka-ui.yaml
        target: /etc/kafkaui/config.yaml
```

## Expose only Caddy

`Caddyfile`
```
http://localhost:80 {
  reverse_proxy http://kafka-ui:8080
}
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
