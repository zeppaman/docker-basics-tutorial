FROM alpine
WORKDIR /var/tmp/

RUN apk add --update nodejs nodejs-npm

#RUN apk add --update bash && rm -rf /var/cache/apk/*

RUN npm install -g http-server

EXPOSE 8080

CMD [ "http-server" ]