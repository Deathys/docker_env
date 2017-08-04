# docker_env
Linux host:

Using Ubuntu 16.04 on VirtualBox

Installing docker: https://docs.docker.com/engine/installation/linux/docker-ce/ubuntu/ (Install Docker CE, just follow the instructions)

https://gist.github.com/kjtanaka/38c6baed3c60b7dd9f7c727edab38851 - how connect containers to external network:

- sudo ip addr del 192.168.1.57 dev enp0s8
- sudo brctl addif docker1 enp0s8
- sudo docker network create --driver bridge --subnet=192.168.1.0/24 --gateway=192.168.1.57 --opt "com.docker.network.bridge.name"="docker1" shared_nw

Installing docker-compose: 
  - just download one of latest release https://github.com/docker/compose/releases 
  - then copy docker-compose to /usr/local/bin/
  - chmod +x /usr/local/bin/docker-compose

Some useful commands:
1. sudo docker network create -d bridge -o com.docker.network.windowsshim.interface="enp0s9" --subnet=192.168.1.0/12 --gateway=192.168.1.1 MyBridge
2. sudo docker exec -i -t "CONTAINER_ID"  /bin/bash


Windows host:
Some useful commands:
1. docker inspect -f "{{ .NetworkSettings.Networks.MyBridge.IPAddress }}" "containername"
2. docker network create -d l2bridge  -o com.docker.network.windowsshim.interface="Ethernet 3" --subnet=192.168.1.0/12 --gateway=192.168.1.1 MyBridge
