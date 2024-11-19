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
