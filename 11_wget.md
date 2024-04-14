# wget

## Options

* `-q` hide wget info
* `-O arg` specify output
* `-t arg` set number of retries
* `-m` mirror
* `-c` continue

Save a web page
```sh
wget http://go.dev \
  -O home.html
```

Show Output in stdout
```sh
wget -O - https://example.com
```

```sh
wget -q -O /dev/stdout https://example.com
```

Download file
```sh
wget -O go.tar.gz https://go.dev/dl/go1.21.4.linux-amd64.tar.gz
```

Download mirror of a website
```sh
wget -m https://example.com
```

Resume the download
```sh
wget -c https://go.dev/dl/go1.22.0.linux-amd64.tar.gz
```
