# Docker Notes



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