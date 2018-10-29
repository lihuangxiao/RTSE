# Docker handbook

### installation
```
curl -fsSL https://download.docker.com/linux/ubuntu/gpg | sudo apt-key add -
sudo add-apt-repository \
   "deb [arch=amd64] https://download.docker.com/linux/ubuntu \
   $(lsb_release -cs) \
   stable"
sudo apt-get update
sudo apt-get install docker-ce
sudo usermod -aG docker $USER
sudo curl -L https://github.com/docker/compose/releases/download/1.22.0/docker-compose-$(uname -s)-$(uname -m) -o /usr/local/bin/docker-compose
sudo chmod +x /usr/local/bin/docker-compose
```

### cheatsheet
+ login to docker registery
  + aws: `$(aws ecr get-login --no-include-email --region us-west-2)`
  + gcp: `docker login -u oauth2accesstoken -p "$(gcloud auth print-access-token)" https://gcr.io`
+ `docker system prune`
+ `docker pull 160712987787.dkr.ecr.us-west-2.amazonaws.com/*`
+ `docker tag IMAGE_HASH REMOTE_REPO:TAG` for remote
+ `docker push REMOTE_REPO:TAG`
+ `docker run --entrypoint START_CMD IMAGE START_CMD_ARGS`
+ `docker exec -it CONTAINER_HASH bash`
+ `docker commit CONTAINER_HASH REMOTE_REPO:TAG`
+ `docker build --no-cache -f ${DOCKERFILE} .`
+ `docker build --no-cache -f ${DOCKERFILE} conf -q | sed 's/sha256://`
