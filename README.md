<h1 align="center">vpp-base</h1>

<p align="center">
  <a href="https://hub.docker.com/r/ligato/vpp-base/builds"><img src="https://img.shields.io/docker/cloud/build/ligato/vpp-base.svg" alt="Docker Cloud Build Status"></a>
  <a href="https://hub.docker.com/r/ligato/vpp-base"><img src="https://img.shields.io/docker/pulls/ligato/vpp-base.svg" alt="Docker Pulls"></a>
</p>

<p align="center">The <b>vpp-base</b> provides code used for building docker images with VPP.</p>

---

## Use Cases

* Use as base image in docker images that work with VPP.
* Quickly test some feature in specific VPP version.
* Distribute _.deb_ packages for VPP where needed.
* Generate VPP binary API using installed _.api.json_ files.

## Quickstart

Following command will get you vpp-base image that comes with recent version of VPP:

```sh
# get the latest image
➢ docker pull ligato/vpp-base

# print the VPP version
➢ docker run --rm ligato/vpp-base cat /vpp/version
19.08-rc0~235-gfe52dea08~b2798
```

## Image Contents

The vpp-base image consists of:
 
- **Installed VPP** ready for use with default config - `/etc/vpp/startup.conf`
- **Download script** for getting VPP from [PackageCloud][packagecloud-fdio] - `/vpp/get-vpp.sh`
- **All _.deb_ packages** that come with VPP - `/vpp/*.deb`
- **Version file** that contains VPP version - `/vpp/version` 

## Published Versions

The vpp-base images are [built continuously][dockercloud-builds] and published to DockerHub repository [ligato/vpp-base][dockerhub].

Beside the `vpp-base:latest` image built from master, there are images with stable VPP version. These images are tagged with the respective VPP version they contain: `ligato/vpp-base:YYMM`. 

Following images are currently published and available on DockerHub:

| Image | Details | VPP source |
|---|---|---|
|[![latest](https://img.shields.io/badge/ligato/vpp--base-latest-blue.svg?logo=docker&logoColor=white&style=popout)][dockerhub] | [![](https://images.microbadger.com/badges/image/ligato/vpp-base.svg)](https://microbadger.com/images/ligato/vpp-base:latest) | [![master](https://img.shields.io/badge/packagecloud_repo-master-37327b.svg?logo=debian)](https://packagecloud.io/fdio/master) |
|[![1904](https://img.shields.io/badge/ligato/vpp--base-1904-blue.svg?logo=docker&logoColor=white&style=popout)][dockerhub] | [![](https://images.microbadger.com/badges/image/ligato/vpp-base:1904.svg)](https://microbadger.com/images/ligato/vpp-base:1904) | [![1904](https://img.shields.io/badge/packagecloud_repo-1904-37327b.svg?logo=debian)](https://packagecloud.io/fdio/1904) |
|[![1901](https://img.shields.io/badge/ligato/vpp--base-1901-blue.svg?logo=docker&logoColor=white&style=popout)][dockerhub] | [![](https://images.microbadger.com/badges/image/ligato/vpp-base:1901.svg)](https://microbadger.com/images/ligato/vpp-base:1901) | [![1901](https://img.shields.io/badge/packagecloud_repo-1901-37327b.svg?logo=debian)](https://packagecloud.io/fdio/1901) |

The complete list of available image tags can be found on [DockerHub][dockerhub-tags].

## Building Image

To build custom vpp-base image you can simply use docker build command with without cloning this git repository, you can use:

```sh
# Latest VPP
➢ docker build github.com/ligato/vpp-base

# Stable VPP 19.04
➢ docker build --build-arg REPO='1904' github.com/ligato/vpp-base

# With specific VPP version
➢ docker build --build-arg VPP_VERSION='19.08-rc0~196-g7fe470a54' github.com/ligato/vpp-base

# With specific VPP commit
➢ docker build --build-arg VPP_VERSION='19.04[^ ]*-g7fe470a54' github.com/ligato/vpp-base
```

[dockerhub]: https://hub.docker.com/r/ligato/vpp-base
[dockerhub-tags]: https://hub.docker.com/r/ligato/vpp-base/tags
[dockercloud-builds]: https://hub.docker.com/r/ligato/vpp-base/builds
[packagecloud-fdio]: https://packagecloud.io/fdio
