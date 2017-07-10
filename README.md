# docker_env
Linux host:
Using Ubuntu 16.04 on VirtualBox
Installing docker: https://docs.docker.com/engine/installation/linux/docker-ce/ubuntu/

Windows host:
Some useful commands:
docker inspect -f "{{ .NetworkSettings.Networks.nat.IPAddress }}" "containername"
