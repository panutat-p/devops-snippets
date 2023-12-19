# Elasticsearch

https://hub.docker.com/r/elastic/elasticsearch

## Docker Compose

https://www.elastic.co/guide/en/elasticsearch/reference/current/docker.html

https://github.com/elastic/elasticsearch/blob/8.11/docs/reference/setup/install/docker/docker-compose.yml

```yaml
version: '3.9'

services:
  elasticsearch:
    image: 'elastic/elasticsearch:8.11.3'
    environment:
      xpack.security.enabled: false
      xpack.security.http.ssl.enabled: false
      xpack.security.transport.ssl.enabled: false
      ELASTIC_USERNAME: admin
      ELASTIC_PASSWORD: 1234
    ports:
      - '9200:9200'
    restart: always
```
