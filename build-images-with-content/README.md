# Build an image with embedded contents
This put  content into an image during build. It is useful to provide your own image with inside your ready application.

This is very simple, just use COPY command to add contents

> COPY http /var/tmp/

Using the right combination of "RUN" and "COPY" you will be able to realize all your forbidden dreams, or quite.


```console
docker build . -t http-server-embedded
```


```console
 docker run -p 8086:8080 --name http-server-embedded-instance http-server-embedded
 ```

[localhost:8086](http://localhost:8086)

 ```console
 docker exec -it http-server-embedded-instance bash
 ```
