# DB Mate

https://github.com/amacneil/dbmate

## Install

### Homebrew

```sh
brew install mysql-client
export PATH=$PATH:/opt/homebrew/opt/mysql-client/bin
mysqldump --version
```

```sh
brew install dbmate
dbmate --version
```

### Docker

https://ghcr.io/amacneil/dbmate

https://hub.docker.com/r/amacneil/dbmate

## CLI

```sh
export DATABASE_URL='mysql://root:1234@localhost:3306/poc'
export DBMATE_MIGRATIONS_DIR=$HOME/compose/poc
export DBMATE_SCHEMA_FILE=$HOME/compose/poc/schema.sql
```

```sh
dbmate new 'create_fruit'
```

```sh
dbmate wait
```

```sh
dbmate up
```

```sh
dbmate rollback
```

```sh
dbmate -u 'mysql://root:1234@localhost:3306/poc' -d ~/compose/poc up -s ~/compose/poc
```

`yyyymmddHHmmss_create_fruits_table.sql`
```sql
-- migrate:up
CREATE TABLE fruit (
    id INT AUTO_INCREMENT PRIMARY KEY,
    name VARCHAR(255) NOT NULL,
    price DECIMAL(10,2) NOT NULL
);
CREATE INDEX idx_fruits_name ON fruit(name);
INSERT INTO fruit (name, price) VALUES ('apple', 12.20);
INSERT INTO fruit (name, price) VALUES ('banana', 8.00);
INSERT INTO fruit (name, price) VALUES ('carrot', 6.50);
INSERT INTO fruit (name, price) VALUES ('durian', 50.50);

-- migrate:down
DROP INDEX idx_fruits_name ON fruit;
DROP TABLE fruit;
```
