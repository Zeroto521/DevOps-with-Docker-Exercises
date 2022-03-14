FROM golang:alpine3.13 as build

WORKDIR /usr/src/app

COPY . .

RUN go env -w GOPROXY=https://goproxy.cn && \
    go build


FROM alpine

WORKDIR /usr/src/app

COPY --from=build ./usr/src/app/server ./server

CMD ./server
