# MinIO

https://hub.docker.com/r/minio/minio

https://github.com/minio/minio

## Simple

```yaml
services:
  minio:
    image: minio/minio:latest
    volumes:
      - type: volume
        source: minio_data
        target: /data
    ports:
      - '9000:9000'
    environment:
      MINIO_ACCESS_KEY: 'AKIAIOSFODNN7EXAMPLE'
      MINIO_SECRET_KEY: 'wJalrXUtnFEMI/K7MDENG/bPxRfiCYEXAMPLEKEY'
    restart: unless-stopped

volumes:
  minio_data:
    external: true
```

## Generate local Amazon credentials file

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

## MinIO CLI

https://github.com/minio/mc

### Install

MacOS
```sh
brew install minio-mc
```

Ubuntu
```sh
wget -O /usr/local/bin/mc https://dl.min.io/client/mc/release/linux-amd64/mc && sudo chmod +x /usr/local/bin/mc
chmod +x /usr/local/bin/mc
```

```sh
mc --autocompletion
```

### Upload a file

```sh
mc alias set local http://localhost:9000 'AKIAIOSFODNN7EXAMPLE' 'wJalrXUtnFEMI/K7MDENG/bPxRfiCYEXAMPLEKEY'
```

```sh
mc cp apple.jpg s3/fruits
```
