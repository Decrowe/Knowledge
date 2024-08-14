**docker pull**
- gets image from registry
**docker run**
- -d
- -t 
- --name
- (imagename)
**docker ps**
- lists running containers
**docker exec** -it (containername) (bash)
- type "exit" to exit 
**docker pull** (username):(tag)
- tags can be used for versioning

Run docker container with forwarded port:
**docker run** -d -t -p (host-port):(container-port) --name (container-name) (image)
docker stop (containername)

**docker stats**
- displays ressources used by the containers