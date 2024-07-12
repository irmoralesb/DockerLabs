# Image vs Container

Differences between image and container

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

