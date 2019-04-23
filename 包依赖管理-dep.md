#### 参考
- [Golang环境安装和依赖管理](https://www.jianshu.com/p/80b52e054c35)
#### Vendor
> `Golang1.5`加入了一个试验性的`vendor`文件夹机制`(vendor：供应商/小贩)`。
从`Golang1.6`正式开启这个功能。`vendor`机制就是在项目中加入了vendor文件夹，用于存放依赖，这样就可以将不同项目的依赖隔离开。
当使用`go run`或者`go build`命令时，会首先从当前路径下的`vendor`文件夹中查找依赖，如果`vendor`不存在，才会从`GOPATH`中查找依赖。
然而我们安装依赖通常使用`go get`或者`go install`命令，这两个命令依旧会把依赖安装到`GOPATH`路径下。
#### go mod/Go1.11以后
> `Golang 1.11` 开始， 实验性出现了可以不用定义`GOPATH`的功能，且官方有`go mod`支持。`Golang 1.12`更是将此特征正式化。

现在用 Golang1.12 进行
#### 包管理工具dep
`Vendor`只是go官方提供的一个机制，但是包管理的问题依然没有解决，并且也没有对依赖进行版本管理。如果要实现上述的功能，还需要借助包管理工具。

https://github.com/golang/go/wiki/PackageManagementTools
https://github.com/golang/dep

```
go get -u github.com/golang/dep/cmd/dep
```
```
go get github.com/tools/godep

$ godep help
Godep is a tool for managing Go package dependencies.

Usage:

        godep command [arguments]

The commands are:

    save     list and copy dependencies into Godeps
    go       run the go tool with saved dependencies
    get      download and install packages with specified dependencies
    path     print GOPATH for dependency code
    restore  check out listed dependency versions in GOPATH
    update   update selected packages or the go version
    diff     shows the diff between current and previously saved set of dependencies
    version  show version info

Use "godep help [command]" for more information about a command.
```
