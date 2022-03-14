FROM alpine

WORKDIR /usr/src/app

COPY curler.sh .

RUN apk add --update curl

CMD ./curler.sh
