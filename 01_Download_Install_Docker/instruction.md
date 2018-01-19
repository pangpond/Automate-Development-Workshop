#Workshop 1: Install Docker

## 1. Download and install
- Windows 10: [Docker Community Edition for Windows](https://store.docker.com/editions/community/docker-ce-desktop-windows). 
- Mac OSX: [Docker Community Edition for Mac](https://store.docker.com/editions/community/docker-ce-desktop-mac)  
- Ubuntu: [Docker Community Edition for Ubuntu](https://store.docker.com/editions/community/docker-ce-server-ubuntu)
	
## 2. Check docker functional
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

## 3. Pull images
Run command below for pull image and preparation (Line-by-Line): This will take about 15 - 20 min for pull

```
docker pull bitnami/nginx
docker pull bitnami/php-fpm
docker pull bitnami/postgresql
docker pull composer
```

## 4. Basic Commands
ref from [docker-tutorial-series](https://rominirani.com/docker-tutorial-series-part-2-basic-commands-baaf70807fd3)

```
docker version
docker info
docker images #check sizing and detail of all image
docker inspect bitnami/nginx:latest
docker search nginx
docker ps --all 
docker run -t -i busybox
```

## 5. Run Container from Image
5.1. run docker for nginx web server by command

```
docker run -dt --user root --name nginxtest -p 80:8080 -p 443:8443 bitnami/nginx
```

5.2. open browser with url: 

```
http://localhost
https://localhost
```

5.3. access shell to container with command:

```
docker exec -it nginxtest bash
```

5.4. Check file ```index.html``` with command: 

```
more index.html
```

5.5. Check path of container by command: 

```
pwd
exit
```
5.6. Stop container and remove from system by command:

```
docker stop nginxtest
docker rm nginxtest
```


## 6. Docker Machine

6.1. Check the installation by displaying the Machine version:

```
docker-machine version
```

6.2. for Ununtu install ```docker-macine``` command following by [Install Machine directly](https://docs.docker.com/machine/install-machine/)

6.3. Create machine

```
docker-machine create --driver=virtualbox --virtualbox-memory=600 dockerLab
```

6.3. ssh to docker machine

```
docker-machine ssh dockerLab
```

6.4. repeat Step 5


## 7. Map & Volume

7.1. Setup file sharing on docker option to current directory before operate / Apply & Restart
