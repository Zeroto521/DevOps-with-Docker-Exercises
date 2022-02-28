# FROM ubuntu:latest
FROM golang:1.16

EXPOSE 8080

WORKDIR /usr/src/app

COPY . .

ENV REQUEST_ORIGIN http://localhost:5000

RUN go env -w GOPROXY=https://goproxy.cn
RUN go build
RUN go test

CMD ./server
