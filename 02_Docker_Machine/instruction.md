# Workshop 2: Docker Machine

## 1. Install Docker Machine
normally Docker Machine ins installes along with Docker for Mac, Docker for Windows, or Docker Toolbox.
That mean you dont't need to install again.

### 1.1. Check the installation by displaying the Machine version:

```
docker-machine version
```
for Ununtu install ```docker-macine``` command following by [Install Machine directly](https://docs.docker.com/machine/install-machine/)

### 1.3. Create machine

```
docker-machine create --driver=virtualbox --virtualbox-memory=600 dockerLab
```

### 1.4. ssh to docker machine

```
docker-machine ssh dockerLab
```

### 1.5. Repeat Step 4 and Step 5 from Workshop 1

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

### 1.6. Basic Commands

```
docker-machine ls
docker-machine restart dockerLab
docker-machine stop dockerLab
docker-machine start dockerLab
```

## 2. Map & Volume
create folder call ```LabShare``` in same path of ```Automate-Development-Workshop``` and copy ```share``` folder into it

### Folder structure:

```
│
├── Automate-Development-Workshop
│   ├── 01_Download_Install_Docker
│   │   ├── instruction.md
│   ├── 02_Docker_Machine
│   │   ├── instruction.md
│   │   ├── source
│   │   │   ├── index.html
├── GitFlow
├── LabShare
│   ├── source
│   │   ├── index.html
```

### 2.1. Setup file sharing

- open VirtualBox and setup file sharing
Settings->Shared Folders->Adds new shared folder call ```LabShare``` and browse to directory above step
	- [x] Auto-Mount
	- [x] Make Permanent
	
- restart VirtualBox by command:

```
docker-machine restart dockerLab
```

### 2.2 SSH to docker machine

```
docker-machine ssh dockerLab
ls -l /LabShare/
```

you will see result like this

```
docker@dockerLab:~$ ls -l /LabShare/
total 0
drwxrwxrwx    1 docker   staff          102 Nov  4 01:57 source/
```

### 2.3 Run docker 
run docker for nginx web server with map file index.html by command:

```
docker run -dt --name nginxtest -v /LabShare/source:/opt/bitnami/nginx/html:ro -p 80:8080 -p 443:8443 bitnami/nginx
```

- open browser with url: ```http://192.168.99.100 https://192.168.99.100```
- try to change content in ```index.html``` on your machine
- refresh browser again 


### 2.4 7 Stop container and remove from system by command:

```
docker stop nginxtest
docker rm nginxtest
```
