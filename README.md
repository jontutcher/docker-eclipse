# docker-tbc

[TopBraid Composer](http://www.topquadrant.com/downloads/topbraid-composer-install/) in a Docker container, pulling from BBC R&D-proxified base image. Forked & modified from [fgrehm/docker-eclipse](https://github.com/fgrehm/docker-eclipse)

## Requirements

* Docker 1.2+ (should work fine on 1.0+ but I haven't tried)
* A copy of [TopBraid Composer](http://www.topquadrant.com/downloads/topbraid-composer-install/).
* An X11 socket

## Quickstart

Assuming `$HOME/bin` is on your `PATH` and that you are able to run `docker`
commands [without `sudo`](http://docs.docker.io/installation/ubuntulinux/#giving-non-root-access),
you can use the [provided `tbc` script](eclipse) to start a disposable
Eclipse Docker container with your project sources mounted at `/home/developer/workspace`
within the container.

Once you close Eclipse the container will be removed and no traces of it will be
kept on your machine (apart from the Docker image of course).

## Workspaces

The `tbc` script will use the value of the `$TBC_WORKSPACE` environment variable to mount a TopBraid workspace locally. If this isn't found, it uses the current directory. 

## Help! I started the container but I don't see the Eclipse screen

You might have an issue with the X11 socket permissions since the default user
used by the base image has an user and group ids set to `1000`, in that case
you can run either create your own base image with the appropriate ids or run
`xhost +` on your machine and try again.
