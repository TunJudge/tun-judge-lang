FROM node:14.18.0-alpine

RUN apk update && apk add --no-cache g++ bash

RUN npm install -g ts-node @types/node typescript

WORKDIR /opt/code
