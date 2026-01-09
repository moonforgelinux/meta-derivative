# meta-derivative

This is an example project for how derivative distributions can be made using the [meta-moonforge](https://github.com/moonforgelinux/meta-moonforge) Yocto layer.

Check this [tutorial](./HOWTO.md) for how this derivative example was made from scratch.

## Setup

The host requirements are:

* [docker](https://www.docker.com/) or [podman](https://podman.io/)
* python3-pip

See the official documentation for common Linux distributions like [Fedora](https://docs.docker.com/engine/install/fedora/) or [Ubuntu](https://docs.docker.com/engine/install/ubuntu/).

Install the necessary tooling to run kas:

```sh
$ pip install --user kas==5.0
$ kas-container --help
```

Create a workspace directory, needed to hold the persistent cache, and clone this repository:

```sh
$ mkdir workspace && cd workspace
$ mkdir cache
$ git clone https://github.com/moonforgelinux/meta-derivative.git
```

## Build

Set up cache directories to speed up subsequent builds:

```sh
$ cd meta-derivative
$ export KAS_CONTAINER_ENGINE=docker
$ export DL_DIR=$PWD/../cache/downloads/
$ export SSTATE_DIR=$PWD/../cache/sstate-cache/
```

Use *kas-container* to build the image:

```sh
$ cd meta-derivative
$ kas-container build kas/derivative-image-base-raspberrypi5.yml
```

## Test

Once the image is successfully built use a tool like [bmaptool](https://docs.yoctoproject.org/dev-manual/bmaptool.html) to flash the SD card:

```sh
$ cd meta-derivative
$ sudo bmaptool copy ./build/tmp/deploy/images/raspberrypi5/moonforge-image-base-raspberrypi5.rootfs.wic.bz2 /dev/sdX
```

## Legal

MIT License

Copyright (c) 2026 Igalia, S.L.

