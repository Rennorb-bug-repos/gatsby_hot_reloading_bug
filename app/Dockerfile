FROM node:17-alpine3.12 as builder
RUN apk update && apk add build-base autoconf automake libtool pkgconfig nasm

WORKDIR /app

COPY ./package*.json ./
COPY ./gatsby-*.js ./
ENV GATSBY_TELEMETRY_DISABLED=1
RUN npm ci

FROM node:17-alpine3.12
WORKDIR /app

COPY --from=builder /app/node_modules ./node_modules

COPY . ./

ENV GATSBY_TELEMETRY_DISABLED=1
CMD ["ash", "-c", "npm run build && npm run develop"]