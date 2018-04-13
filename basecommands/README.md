# Docker basic commands
First of all pull command. It takes images from docker hub and bring to our local host.

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

Then we can use docker images command to display all images. You should see downloaded image. Please notice size (less than 5 MB).

```console
docker images
alpine                                              latest                   3fd9065eaf02        3 months ago        4.15MB
```

## Pull and run simple http server

This example will pull an image with a build in http server. This image stars from the base OS image then add many layer to get full functionalities.

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

## Run an image

Now we have the image, let's try to run it. Notice that we need to map port to reach the virtual docker network. Usually we do not use ports that may be in conflict with tradizional port service in host machine.

docker run  -p 8080:80 --name simple-http  fnichol/uhttpd

What to do now?

- see it turned on (using **docker ps** that list docke containers)
- see localhost:8080 it responds! Great!
- go inside machine using kitematic (or **docker exec -it simple-http bash**)  => why didn't work? please see next chapter!

## Map folders

Just notice your image starts with built in content. How to put your application files inside? This is done by mapping volumes. Volumes link local files to the container so that you can let container read some path on your drive (just to make a comparison it seems very similar to symbolic links on linux!)

docker run  -p 8085:80 -v %cd%/http/:/www/  --name simple-http-volume fnichol/uhttpd

**Note:** %cd% have to be changed with 'pwd' in linux.


## Point of interest
We can downlad docker images, run it locally and changes to run or application. 