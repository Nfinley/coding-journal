# Docker Notes

## What is it? [GetStarted](https://docs.docker.com/get-started/)
* Docker is a platform for devs to develop, deploy and run applications with containers
* Containerization is popular because containers are: 
    * Flexible: Even the most complex applications can be containerized
    * Lightweight
    * Interchangeable
    * Portable
    * Scalable: You can increase and automatically distribute container replicas
    * Stackable: You can stack services vertically and on-the-fly
* An imag is an executable package that includes everything needed to run an application (code, libraries, env variables and config files)
* Container is a runtime instance of an image

## Setting up Docker to run locally

1. Install Docker
2. 


# CHEAT SHEET
##### List Docker CLI commands
```
docker
docker container --help
```

##### Display Docker version and info
```
docker --version
docker version
docker info
```

##### Execute Docker image
`docker run hello-world`

##### List Docker images
`docker image ls`

##### List Docker containers (running, all, all in quiet mode)
```
docker container ls
docker container ls --all
docker container ls -aq
```

#### Create a tag TARGET_IMAGE that refers to SOURCE_IMAGE
`docker tag SOURCE_IMAGE[:TAG] TARGET_IMAGE[:TAG]` 

### To update the timezone on a container

Within your `Dockerfile`:
```dockerfile
ENV TZ America/Los_Angeles
ENV PORT 8888
RUN npm install ;\
    apt-get update ;\
    apt-get install -y tzdata ;\
#    ln -snf /usr/share/zoneinfo/$TZ /etc/localtime ;\
    echo $TZ > /etc/timezone ;\
    dpkg-reconfigure -f noninteractive tzdata
```
Sources: 
* [Medium article](https://medium.com/@ibrahimgunduz34/be-careful-while-playing-docker-about-timezone-configuration-e7a2217e9b76)
* [Stack Overflow](https://unix.stackexchange.com/questions/140734/configure-localtime-dpkg-reconfigure-tzdata)