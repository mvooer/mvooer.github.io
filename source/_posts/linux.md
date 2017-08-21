---
title: Linux 填坑记
date: 2017-08-02 10:49:54
tags:
- linux
- freedom
- note
---

## 常用命令

```shell
nano
apt-get update  # apt-get upgrade
apt-get autoclean atuoremove
```


-------------------------


## Ubuntu/Debian

### 升级内核

如果系统是 64 位，则下载 amd64 的 linux-image 中含有 generic 这个 deb 包  
如果系统是 32 位，则下载 i386 的 linux-image 中含有 generic 这个 deb 包  
安装命令 `dpkg -i name.deb`, 请自行替换你下载好的deb包文件名  
安装完成后 执行 `/usr/sbin/update-grub`, 然后重启vps即可  

### 升级 gcc

#### `add-apt-repository: command not found`  

```
apt-get install python-software-properties
apt-get install software-properties-common
```

#### `GCC`创建文件链接  

- `ln -sf `which gcc-4.9` /usr/bin/gcc`


-------------------------


## Centos

### Centos 6 更换内核

```
wget ftp://ftp.riken.jp/Linux/cern/updates/slc66/i386/RPMS/kernel-firmware-2.6.32-504.el6.noarch.rpm && rpm -Uvh kernel-firmware-2.6.32-504.el6.noarch.rpm
rpm -ivh http://soft.91yun.org/ISO/Linux/CentOS/kernel/kernel-firmware-2.6.32-504.3.3.el6.noarch.rpm
rpm -ivh http://soft.91yun.org/ISO/Linux/CentOS/kernel/kernel-2.6.32-504.3.3.el6.x86_64.rpm --force

```
 `rpm -qa | grep kernel` 如果内核列表有要装的那个版本号就表示OK,然后重启就阔以  `uname -r`  
 `wget --no-check-certificate -qO /tmp/appex.sh "https://raw.githubusercontent.com/0oVicero0/serverSpeeder_Install/master/appex.sh" && bash /tmp/appex.sh 'install'`