#### 下载`protobuf`的编译器`protoc`
```
https://github.com/protocolbuffers/protobuf/releases
```
下载: [protoc-xxx-win64.zip](https://github.com/protocolbuffers/protobuf/releases)
解压，把bin目录下的`protoc.exe`复制到`GOPATH/bin`下，`GOPATH/bin`加入环境变量。

#### 安装golang编译插件`protoc-gen-go`
```
go get -u github.com/golang/protobuf/protoc-gen-go
```
如果成功，会在`GOPATH/bin`下生成`protoc-gen-go.exe`文件
