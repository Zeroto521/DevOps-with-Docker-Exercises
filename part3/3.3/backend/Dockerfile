FROM golang:1.16

WORKDIR /usr/src/app

COPY . .

RUN go env -w GOPROXY=https://goproxy.cn
RUN go build

RUN useradd -m appuser
USER appuser

CMD ./server
