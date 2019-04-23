#### Vendor
> `vendor`机制就是在项目中加入了vendor文件夹，用于存放依赖，这样就可以将不同项目的依赖隔离开。
当使用`go run`或者`go build`命令时，会首先从当前路径下的`vendor`文件夹中查找依赖，如果`vendor`不存在，才会从`GOPATH`中查找依赖。
然而我们安装依赖通常使用`go get`或者`go install`命令，这两个命令依旧会把依赖安装到`GOPATH`路径下。

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
