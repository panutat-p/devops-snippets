# Dockerfile Go

https://hub.docker.com/_/golang

https://hub.docker.com/_/alpine

## Simple

https://docs.docker.com/language/golang/build-images

```Dockerfile
FROM golang:1.21

WORKDIR /app
COPY go.mod go.sum ./
RUN go mod download
COPY . ./

RUN CGO_ENABLED=0 GOOS=linux GOARCH=amd64 go build -o /app

EXPOSE 8080
CMD ["/app"]
```

## Multi-stage

https://docs.docker.com/build/building/multi-stage

```Dockerfile
FROM golang:1.21 as builder
WORKDIR /opt
COPY go.mod go.sum ./
RUN go mod download
COPY . ./
RUN CGO_ENABLED=0 GOOS=linux GOARCH=amd64 go build -o /app

FROM alpine:3.18
COPY --from=builder /app /app
EXPOSE 8080
CMD ["/app"]
```

## Docker ignore

https://docs.docker.com/build/building/context/#dockerignore-files

`.dockerignore`
```
*.md
*.log
.git
.aws
*.env
*.env.*
.coverage
.coverage.*
.idea
.vscode

bin
```
