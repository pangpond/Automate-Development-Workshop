#Workshop 1: Install Docker

##1. Download and install
- Windows 10: [Docker Community Edition for Windows](https://store.docker.com/editions/community/docker-ce-desktop-windows). 
- Mac OSX: [Docker Community Edition for Mac](https://store.docker.com/editions/community/docker-ce-desktop-mac)  
- Ubuntu: [Docker Community Edition for Ubuntu](https://store.docker.com/editions/community/docker-ce-server-ubuntu)
	
##2. Check docker functional
After finished then run below command for check docker fuctional

```
docker run hello-world
```

Expect Result

```
Hello from Docker!
This message shows that your installation appears to be working correctly.

To generate this message, Docker took the following steps:
 1. The Docker client contacted the Docker daemon.
 2. The Docker daemon pulled the "hello-world" image from the Docker Hub.
 3. The Docker daemon created a new container from that image which runs the
    executable that produces the output you are currently reading.
 4. The Docker daemon streamed that output to the Docker client, which sent it
    to your terminal.

To try something more ambitious, you can run an Ubuntu container with:
 $ docker run -it ubuntu bash

Share images, automate workflows, and more with a free Docker ID:
 https://cloud.docker.com/

For more examples and ideas, visit:
 https://docs.docker.com/engine/userguide/
```

##3. Pull images
Run command below for pull image and preparation (Line-by-Line): This will take about 15 - 20 min for pull

```
docker pull bitnami/nginx
docker pull bitnami/php-fpm
docker pull bitnami/postgresql
docker pull composer
```