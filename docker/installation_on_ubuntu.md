# Installation on Ubuntu 14.04

## Prerequisites

> Docker requires a 64-bit installation regardless of your Ubuntu version. Additionally, your kernel must be 3.10 at minimum.

```
$ uname -r
3.11.0-15-generic
```

## Update your apt sources

1. Update package information, ensure that APT works with the https method, and that CA certificates are installed.
```
 $ sudo apt-get update
 $ sudo apt-get install apt-transport-https ca-certificates
```
2. Add the new GPG key.
```
$ sudo apt-key adv --keyserver hkp://p80.pool.sks-keyservers.net:80 --recv-keys 58118E89F3A912897C070ADBF76221572C52609D
```
3. Edit `/etc/apt/sources.list.d/docker.list`. Remove any existing entries. Add
```
# for ubuntu 14.04
deb https://apt.dockerproject.org/repo ubuntu-trusty main
```
4. Purge the old repo if it exists.
```
$ sudo apt-get update
$ sudo apt-get purge lxc-docker
$ apt-cache policy docker-engine
```
5. Install the recommended packages.
```
$ sudo apt-get install linux-image-extra-$(uname -r) linux-image-extra-virtual
```
6. Install docker
```
$ sudo apt-get install docker-engine
```
7. Verify `docker` is installed correctly
```
$ sudo docker run hello-world
```