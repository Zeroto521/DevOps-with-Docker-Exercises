FROM ubuntu:18.04

WORKDIR /usr/src/app

COPY . .

ENV PATH /usr/local/go/bin:$PATH

RUN apt-get update && \
    apt-get install -y wget gcc && \
    rm -rf /usr/local/go && \
    wget -c https://golang.google.cn/dl/go1.16.15.linux-amd64.tar.gz && \
    tar -C /usr/local -xzf go1.16.15.linux-amd64.tar.gz  && \
    rm -rf /usr/local/go1.16.15.linux-amd64.tar.gz && \
    go env -w GOPROXY=https://goproxy.cn && \
    go build && \
    go clean --cache && \
    apt-get purge -y --auto-remove wget gcc && \
    rm -rf /var/lib/apt/lists/* && \
    useradd -m appuser

USER appuser

CMD ./server
