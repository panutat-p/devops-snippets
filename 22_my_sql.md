# MySQL

https://hub.docker.com/_/mysql

```yaml
version: '3.9'

services:
  mysql:
    image: mysql:8
    ports:
      - '80:80'
    environment:
      MYSQL_ROOT_PASSWORD: 1234
      MYSQL_DATABASE: fruits
      MYSQL_USER: admin
      MYSQL_PASSWORD: 1234
    volumes:
      - type: volume
        source: mysql_data
        target: /var/lib/mysql
    restart: unless-stopped

volumes:
  mysql_data:
    external: true
```
