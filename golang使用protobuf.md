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

#### 编辑hello.proto
```
syntax = "proto3";
package hello.protobuf;

enum BookCategory {
    ComputerScience = 0; //计算机科学
    English = 1; //英语
    Economics = 2; //经济学
}
message Book {
    string name = 1; // 书名
    int32 price = 2; // 价格
    repeated BookCategory category = 3; // 类别
}
```
#### 生成golang文件
```
protoc --go_out=. hello.proto
```

### Protobuf语法
#### 标识符Tags
> 可以看到，消息的定义中，每个字段都有一个唯一的数值型标识符。这些标识符用于标识字段在消息中的二进制格式，使用中的类型不应该随意改动。
需要注意的是，[1-15]内的标识在编码时只占用一个字节，包含标识符和字段类型。[16-2047]之间的标识符占用2个字节。
建议为频繁出现的消息元素使用[1-15]间的标识符

#### 导入定义(import)
可以使用import语句导入使用其它描述文件中声明的类型
```
import "others.proto";
```
`protocol buffer`编译器会在`-I / --proto_path`参数指定的目录中查找导入的文件，如果没有指定该参数，默认在当前目录中查找。
#### 字段规则
- `repeated`：标识字段可以重复任意次，类似数组
- `proto3`不支持`proto2`中的`required`和`optional`
#### 包(Packages)
在.proto文件中使用package声明包名，避免命名冲突。
```
syntax = "proto3";
package hello.protobuf;
...
```
在其他的消息格式定义中可以使用包名+消息名的方式来使用类型，如：
```
syntax = "proto3";
import "hello.proto";

package world.protobuf;

//书店
message BookStore {
    repeated hello.protobuf.Book bookList = 1;
}
```
