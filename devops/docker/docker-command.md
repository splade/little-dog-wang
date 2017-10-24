# Docker 命令

## 停止，删除所有的　Docker container, Docker images

> docker stop $(docker ps -a -q)
docker rm $(docker ps -a -q)
docker rmi $(docker images -q)
docker rm -f $(docker ps -a -q)
docker rm -f -v $(docker ps -a -q)


`docker ps -a -q` 中的 `-q` 仅仅显示　id.　如果提示权限问题, 使用　`sudo`.

容器需要停止之后才能删除, 可以使用　-f (发送 SIGKILL).
爱删除容器的同时需要删除卷, 使用　-v 参数. 

> sudo docker rm -f -v $(docker ps -a -q)

> for f in $(docker ps -a -q) ; do docker rm -f $f ; done

> dstop() { docker stop $(docker ps -a -q); }
alias dstop=dstop


过滤特定名称的容器

> docker rm $(docker ps -a | grep cluster | awk '{print $1;}')
docker rmi $(docker ps -a | grep cluster | awk '{print $3;}')

使用过滤条件

删除所有已经退出的容器 (Exited)
> docker rm $(docker ps -q -f status=exited)

删除所有已经停止的容器 (Stopped)
> docker rm $(docker ps -a -q)

删除所有正在运行的, 停止的容器
> docker stop $(docker ps -a -q)
docker rm $(docker ps -a -q)

删除所有　"none" 镜像

> docker rmi $(docker images | grep "^<none>" | awk '{ print $3 }')

删除所有的 Dangling Images

> sudo docker rmi $(sudo docker images -f "dangling=true" -q)

** 在新版本的 Docker 中 **

删除 "untagged", "none", "dangling" images and containers

> docker system prune

> docker container prune
docker image prune
docker network prune
docker volume prune



