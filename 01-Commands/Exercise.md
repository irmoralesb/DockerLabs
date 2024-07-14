# The Windows Subsystem for Linux (WSL)

`wsl.exe --install`
`wsl.exe --install --no-distribution`

## Installation Troubleshooting

`dism.exe /online /enable-feature /featurename:Microsoft-Windows-Subsystem-Linux /all /norestart`

`dism.exe /online /enable-feature /featurename:VirtualMachinePlatform /all /norestart`

`wsl --set-default-version 2`

## Testing

`wsl`

It displays network interface data
`ifconfig`

It displays the kernel info
`uname -a`

It displays distro data
`lsb_release -a`

It displayes available distros for WSL
`wsl --list --online`

## Installation

Installing distros
`wsl --installing debian`
`wsl --installing ubuntu`


## Basic Linux Commands


`cd`

`ls`

`less <file>`

`man`

### etc folder

`cat wsl.conf`

`less group`

`nano group`
`sudo nano group `
### home folder

`ls`

`mkdir`

`cp`

`mv`

`rm`

### var folder
In old system it stored temp data, such as emails

* log/

### Updating Distro

`sudo apt update`

`sudo apt upgrade`

### System Status

`sudo systemctl list-units`

* `sudo systemctl status apache2`
* `sudo systemctl enable apache2`
* `sudo systemctl disable apache2`
* `sudo systemctl restart apache2` ?

Shows the ip configuration, get the ip for requestion a page
`ip a`

### Logs

#### Old one - syslogd

`cd /var/log`
`ls`
`cat syslog`
`cat syslog | grep <word>`


#### New one - journalctl

`journalctl`
`journalctl -u <service> --since today`
* `journalctl -u apache2 --since today`

## Linux Security

| Permission  | Shortcut  | Value  |   
|---|---|---|
| Read | R |  4 |
| Write  | W  | 2  |
| Execute  | E  | 1  |

* Full Permissions: 7
* Read/Execute: 5
* Execute: 1

User  - Group - Everyone Else

Default permission for new files
`umask`
- for the last 3 digits, it works the other way around, 777: means no one has any permission. and 000 all have full access.

0022 - Owner has 7 (full access), Group and everybody else have 5 (RX)

Change permission
`chmod 755`

Change Ownership
`sudo chown root:root <file>`

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
