# docker_env
Linux host:
Using Ubuntu 16.04 on VirtualBox

some useful commands:

docker inspect -f "{{ .NetworkSettings.Networks.nat.IPAddress }}" "containername"
