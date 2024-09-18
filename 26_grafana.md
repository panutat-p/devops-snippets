# Grafana

https://hub.docker.com/r/grafana/grafana

https://hub.docker.com/_/influxdb

https://hub.docker.com/r/prom/prometheus

https://hub.docker.com/r/prom/pushgateway

## Grafana

```yaml
services:

  grafana:
    image: grafana/grafana:11.2.0
    ports:
      - '3000:3000'
    environment:
      GF_SECURITY_ADMIN_USER: 'admin'
      GF_SECURITY_ADMIN_PASSWORD: '12345678'
      GF_LOG_LEVEL: 'info'
      GF_INSTALL_PLUGINS: 'grafana-clock-panel,grafana-simple-json-datasource'
    volumes:
      - type: volume
        source: grafana_data
        target: /var/lib/grafana
    restart: unless-stopped

  influxdb:
    image: influxdb:2.7
    ports:
      - '8086:8086'
    environment:
      DOCKER_INFLUXDB_INIT_MODE: 'setup'
      DOCKER_INFLUXDB_INIT_USERNAME: 'admin'
      DOCKER_INFLUXDB_INIT_PASSWORD: '12345678'
      DOCKER_INFLUXDB_INIT_ORG: 'demo'
      DOCKER_INFLUXDB_INIT_BUCKET: 'fruit'
    volumes:
      - type: volume
        source: influxdb_data
        target: /var/lib/influxdb2
      - type: volume
        source: influxdb_data
        target: /etc/influxdb2
    restart: unless-stopped


volumes:
  grafana_data:
    external: true
  influxdb_data:
    external: true
```
