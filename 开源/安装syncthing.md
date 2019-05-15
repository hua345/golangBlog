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
编译后可执行文件`syncthing`在`bin`目录

#### 启动
```
[root@dockerMaster syncthing]# ./bin/syncthing
[monitor] 12:38:31 INFO: Starting syncthing
[start] 12:38:31 INFO: Generating ECDSA key and certificate for syncthing...
[FOWNB] 12:38:31 INFO: syncthing v1.1.4-rc.1-dirty "Erbium Earthworm" (go1.12.5 linux-amd64) root@dockerMaster 2019-05-12 19:17:55 UTC
[FOWNB] 12:38:31 INFO: My ID: FOWNBMZ-3KJSA62-SAJO42H-PVFDGUR-RIZWJ3A-2LMKBRE-4WRUFD7-O3VB5QF
[FOWNB] 12:38:32 INFO: Single thread SHA256 performance is 199 MB/s using crypto/sha256 (195 MB/s using minio/sha256-simd).
[FOWNB] 12:38:32 INFO: Default folder created and/or linked to new config
[FOWNB] 12:38:32 INFO: Default config saved. Edit /root/.config/syncthing/config.xml to taste (with Syncthing stopped) or use the GUI
[FOWNB] 12:38:32 INFO: Hashing performance is 162.40 MB/s
[FOWNB] 12:38:32 INFO: Starting deadlock detector with 20m0s timeout
[FOWNB] 12:38:32 INFO: No stored folder metadata for "default": recalculating
[FOWNB] 12:38:32 INFO: Ready to synchronize "Default Folder" (default) (sendreceive)
[FOWNB] 12:38:32 INFO: Overall send rate is unlimited, receive rate is unlimited
[FOWNB] 12:38:32 INFO: Using discovery server https://discovery-v4.syncthing.net/v2/?nolookup&id=LYXKCHX-VI3NYZR-ALCJBHF-WMZYSPK-QG6QJA3-MPFYMSO-U56GTUK-NA2MIAW
[FOWNB] 12:38:32 INFO: Using discovery server https://discovery-v6.syncthing.net/v2/?nolookup&id=LYXKCHX-VI3NYZR-ALCJBHF-WMZYSPK-QG6QJA3-MPFYMSO-U56GTUK-NA2MIAW
[FOWNB] 12:38:32 INFO: Using discovery server https://discovery.syncthing.net/v2/?noannounce&id=LYXKCHX-VI3NYZR-ALCJBHF-WMZYSPK-QG6QJA3-MPFYMSO-U56GTUK-NA2MIAW
[FOWNB] 12:38:32 INFO: TCP listener ([::]:22000) starting
[FOWNB] 12:38:32 INFO: Relay listener (dynamic+https://relays.syncthing.net/endpoint) starting
[FOWNB] 12:38:32 INFO: Completed initial scan of sendreceive folder "Default Folder" (default)
[FOWNB] 12:38:32 INFO: Anonymous usage reporting is always enabled for candidate releases.
[FOWNB] 12:38:32 INFO: Loading HTTPS certificate: open /root/.config/syncthing/https-cert.pem: no such file or directory
[FOWNB] 12:38:32 INFO: Creating new HTTPS certificate
[FOWNB] 12:38:32 INFO: GUI and API listening on 127.0.0.1:8384
[FOWNB] 12:38:32 INFO: Access the GUI via the following URL: http://127.0.0.1:8384/
```
#### 配置
```
[root@dockerMaster ~]# ls ~/.config/syncthing/
cert.pem  config.xml  https-cert.pem  https-key.pem  index-v0.14.0.db  key.pem

[root@dockerMaster ~]# vi ~/.config/syncthing/config.xml
<configuration version="28">
...
    <gui enabled="true" tls="false" debugging="false">
        <address>127.0.0.1:8384</address>
        <apikey>eTdsTc34JoJktgEMvzadam6pNaLqpQRe</apikey>
        <theme>default</theme>
    </gui>
</configuration>
```
将`127.0.0.1:8384`改为`0.0.0.0:8384`,重启`syncthing`

