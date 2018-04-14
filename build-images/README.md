 # Build your first docker image
 Docker syntax to build a docker image is very simple. Just:

 - put a "Dockerfile" into a folder
 - move to the foder and run the docker build command

**Note** please note Dockerfile content before barely run next command.
 
 > docker build . -t http-server-cool

 Yes, http-server-cool is otional but very useful to recognize docker images.

```console
 Sending build context to Docker daemon   2.56kB
Step 1/6 : FROM alpine
 ---> 3fd9065eaf02
Step 2/6 : WORKDIR /
 ---> Using cache
 ---> c54dc6991b73
Step 3/6 : RUN apk add --update nodejs nodejs-npm
 ---> Running in cdc644ab87ba
fetch http://dl-cdn.alpinelinux.org/alpine/v3.7/main/x86_64/APKINDEX.tar.gz
fetch http://dl-cdn.alpinelinux.org/alpine/v3.7/community/x86_64/APKINDEX.tar.gz
(1/10) Installing ca-certificates (20171114-r0)
(2/10) Installing nodejs-npm (8.9.3-r1)
(3/10) Installing c-ares (1.13.0-r0)
(4/10) Installing libcrypto1.0 (1.0.2o-r0)
(5/10) Installing libgcc (6.4.0-r5)
(6/10) Installing http-parser (2.7.1-r1)
(7/10) Installing libssl1.0 (1.0.2o-r0)
(8/10) Installing libstdc++ (6.4.0-r5)
(9/10) Installing libuv (1.17.0-r0)
(10/10) Installing nodejs (8.9.3-r1)
Executing busybox-1.27.2-r7.trigger
Executing ca-certificates-20171114-r0.trigger
OK: 61 MiB in 21 packages
Removing intermediate container cdc644ab87ba
 ---> 9dec484019b0
Step 4/6 : RUN npm install -g http-server
 ---> Running in 687cb0ed9124
/usr/bin/http-server -> /usr/lib/node_modules/http-server/bin/http-server
/usr/bin/hs -> /usr/lib/node_modules/http-server/bin/http-server
+ http-server@0.11.1
added 23 packages in 4.169s
Removing intermediate container 687cb0ed9124
 ---> 2e0288ed7fba
Step 5/6 : EXPOSE 8080
 ---> Running in 0f9c56224a68
Removing intermediate container 0f9c56224a68
 ---> d48eee064c59
Step 6/6 : CMD [ "http-server" ]
 ---> Running in 5091a6a58ce8
Removing intermediate container 5091a6a58ce8
 ---> 36bb15f5801d
Successfully built 36bb15f5801d
```

Where is my image? Just run *docker images* !!

## Try to run the image
As for regular images pulled from docker, just run it!

```console
docker run -p 8091:8080 --name http-server-cool-instance http-server-cool
```
[localhost:8091](http://localhost:8091)


Yes, also in this case name is optional... but you'll agree with me is easier to find instance by speaking name rater then by meaningless sequence of characters.

```console
docker  exec -it  http-server-cool-instance bash


docker stop  http-server-cool-instance ; docker rm  http-server-cool-instance

```
yes, also in this case you can execute remote code (and maybe use bash to access it)


## Points of interest
You can build your own machine by adding  a set of command on a docker file. Each command means  a new layer is created. Bad news is that layers do not comunicate one each other so you will usually manage a long set of *&&* separated command ( you are partially saved by using  **&& \\** to have some that can be read without an headhache)

** Alpine Linux image doesn't contain bash, Instead you can use /bin/ash, /bin/sh, ash or only sh. Now you know with previous step was just didattic**