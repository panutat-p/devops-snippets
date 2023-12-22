# Elasticsearch

https://www.docker.elastic.co/r/elasticsearch

https://www.docker.elastic.co/r/kibana

## Docker Compose

https://www.elastic.co/guide/en/elasticsearch/reference/current/docker.html

https://github.com/elastic/elasticsearch/blob/8.11/docs/reference/setup/install/docker/docker-compose.yml

```yaml
version: '3.9'

services:
  elasticsearch:
#    image: 'docker.elastic.co/elasticsearch/elasticsearch:7.17.16'
    image: 'docker.elastic.co/elasticsearch/elasticsearch:8.11.3'
    environment:
      - discovery.type=single-node
      - xpack.security.enabled=false
      - xpack.security.transport.ssl.enabled=false
      - ELASTIC_USERNAME=admin
      - ELASTIC_PASSWORD="1234"
    ports:
      - '9200:9200'
    restart: unless-stopped
  kibana:
    depends_on:
      - elasticsearch
#    image: 'docker.elastic.co/kibana/kibana:7.17.16'
    image: 'docker.elastic.co/kibana/kibana:8.11.3'
    ports:
      - '5601:5601'
    environment:
      - ELASTICSEARCH_HOSTS=http://elasticsearch:9200
      - ELASTICSEARCH_USERNAME=admin
      - ELASTICSEARCH_PASSWORD="1234"
    restart: unless-stopped
```

## Kibana UI

```shell
GET /
```

```shell
GET /_cat/indices
```

```shell
PUT /fruit
{
  "mappings": {
    "properties": {
      "name": {
        "type": "text"
      },
      "price": {
        "type": "integer"
      }
    }
  }
}
```

```shell
PUT /fruit/_mapping
{
  "properties": {
    "tag": {
      "type": "keyword"
    }
  }
}
```

```shell
POST /fruit/_doc
{
  "name": "pineapple",
  "price": 25
}
```

```shell
POST /fruit/_bulk
{ "index" : { "_id" : "1" } }
{ "name" : "apple", "price" : 10 }
{ "index" : { "_id" : "2" } }
{ "name" : "banana", "price" : 10 }
{ "index" : { "_id" : "3" } }
{ "name" : "carrot", "price" : 6 }
{ "index" : { "_id" : "4" } }
{ "name" : "durian", "price" : 100 }
```

```shell
POST /fruit/_bulk
  { "update" : {"_id" : 1 }}
  { "doc" : {"price" : 15}}
  { "update" : {"_id" : 2 }}
  { "doc" : {"price" : 8}}
```

```shell
GET /fruit/_count
```

```shell
GET /fruit/_search?filter_path=hits.hits._source
```

```shell
GET /fruit/_search
{
  "query": {
    "match": {
      "name": "apple"
    }
  }
}
```

```shell
GET /fruit/_search
{
  "query": {
    "match": {
      "price": 10
    }
  }
}
```

```shell
DELETE /fruit
```
