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

### CLI

https://github.com/minio/mc

MacOS
```sh
brew install minio-mc
```

Ubuntu
```sh
wget https://dl.min.io/client/mc/release/linux-amd64/mc
chmod +x mc
mv mc /usr/local/bin
```

```sh
mc --autocompletion
```

```sh
mc alias set s3 http://localhost:9000 root 1234
```

```sh
mc cp apple.jpg s3/fruits
```
