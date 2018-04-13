FROM alpine
WORKDIR /var/tmp/

RUN apk add --update nodejs nodejs-npm

RUN npm install -g http-server

EXPOSE 8080

CMD [ "http-server" ]