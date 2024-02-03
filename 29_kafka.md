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
    restart: unless-stopped
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
    restart: unless-stopped
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
