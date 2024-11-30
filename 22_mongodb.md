# MongoDB

## Mongo Shell

https://www.mongodb.com/docs/mongodb-shell/install

MacOS
```sh
brew install mongosh
```

Ubuntu
```sh
wget -qO- https://www.mongodb.org/static/pgp/server-8.0.asc | tee /etc/apt/trusted.gpg.d/server-8.0.asc

echo "deb [ arch=amd64,arm64 ] https://repo.mongodb.org/apt/ubuntu jammy/mongodb-org/8.0 multiverse" | tee /etc/apt/sources.list.d/mongodb-org-8.0.list

apt update

apt install -y mongodb-mongosh
```

```sh
mongosh --version
```

## Compose

```yaml
services:

  mongodb8:
    container_name: mongodb8
    image: mongo:8
    ports:
      - '27017:27017'
    environment:
      - MONGO_INITDB_ROOT_USERNAME=root
      - MONGO_INITDB_ROOT_PASSWORD=1234
      - MONGO_INITDB_DATABASE=demo
    volumes:
      - type: volume
        source: mongodb8_data
        target: /data/db
    restart: on-failure


volumes:
  mongodb8_data:
    external: true
```

```sh
mongosh 'mongodb://root:1234@localhost/admin'
```
