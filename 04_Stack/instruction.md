## 1. Setup boot2docker

Boot2Docker is a lightweight Linux distribution made specifically to run Docker containers. It runs completely from RAM, is a small ~38MB download and boots in ~5s (YMMV).

```
uname -a

### espect result
Linux dockerLab 4.4.111-boot2docker #1 SMP Thu Jan 11 16:25:31 UTC 2018 x86_64 GNU/Linux
```

### 1.1 Install bash on boot2docker

answer the question in `{xxx}`

```
tce

tce-ab - Tiny Core Extension: Application Browser

S)earch P)rovides K)eywords or Q)uit: {s}

Enter starting chars of desired extension, e.g. abi: {bash}

tce - Tiny Core Extension browser

	 1. bash-completion.tcz
	 2. bash-dev.tcz
	 3. bash.tcz

Enter selection ( 1 - 3 ) or (q)uit: {3}


Copying-policy: GPL
Size:		520KB
Extension_by:   juanito
Tags:	        shell
Comments:       Bash is a shell for Linux
		This extension is PPI compatible
                ----------
Change-log:     2012/11/09 first version
                2013/10/12 updated 4.0 -> 4.2
                2014/09/22 updated 4.2 -> 4.3 patches 0-25
                2015/07/29 updated 4.3 -> 4.3.30 patches -> 39
                2015/09/27 adjusted startup script
Current:	2016/11/17 updated 4.3.30 -> 4.4

{q}

A)bout I)nstall O)nDemand D)epends T)ree F)iles siZ)e L)ist S)earch P)rovides K)eywords or Q)uit: {i}

A)bout I)nstall O)nDemand D)epends T)ree F)iles siZ)e L)ist S)earch P)rovides K)eywords or Q)uit: {q}
```

### 1.2 Install docker-compose on boot2docker

```
sudo curl -L https://github.com/docker/compose/releases/download/1.18.0/docker-compose-`uname -s`-`uname -m` -o /usr/local/bin/docker-compose
sudo chmod +x /usr/local/bin/docker-compose

docker-compose --version
```

## 2 Seup Stack

### 2.1 Run composer update using composer image

copy `./source` to ``LabShare` then

```
cd /LabShare/yii2_advance
cd www
git clone https://github.com/yiisoft/yii2-app-advanced.git .
cd ..
docker-compose up -d
```

(take a coffee)

```
docker-compose run --rm php ./init
docker-compose run --rm php composer --version
docker-compose run --rm php composer install (take a nap)
docker-compose run --rm php ./yii migrate
```

```
http://ng-frontend/
http://ng-backend/
http://ng-pma:8000/
```

```
docker exec -it 4ed7a8e4c1ba mysql -u root -p
```

```
#!/bin/bash

mysql -u root -e "grant all on *.* to '$MYSQL_USER'@'%' identified by '${MYSQL_PASSWORD}' with grant option; flush privileges;"
```

and its use in Dockerfile:

```
# copy the file into the container
COPY fix-permissions.sh /docker-entrypoint-initdb.d/fix-permissions.sh

# make it executable
RUN chmod +x /docker-entrypoint-initdb.d/fix-permissions.sh
```
