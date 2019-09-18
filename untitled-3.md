# Docker Command



Docker is a platform or ecosystem around creating and running containers

Image: single file with all the config and deps required to run a program

Container: Instance of a image. Runs a program

Docker Client\(Docker CLI\):  

```text
$ docker-machine ls
NAME      ACTIVE   DRIVER       STATE   URL   SWARM   DOCKER    ERRORS
default   -        virtualbox   Saved                 Unknown

$ docker-machine restart

$ docker-machine env

$ docker-machine stop

$ docker-machine ip default

sudo -i     

docker volume create postgres_database
docker volume ls

```

### remove docker container and images

docker rm $\(docker ps -a -q\) 

docker rmi $\(docker images -q\)

```text
# 啟動 Docker 容器
docker run -it tensorflow/tensorflow bash
加上 -it 參數代表在執行 Docker 虛擬容器環境時，開啟虛擬終端機
```

### docker run -d

-d :daemon which means that the docker container would run in the background completely detached from your current shell.在背景執行。在terminal中不會看到有東西，在docker logs裡面會看到有東西在跑。有些文章把它翻譯成守護狀態。

### docker top \[container\_id\]

秀出 Container 正在執行的 process

### docker stats \[container\_id\]

顯示容器使用的系統資源  
\[CONTAINER\]：以短格式顯示容器的 ID。   
\[CPU %\]：CPU 的使用情況。   
\[MEM USAGE / LIMIT\]：當前使用的記憶體和最大可以使用的記憶體。  
\[MEM %\]：以百分比的形式顯示記憶體使用情況。   
\[NET I/O\]：網路 I/O 資料。  
\[BLOCK I/O\]：磁碟 I/O 資料。  
\[PIDS\]：PID 號。

### docker stats --no-stream  \[container\_id\]

如果不想持續的監控容器使用資源的情況，可以通過 –no-stream 選項只輸出當前的狀態

