#Docker basic commands

> docker pull alpine

output

```console
$ docker pull alpine
Using default tag: latest
latest: Pulling from library/alpine
ff3a5c916c92: Already exists
Digest: sha256:7df6db5aa61ae9480f52f0b3a06a140ab98d427f86d8d5de0bedab9b8df6b1c0
Status: Downloaded newer image for alpine:latest
```

```console
docker images
alpine                                              latest                   3fd9065eaf02        3 months ago        4.15MB
```

# Pull and run simple http server
Example: http server
https://github.com/fnichol/docker-uhttpd/blob/master/Dockerfile

```console
> docker pull fnichol/uhttpd
Using default tag: latest
latest: Pulling from fnichol/uhttpd
a3ed95caeb02: Already exists
1775fca35fb6: Pull complete
718e21306e6b: Pull complete
889bfeab2d4e: Pull complete
8ac43f1732b7: Pull complete
cefd08b5f834: Pull complete
a32be2ed7953: Pull complete
1c78be7a5ec7: Pull complete
74984e6e6d1c: Pull complete
Digest: sha256:28e6f95cf33ae1336525034e2b9d58ddf3cc63a2cdd9edebc8765321d96da9e0
Status: Downloaded newer image for fnichol/uhttpd:latest
```

## run an image
docker run  -p 8080:80 --name simple-http  fnichol/uhttpd

- see it on (docker ps)
- see localhost:8080 it responds!
- go inside machine using kitematic (or docker exec -it simple-http bash) THIS FAILS!

## map folders

docker run  -p 8085:80 -v %cd%/http/:/www/  --name simple-http-volume fnichol/uhttpd
