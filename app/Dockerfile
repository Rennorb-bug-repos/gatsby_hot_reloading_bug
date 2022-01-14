FROM node:17-alpine3.12 as builder
RUN apk update && apk add build-base autoconf automake libtool pkgconfig nasm

WORKDIR /app

copy . .
RUN npm i

CMD ["npm", "run", "develop"]