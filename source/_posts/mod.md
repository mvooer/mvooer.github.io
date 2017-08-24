---
title: 魔改 填坑记
date: 2017-08-08 07:25:46
tags:
- linux
- bt
- centos
- debian
- bbr
---

## 基础环境

### 宝塔

[BT](https://bt.cn)

### HTTPS

`http`301跳转`https`
```nginx
server {
listen 80;
server_name name.com;
return 301 https://name.com$request_uri;
}
```

### 伪静态

```nginx
         location / {
            try_files $uri $uri/ /index.php$is_args$args;
        } 
```
然后重启`nginx`

### 常用

```shell
service bt restart # stop start 
cat /www/server/panel/data/port.pl # 查看面板端口
cat /www/server/panel/default.pl #查看默认密码
rm -f /www/server/panel/data/*.login #清除登录限制
/www/server/php/56/etc/php.ini # php.ini 位置
```


---------------------


## 前端


```shell
git clone https://github.com/esdeathlove/ss-panel-v3-mod.git tmp -b new_master && mv tmp/.git . && rm -rf tmp && git reset --hard
php composer.phar install
chown -R root:root *
chmod -R 777 *
chown -R www:www storage
chattr -i .user.ini
mv .user.ini public
cd public
chattr +i .user.ini
```

配置,重点是 数据库, 邮件, 邮箱验证码  
```shell
cp config/.config.php.example config/.config.php
nano config/.config.php
```
下载网站目录SQL文件夹里的`glzjin_all.sql`然后导入数据库  

添加管理员账户,定时任务  
```shell
php -n xcat createAdmin #php xcat resetTraffic
php xcat syncusers
crontab -e  
# 按键盘 Insert 添加
## 30 22 * * * php /www/wwwroot/website.org/xcat sendDiaryMail
*/1 * * * * php /www/wwwroot/website.org/xcat synclogin
## */1 * * * * php /www/wwwroot/website.org/xcat syncvpn
0 0 * * * php -n /www/wwwroot/website.org/xcat dailyjob
*/1 * * * * php /www/wwwroot/website.org/xcat checkjob
*/1 * * * * php -n /www/wwwroot/website.org/xcat syncnas
# 最后按键盘 Insert Esc :wq 退出并保存  
```


------------------------


## 后端

```shell
yum -y groupinstall "Development Tools" && yum -y install wget && wget https://github.com/jedisct1/libsodium/releases/download/1.0.13/libsodium-1.0.13.tar.gz && tar xf libsodium-1.0.13.tar.gz && cd libsodium-1.0.13 && ./configure && make -j2 && make install && echo /usr/local/lib > /etc/ld.so.conf.d/usr_local_lib.conf && ldconfig && rm -rf /root/libsodium-1.0.11.tar.gz && cd /root
git clone -b manyuser https://github.com/esdeathlove/shadowsocks.git
cd shadowsocks
yum -y install python-devel && yum -y install libffi-devel && yum -y install openssl-devel
pip install -r requirements.txt # Debian pip install cymysql
cp apiconfig.py userapiconfig.py
cp config.json user-config.json
service iptables stop
chkconfig iptables off # 重启后永久关闭 iptabls 不要卸载.. #   rpm -e epel-release-6-8.noarch
```


----------------------


## 优化

### TFO

```
服务端要启用 TFO:
1. 确认服务器内核 > 3.7
2. 确认内核选项 net.ipv4.tcp_fastopen 为 3.
3. user-config.json 里 fast_open 需要为 true.
```


--------------------


## 感谢 (参考)

- https://lala.im/88.html
- https://91vps.club/2017/06/08/ss-panel-1/
- http://xu62011.cn/archives/430
- https://moeclub.org/2017/03/08/14/
- https://www.91yun.co/archives/795


----------------------------


## 拜谢
- orvice
- esdeathlove
- glzjin


---------------------------------


## 怀念
- breakwa11
- clowwindy