一、下载

二、修改参数

修改配置文件：`config/elasticsearch.yml`

```
# 修改一下ES的监听地址，这样别的机器也可以访问
```

`network.host: 0.0.0.0`

```
# 默认的就好
```

三错误处理：

ERROR: bootstrap checks failed

max file descriptors \[4096\] for elasticsearch process likely too low, increase to at least \[65536\]

修改vi /etc/security/limits.conf

\* soft nofile 65536

\* hard nofile 131072

\* soft nproc 2048

\* hard nproc 4096



max number of threads \[1024\] for user \[es\] likely too low, increase to at least \[2048\]

原因：无法创建本地线程问题,用户最大可创建线程数太小

