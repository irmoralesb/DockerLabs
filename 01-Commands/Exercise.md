# Image vs Container

Differences between image and container

# Running the first container

https://hub.docker.com/_/nginx

`docker run --name my_nginx -it -p 8080:80 nginx /bin/sh`

etc/os-release
exit
(Use the browser)

`docker container ps`

`docker stop my_nginx`

`docker start my_nginx` 

`docker container ps -a`

# How to get an image

## Getting Latest DotNet Linux Image

https://hub.docker.com/

https://hub.docker.com/explore


* Ubuntu - https://hub.docker.com/_/ubuntu
  `docker pull ubuntu`

* Amazon Linux - https://hub.docker.com/_/amazonlinux
  `docker pull amazonlinux`

* Microsoft Repos - https://hub.docker.com/r/microsoft/dotnet
  .Net SDK - `docker pull mcr.microsoft.com/dotnet/sdk`
  .Net Runtime - `docker pull mcr.microsoft.com/dotnet/runtime`
  .Net Asp.Net - `docker pull mcr.microsoft.com/dotnet/aspnet`


### Image Commands

* docker pull ... - Get image from remote repo
* docker images - list the local images
* docker image rmi <image_name> - delete local image, it must not be used by a container
* docker image prune - remove all unused images
* docker image inspect <image_name>

### Container Commands

* docker container ps [-a]
* docker run -it -p ####:#### --name `<container_name>` `<image_name>` [start_command]
* docker start `<container_name>`
* docker stop `<container_name>`
* docker container logs `<container_name>`
* docker container --help
* docker container rm `<container_name>`
  * docker container rm $(docker ps -a --format '{{.Names}}')
    (docker ps -a -q -f status=exited | xargs docker container rm)
