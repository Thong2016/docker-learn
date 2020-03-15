# docker学习笔记-docker常用命令

# docker容器信息

查看docker容器版本:

```shell
docker --version
docker version
```

查看docker容器信息:

```shell
docker info
```

查看docker容器帮助信息:

```shell
docker --help
docker help
```

# docker镜像相关命令

查看镜像:

```shell
#列出本地images
docker image list
#包含中间映像层
docker image list -a

docker image ls
docker image ls -a

docker images
docker images -a

#只显示镜像ID
docker images -q

#含中间映像层
docker images -qa

#显示DIGEST列
docker images --digests
```

镜像搜索:

```shell
#搜索仓库mysql镜像
docker search mysql

#显示镜像完整的描述信息
docker search --no-trunc mysql

#只显示官方镜像
 docker search --filter is-official=true mysql
 
 #只starts>=600的镜像
 docker search --filter=stars=600 mysql
```

镜像下载:

```shell
#下载mysql最新镜像, 相当于docker pull mysql:latest
docker pull mysql

#下载仓库中所有mysql镜像
docker pull -a mysql

#下载私人仓库镜像
docker pull tanghong/mysql
```

删除镜像:

```shell
#根据image id删除,只加image id的前缀也可以,跟其他image能够区分开就可以删除成功
docker image rm 380b4e2cbe72
docker rmi 380b4e2cbe72

docker image rm mysql
docker rmi mysql

#强制删除,即使该镜像有容器在运行
docker rmi -f mysql

#删除全部镜像
docker rmi $(docker images -q)
```

镜像构建:

```shell
#.表示加载当前目录下的Dockerfile文件
docker build -t tanghong163/hello-world .
```

