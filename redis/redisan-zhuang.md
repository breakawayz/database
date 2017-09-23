一、下载redis-4.0.2.tar.gz

$ tar zxf redis-4.0.2.tar.gz

$ cd redis-4.0.2

$ make

$ make test

二、安装遇到问题请查询redis安装遇到的问题解决

三、在redis-4.0.2新建redis-cluster文件。然后分别新增7000 7001 7002

$ mkdir 7000 7001 7002

四、配置文件，在7000下新增redis.conf文件。内容如下

`port 7000`

`#默认ip为127.0.0.1，需要改为其他节点机器可访问的ip，否则创建集群时无法访问对应的端口，无法创建集群，该ip为物理网卡ip，其他ip无效`

`bind 192.168.0.191`

`#redis后台运行`

`daemonize yes`

`#pidfile文件对应7000，7001，7002`

`#pidfile /var/run/redis_7000.pid`

`#开启集群，把注释#去掉`

`cluster-enabled yes`

`#集群的配置，配置文件首次启动自动生成 7000，7001，7002          `

`cluster-config-file nodes_7000.conf`

`#请求超时，默认15秒，可自行设置 `

`cluster-node-timeout 10100`

`#aof日志开启，有需要就开启，它会每次写操作都记录一条日志`

`appendonly yes`

五、其他文件夹和节点跟上面一样配置

六、启动

`$ for((i=0;i<=2;i++));  do src/redis-server redis-cluster/700$i/redis.conf;done`

创建集群

`$ src/redis-trib.rb create --replicas 1 192.168.0.105:7000 192.168.0.105:7001 192.168.0.191:7000 192.168.0.191:7001 192.168.0.105:7002 192.168.0.191:7002`

七、重建集群

删除cluster-config-file和aof文件，执行重启和创建集群

