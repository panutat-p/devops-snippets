# MinIO

https://hub.docker.com/r/minio/minio

https://github.com/minio/minio

## Simple

```yaml
services:
  minio:
    image: minio/minio
    volumes:
      - type: volume
        source: minio_data
        target: /data
    ports:
      - '9000:9000'
    environment:
      MINIO_ACCESS_KEY: root
      MINIO_SECRET_KEY: 1234
    restart: unless-stopped

volumes:
  minio_data:
    external: true
```

### Generate local Amazon credentials file

```sh
aws configure --profile local
```

```sh
cat ~/.aws/config
```

```sh
cat ~/.aws/credentials
```

```sh
aws configure list
```

```sh
export AWS_PROFILE=local
```
