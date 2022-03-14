FROM node:16 as build

WORKDIR /usr/src/app

COPY . .

RUN npm install && \
    npm run build


FROM alpine

WORKDIR /usr/src/app

COPY --from=build /usr/src/app/build ./build

RUN apk add --update nodejs npm && \
    npm install -g serve && \
    adduser -D userapp

USER userapp

CMD npx serve -s -l 5000 build
