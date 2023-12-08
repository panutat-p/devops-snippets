# wget

## options

* `-q` hide wget info
* `-O arg` specify output
* `-t arg` set number of retries
* `-m` mirror

```shell
apt install wget
```

Save a web page
```shell
wget http://go.dev \
  -O home.html
```

Show Output in stdout
```shell
wget -O - https://example.com
```

```shell
wget -q -O /dev/stdout https://example.com
```

Download file
```shell
wget -O go.tar.gz https://go.dev/dl/go1.21.4.linux-amd64.tar.gz
```

Download mirror of a website
```shell
wget -m https://example.com
```
