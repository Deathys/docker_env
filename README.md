# docker_env
some useful commands:

docker inspect -f "{{ .NetworkSettings.Networks.nat.IPAddress }}" <containername>
