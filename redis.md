一、下载redis-4.0.2.tar.gz 

`$ tar zxf redis-4.0.2.tar.gz `

`$ make`

`$ make test`

二、安装中出现问题，请参考redis安装遇到的问题

三、新增配置文件

在redis-4.0.2新增文件夹redis-cluster、

分别新加7000 7001 7002

`$ mkdir 7000 7001 7002`

在7000文件文件夹下新增redis.conf文件，内容如下



`port 7000`

`#默认ip为127.0.0.1，需要改为其他节点机器可访问的ip，否则创建集群时无法访问对应的端口，无法创建集群，注意该ip物理网卡ip，其他的没有用`

`bind 192.168.0.105`

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

`                `

四、其他目录和服务器重复以上操作

五、启动

`$ for((i=0;i<=2;i++));  do src/redis-server redis-cluster/700$i/redis.conf;done`

六、创建集群

`$ src/redis-trib.rb create --replicas 1 192.168.0.105:7000 192.168.0.105:7001 192.168.0.191:7000 192.168.0.191:7001 192.168.0.105:7002 192.168.0.191:7002`

7、关闭节点

`$ pkill redis`

8、重建集群

首先关闭节点，删除cluster-config-file和aop文件，然后启动节点，执行`src/redis-trib.rb create创建节点`

