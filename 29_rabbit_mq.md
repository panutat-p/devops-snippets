# Rabbit MQ

https://hub.docker.com/_/rabbitmq

```yaml
services:
  rabbitmq:
    image: rabbitmq:3-management
    ports:
      - "5672:5672"
      - "15672:15672"
    volumes:
      - type: volume
        source: rabbitmq_data
        target: /var/lib/rabbitmq
    environment:
      - RABBITMQ_DEFAULT_USER=user
      - RABBITMQ_DEFAULT_PASS=password

volumes:
  rabbitmq_data:
```
