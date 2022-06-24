#!/bin/bash
docker run -it -v /MountPoint --name myalpes1 alpine /bin/ash
docker ps -a
docker start myalpes1
docker attach myalpes1
docker commit myalpes1 myalmine:v12
docker images 
docker export myalpes1 > latest.tar 
docker rmi -f $(docker images -q)
docker images 
cat latest.tar | docker import - myalpine:v12
docker images 
docker history myalpine:v12
docker login -u anaiswab -p*****
docker image tag myalpine:v12 anaiswab/myalpine:v12
docker push anaiswab/myalpine:v12
