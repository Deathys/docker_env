# docker_env
Linux host:

Using Ubuntu 16.04 on VirtualBox

Installing docker: https://docs.docker.com/engine/installation/linux/docker-ce/ubuntu/ (Install Docker CE, just follow the instructions)

Installing docker-compose: 
  - just download one of latest release https://github.com/docker/compose/releases 
  - then copy docker-compose to /usr/local/bin/
  - chmod +x /usr/local/bin/docker-compose

Windows host:
Some useful commands:
1. docker inspect -f "{{ .NetworkSettings.Networks.nat.IPAddress }}" "containername"
2. docker network create -d l2bridge --subnet=192.168.1.0/12 --gateway=192.168.1.1 MyBridgeNetwork2
