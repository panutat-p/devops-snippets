# Curl

https://quickref.me/curl.html

https://gorest.co.in

## Basic

Show response header
```shell
curl -i https://gorest.co.in/public/v2/users
```

Show only response header
```shell
curl -I https://gorest.co.in/public/v2/users
```

Redirect
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
