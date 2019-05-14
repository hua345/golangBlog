#### 1. 拉取goalng环境镜像
```
docker pull golang

[root@dockerMaster ~]# docker run golang:latest go version
go version go1.12.5 linux/amd64
```
#### 2. 主机安装
```
go get -u github.com/Go-zh/tour
```
#### dockerFile
```
FROM golang:latest

MAINTAINER chenjianhua 2290910211@qq.com

WORKDIR $GOPATH/src/github.com/Go-zh/tour
ADD $GOPATH/src/golang.org $GOPATH/src/golang.org
ADD $GOPATH/src/github.com/Go-zh $GOPATH/src/github.com/Go-zh
RUN go build

EXPOSE 3999

ENTRYPOINT ["./tour"]
```
