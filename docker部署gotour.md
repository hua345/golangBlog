#### 1. 拉取goalng环境镜像
```
docker pull golang

[root@dockerMaster ~]# docker run golang:latest go version
go version go1.12.5 linux/amd64
```
#### 2. 主机安装
```
# go get -u github.com/Go-zh/tour

# ll $GOPATH/bin/tour
tour
```
#### 编辑`Dockerfile`
```dockerfile
FROM golang:latest

MAINTAINER chenjianhua 2290910211@qq.com

RUN mkdir /app
WORKDIR /app
COPY $GOPATH/bin/tour /app

EXPOSE 3999

ENTRYPOINT ["./tour"]
```
>  WORKDIR
    WORKDIR 用来切换工作目录的。Docker 默认的工作目录是/，只有 RUN 能执行 cd 命令切换目录，而且还只作用在当下下的 RUN，也就是说每一个 RUN 都是独立进行的。如果想让其他指令在指定的目录下执行，就得靠 WORKDIR。WORKDIR 动作的目录改变是持久的，不用每个指令前都使用一次 WORKDIR。


> COPY
    COPY 将文件从路径 <src> 复制添加到容器内部路径 <dest>。
    <src> 必须是想对于源文件夹的一个文件或目录，也可以是一个远程的url，<dest> 是目标容器中的绝对路径。
    所有的新文件和文件夹都会创建UID 和 GID 。事实上如果 <src> 是一个远程文件URL，那么目标文件的权限将会是600。
#### 从`Dockerfile`构建镜像
```
docker build -t gotour $GOPATH/src
```
> 后面的`.`,表示当前目录，会从当前目录去找`Dockerfile`文件， 当前目录会被上传到docker进程作为构建上下文目录， 只有构建上下文目录的文件才可以被`ADD`或者`COPY`到镜像中。
