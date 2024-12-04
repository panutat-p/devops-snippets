# MinIO

https://github.com/minio/minio

## Compose

https://hub.docker.com/r/minio/minio

https://min.io/docs/minio/container/index.html

```yaml
services:

  minio:
    container_name: minio
    image: 'minio/minio:latest'
    ports:
      - '9000:9000'
      - '9001:9001'
    environment:
      MINIO_ROOT_USER: 'root'
      MINIO_ROOT_PASSWORD: '12345678'
      AWS_ACCESS_KEY_ID: root
      AWS_SECRET_ACCESS_KEY: 12345678
      AWS_DEFAULT_REGION: ap-southeast-1
      AWS_ENDPOINT_URL_S3: http://localhost:9000
    command: server /data --console-address ":9001"
    volumes:
      - type: volume
        source: minio_data
        target: /data
    restart: unless-stopped

  minio-cli:
    container_name: minio-cli
    image: 'minio/minio:latest'
    environment:
      MINIO_ROOT_USER: 'root'
      MINIO_ROOT_PASSWORD: '12345678'
    entrypoint: ["/bin/sh", "-c"]
    command: >
      "sleep 3 &&
      mc alias set local http://minio:9000 root 12345678 &&
      mc mb local/fruit"
    depends_on:
      - minio
    restart: no


volumes:
  minio_data:
    external: false
```

## MinIO CLI

https://github.com/minio/mc

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

```sh
export AWS_PROFILE=local
aws configure set output yaml
aws configure set region ap-southeast-1
aws configure set aws_access_key_id root
aws configure set aws_secret_access_key 12345678
aws configure set s3.signature_version s3v4
aws configure set s3.endpoint_url http://localhost:9000

mc alias set local http://localhost:9000 root 12345678
mc mb local/fruit
```
