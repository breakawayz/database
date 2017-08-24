配置文件路径 ：/etc/influxdb/influxdb.conf

可以通过以下命令生成默认配置文件：

```
influxd config > default.conf

influx -precision rfc3339
auth-file = "/etc/collectd/auth_file"

 # types.db can be found in a collectd installation or on github:
 # https://github.com/collectd/collectd/blob/master/src/types.db
 #types.db可从上述地址下载到此路径
 typesdb = "/usr/share/collectd/types.db"
 
 show measurements
```

[https://portal.influxdata.com/downloads](https://portal.influxdata.com/downloads)

[https://docs.influxdata.com/influxdb/v1.2/introduction/getting\_started/](https://docs.influxdata.com/influxdb/v1.2/introduction/getting_started/)

[http://www.echojb.com/go/2017/05/23/398209.html](http://www.echojb.com/go/2017/05/23/398209.html)

[https://collectd.org/download.shtml](https://collectd.org/download.shtml)

源码安装

[https://doc.yonyoucloud.com/doc/logstash-best-practice-cn/input/collectd.html](https://doc.yonyoucloud.com/doc/logstash-best-practice-cn/input/collectd.html).

