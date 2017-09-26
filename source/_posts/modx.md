---
title: 一个魔改魔改版本的说明 
date: 2017-08-08 07:25:46
tags:
 - linux
 - bt
 - centos
 - debian
 - bbr
---
注意：`resources\views\material\admin122` 需要重命名为 `resources\views\material\admin`

<!--more-->
```
cp /usr/share/zoneinfo/Asia/Shanghai /etc/localtime
yum install -y wget
yum -y groupinstall "Development Tools"
wget https://github.com/jedisct1/libsodium/releases/download/1.0.13/libsodium-1.0.13.tar.gz
tar xf libsodium-1.0.13.tar.gz && cd libsodium-1.0.13
./configure && make -j2 && make install
echo /usr/local/lib > /etc/ld.so.conf.d/usr_local_lib.conf
ldconfig

cd /root
yum -y install python-setuptools
easy_install pip
yum install -y git
git clone -b manyuser https://github.com/glzjin/shadowsocks.git
yum -y install python-devel
yum -y install libffi-devel
yum -y install openssl-devel
cd shadowsocks
pip install -r requirements.txt
cp apiconfig.py userapiconfig.py
cp config.json user-config.json
vi userapiconfig.py
```