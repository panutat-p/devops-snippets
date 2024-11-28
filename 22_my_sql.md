# MySQL

https://hub.docker.com/_/mysql

```yaml
services:
  mysql8:
    container_name: mysql8
    image: mysql:8
    ports:
      - '3306:3306'
    environment:
      MYSQL_ROOT_PASSWORD: 1234
    volumes:
      - type: volume
        source: mysql8_data
        target: /var/lib/mysql
    restart: unless-stopped

volumes:
  mysql8_data:
    external: true
```

```yaml
services:
  mysql5:
    container_name: mysql5
    image: mysql:5
    platform: linux/amd64
    ports:
      - '3306:3306'
    environment:
      MYSQL_ROOT_PASSWORD: 1234
    volumes:
      - type: volume
        source: mysql5_data
        target: /var/lib/mysql
    restart: unless-stopped


volumes:
  mysql5_data:
    external: true
```
