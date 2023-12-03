# Curl

https://quickref.me/curl.html

https://gorest.co.in

## Options

* `-v` verbose
* `-vv` very verbose

* `-o arg` download and save to specified file name
* `-O` download
* `-w arg` display information on stdout

* `-i` show response header
* `-I` show only response header
* `-s` hide progress bar
* `-f` hide error
* `-S` show error

* `-1` force to use TLS version 1.X
* `-L` follow redirection

* `-X arg` specify a custom request method
* `-H arg` include extra header
* `-d arg` specify body


## Basic

```shell
curl -i https://gorest.co.in/public/v2/users
```

```shell
curl -L http://google.com
```

Show response time
```
curl https://gorest.co.in/public/v2/users \
  -s \
  -o /dev/null \
  -w '\nLookup time:\t%{time_namelookup}\nConnect time:\t%{time_connect}\nAppCon time:\t%{time_appconnect}\nRedirect time:\t%{time_redirect}\nPreXfer time:\t%{time_pretransfer}\nStartXfer time:\t%{time_starttransfer}\n\nTotal time:\t%{time_total}\n'
```

Download Go runtime
```shell
curl -OL https://go.dev/dl/go1.21.4.linux-amd64.tar.gz
```

## RESTful API

```shell
curl -X GET https://gorest.co.in/public/v2/users
```

```shell
curl -X POST https://gorest.co.in/public/v2/users
```

```shell
curl -X POST https://gorest.co.in/public/v2/users \
  -H "Accept: application/json" \
  -H "Content-Type: application/json" \
  -H "Authorization: Bearer 3fe3138f00b1813fae483eaa078df9d728fe2568fbab0ff0cee0d819e6b6e2e6" \
  -d '{"name":"John Doe", "gender":"male", "email":"john.doe@gmail.com", "status":"active"}'
```
