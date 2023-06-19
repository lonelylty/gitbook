```shell
#1.use ssh to upload docker-compose.yml and docker images to server directory
mkdir -p /directory   

#2.load docker images
docker load -i xxx.tar
or
docker load -i xxx.tar.gz

#3.create docker container
docker-compose up -d