FROM alpine
WORKDIR /var/tmp/

RUN apk add --update nodejs nodejs-npm

RUN npm install -g http-server

RUN apk add --update bash && rm -rf /var/cache/apk/*

COPY http /var/tmp/

EXPOSE 8080

CMD [ "http-server" ]