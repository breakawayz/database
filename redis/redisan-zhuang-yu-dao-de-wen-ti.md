一、You need tcl 8.5 or newer in order to run the Redis test

wget [http://downloads.sourceforge.net/tcl/tcl8.6.1-src.tar.gz](http://downloads.sourceforge.net/tcl/tcl8.6.1-src.tar.gz)

1. sudo tar xzvf tcl8.6.1-src.tar.gz  -C /usr/local/  
2. cd  /usr/local/tcl8.6.1/unix/  
3. sudo ./configure  
4. sudo make  
5. sudo make install  \

二、ruby模块

a. 离线安装rubygems[下载地址](https://rubygems.org/pages/download)

在本文档中下载的版本为rubygems-2.6.6.tgz

```
tar zxvf rubygems-2.6.6.tgz

cd rubygems-2.6.6

ruby setup.rb
```

b. 安装redis模块[下载地址](https://rubygems.org/gems/redis/versions/3.3.1)

使用gem命令安装：

```
gem install -l redis-3.3.1.gem
```



