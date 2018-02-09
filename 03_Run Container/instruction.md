# Workshop 3: Run Container


## 1 Interactive NODEJS

### 1.1 copy content in ```source``` to ```LabShare``` 

```
│
├── Automate-Development-Workshop
│   ├── 01_Download_Install_Docker
│   │   ├── instruction.md
│   ├── 02_Docker_Machine
│   │   ├── instruction.md
│   ├── 03_Run Container
│   │   ├── instruction.md
│   │   ├── source
│   │   │   ├── hello.js
│   │   │   ├── mainlite.py
├── GitFlow
├── LabShare
│   ├── source
│   │   │   ├── hello.js
│   │   │   ├── mainlite.py
```

### 1.2 run docker on interactive mode with command

```
docker-machine ssh dockerLab
cd /LabShare/source

docker run  -i -t --rm --name nodejs -p 3000:3000 \
nextgensoft/alpine-web:latest node hello.js
```

> #### Result        
> Server running at http://0.0.0.0:3000/

### 1.3 open browser with your local IP url
(you can check docker machine ip with command ```docker-machine ls``` on your physical machine)

```
http://192.168.99.100:3000
```

> #### Result        
> Hello World Container Docker for Nodejs


### 1.4 open another session and press command: ```docker ps```

> #### Result 

```
CONTAINER ID        IMAGE                           COMMAND             CREATED             STATUS              PORTS                    NAMES
7ea309394f49        nextgensoft/alpine-web:latest   "node hello.js"     3 minutes ago       Up 3 minutes        0.0.0.0:3000->3000/tcp   nodejs
```

### 1.5 Terminate container with command

```
docker stop nodejs
```

or with option "--rm" so it will remove all container after finished work

```
docker stop --rm nodejs
```


## 2. BOT LINE Notify

### 2.1 get line token from ```http://notify-bot.line.me```

### 2.1 run docker on interactive mode with command
place ```<LINE TOKEN>``` with your token

```
docker run -it --rm --name linebot -e TITLE="Line BOT" \
-e "TOKEN=<LINE TOKEN>" \
-e "URL=https://iapi.bot.or.th/Stat/Stat-ReferenceRate/DAILY_REF_RATE_V1/?" \
-e "KEY=U9G1L457H6DCugT7VmBaEacbHV9RX0PySO05cYaGsm" \
nextgensoft/linenotify:latest
```

## 3. Detach NODEJS
### 3.1 run docker on detach mode with command

```
docker run -d -t --name nodejs -p 3000:3000 \
nextgensoft/alpine-web:latest node hello.js
```

### 3.2 open browser with url

```
http://<ip address of docker>:3000
```

### 3.3 access shell to container with command

```
docker exec -i -t nodejs sh
exit
```

### 3.4 use command

```
docker ps
```
> #### Result:
```
CONTAINER ID        IMAGE                        COMMAND             CREATED             STATUS              PORTS                    NAMES
e0790d46c800        nextgensoft/alpine-web:latest   "node hello.js"     6 seconds ago       Up 5 seconds        0.0.0.0:3000->3000/tcp   nodejs
```

### 3.5 Try to stop/start docker with command

```
docker stop nodejs
docker ps -a
docker start nodejs
```

### 3.6 After finished to stop container. We will remove docker container with command

```
docker rm nodejs
```

## 4. Detach PYTHON

### 4.1 run docker on detach mode with command

```
docker run  -d -t --name python -p 5000:5000 \
labdocker/cluster:webservicelite
```

### 4.2 open browser with url

```
http://<ip address of docker>:5000
```

### 4.3 access shell to container with command

```
docker exec -i -t python sh
```

### 4.4 Stop container and cleanup by command

```
docker stop python
docker rm python
```

