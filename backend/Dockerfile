FROM alpine:latest

COPY nginx/nginx.conf etc/nginx/nginx.conf

WORKDIR /app

RUN apk update && apk add nginx nodejs npm

COPY package*.json ./

RUN npm install && npm install -g pm2

COPY app/ app/

COPY server.js ./server.js

COPY runner.sh ./runner.sh

RUN chmod +x runner.sh

EXPOSE 80

ENTRYPOINT [ "sh", "runner.sh" ]