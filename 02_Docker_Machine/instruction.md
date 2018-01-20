# Workshop 2: Docker Machine

## 1. Install Docker Machine
normally Docker Machine ins installes along with Docker for Mac, Docker for Windows, or Docker Toolbox.
That mean you dont't need to install again.

1.1. Check the installation by displaying the Machine version:

```
docker-machine version
```

1.2. for Ununtu install ```docker-macine``` command following by [Install Machine directly](https://docs.docker.com/machine/install-machine/)

1.3. Create machine

```
docker-machine create --driver=virtualbox --virtualbox-memory=600 dockerLab
```

1.4. ssh to docker machine

```
docker-machine ssh dockerLab
```

1.5. Repeat Step 4 and Step 5 from Workshop 1

```
docker pull bitnami/nginx
docker version
docker info
docker images #check sizing and detail of all image
docker inspect bitnami/nginx:latest
docker search nginx
docker ps --all 
docker run -t -i busybox

docker run -dt --user root --name nginxtest -p 80:8080 -p 443:8443 bitnami/nginx
```

open browser with your local IP url:
(you can check docker machine ip with command ```docker-machine ls```)

```
http://192.168.99.100
https://192.168.99.100
```

1.6. Basic Commands

```
docker-machine ls
docker-machine restart dockerLab
docker-machine stop dockerLab
docker-machine start dockerLab
```

## 2. Map & Volume

2.1. Setup file sharing on docker option to current directory before operate / Apply & Restart
