# ncat

https://nmap.org/ncat

https://nmap.org/ncat/guide/index.html

## Install

### Ubuntu

```sh
apt install -y ncat
```

### MacOS

https://nmap.org/book/inst-macosx.html

## connect mode

### manually retrieve a web page from an HTTP server

```sh
ncat -C google.com 80
```

```sh
ncat -C localhost 4000
```

hit enter twice
```
GET / HTTP/1.0
```

### Check TCP connection

```sh
ncat -vz localhost 4000
```

### Check UDP connection

```sh
ncat -vzu localhost 4000
```

## listen mode

### Host a an HTTP file

`hello.http`
```
HTTP/1.0 200 OK

<html>
  <body>
    <h1>Hello, world!</h1>
  </body>
</html>
```

```sh
ncat -l localhost 8080 < hello.http
```

### Host an HTML file

https://nmap.org/ncat/guide/ncat-tricks.html#ncat-httpserv

```sh
ncat -lk -p 8080 --sh-exec "echo -e 'HTTP/1.1 200 OK\r\n'; cat index.html"
```

### Forward proxy

```sh
ncat -lk 8080 --sh-exec 'ncat localhost 4000'
```
