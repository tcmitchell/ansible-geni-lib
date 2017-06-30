# Test on Ubuntu 16.04

## Build a Docker image

We need a docker image with Ubuntu 16.04 that has the ssh daemon
running so that it can be a target for ansible. A Dockerfile is
supplied in `docker/Ubuntu16`.

```shell
# From the tests directory

docker build -t ssh:Ubuntu16 docker/Ubuntu16
```

## Test the playbook

Test the playbook against the Ubuntu 16.04 image constructed above:

```shell
ansible-playbook geni-lib-ubuntu16.yml
```

# Test on CentOS 7

We can use a publicly available Docker image to test on CentOS 7. That
image is encoded in the test playbook.

_Note: it might be a good idea to grab the Dockerfile for this image
and capture it in the repository so that if the image is no longer
available, it can be reconstructed._

See https://github.com/CentOS/CentOS-Dockerfiles/tree/master/ssh/centos7
for a Dockerfile to construct a CentOS 7 image with ssh. It's a lot
simpler than the one in use now, and could be more repeatable this way.

```shell
ansible-playbook geni-lib-centos7.yml
```
