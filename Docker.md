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
##### Docker Build
`docker build .` 

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

#### Run an image using a specific port 
```
docker run --name <containerName> -p <yourport>:<dockerPort> <imageName>

```
* `-e` to pass in ENV variables 


#### Create a tag TARGET_IMAGE that refers to SOURCE_IMAGE
`docker tag SOURCE_IMAGE[:TAG] TARGET_IMAGE[:TAG]` 


#### Purging All Unused or Dangling Images, Containers, Volumes, and Networks
* Docker provides a single command that will clean up any resources — images, containers, volumes, and networks — that are dangling (not associated with a container):
```
docker system prune
```

* To additionally remove any stopped containers and all unused images (not just dangling images), add the -a flag to the command:

```
docker system prune -a
```

##### Removing Docker Images
##### Remove one or more specific images
* Use the docker images command with the -a flag to locate the ID of the images you want to remove. This will show you every image, including intermediate image layers. When you've located the images you want to delete, you can pass their ID or tag to docker rmi:

``` 
List:
docker images -a

Remove:
docker rmi Image Image
```

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

### To pull an image from Azure
* Login: `az login`
* Then login into the registry: `az acr login --name <registryName>`
* Then pull the image: `docker pull cfchildren.azurecr.io/lms:latest`


Sources: 
* [Medium article](https://medium.com/@ibrahimgunduz34/be-careful-while-playing-docker-about-timezone-configuration-e7a2217e9b76)
* [Stack Overflow](https://unix.stackexchange.com/questions/140734/configure-localtime-dpkg-reconfigure-tzdata)