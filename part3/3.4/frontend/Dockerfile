FROM ubuntu:18.04

WORKDIR /usr/src/app

COPY . .

RUN apt-get update && \
    apt-get install -y curl && \
    curl -sL https://deb.nodesource.com/setup_16.x | bash && \
    apt install -y nodejs && \
    npm install && \
    npm run build && \
    npm install -g serve && \
    npm cache clean --force && \
    apt-get purge -y --auto-remove curl && \
    rm -rf /var/lib/apt/lists/* && \
    useradd -m appuser

USER appuser

CMD npx serve -s -l 5000 build
