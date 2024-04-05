# MySQL

https://hub.docker.com/_/mysql

```yaml
services:
  mysql:
    image: mysql:8
    ports:
      - '3306:3306'
    environment:
      MYSQL_ROOT_PASSWORD: 1234
    volumes:
      - type: volume
        source: mysql_data
        target: /var/lib/mysql
    restart: unless-stopped

volumes:
  mysql_data:
    external: true
```

```yaml
services:
  mysql:
    image: mysql:5
    ports:
      - '3306:3306'
    environment:
      MYSQL_ROOT_PASSWORD: 1234
    volumes:
      - type: volume
        source: mysql_data
        target: /var/lib/mysql
    restart: unless-stopped

volumes:
  mysql_data:
    external: true
```
