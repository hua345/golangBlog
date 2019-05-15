[syncthing](https://github.com/syncthing/syncthing)

> Syncthing is a continuous file synchronization program. It synchronizes files between two or more computers. 

#### Linux 编译安装
```
# This should output "go version go1.12" or higher.
$ go version

# Pick a place for your Syncthing source.
$ mkdir -p ~/dev
$ cd ~/dev

# Grab the code.
$ git clone https://github.com/syncthing/syncthing.git

# Now we have the source. Time to build!
$ cd syncthing

# You should be inside ~/dev/syncthing right now.
$ go run build.go
```
#### windows编译安装
```
# This should output "go version go1.12" or higher.
> go version

# Grab the code.
> git clone https://github.com/syncthing/syncthing.git

# Now we have the source. Time to build!
> cd syncthing
> go run build.go
```
