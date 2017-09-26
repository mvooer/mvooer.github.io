---
title: SSL 证书食用指南
date: 2017-08-17 13:08:46
tags:
 - ssl
 - https
 - cert
---

## SSL 证书类型

![SSl 证书类型](/img/cert-1.png)
SSL 证书按大类一般可分为 `DV` SSL `OV` SSL `EV` SSL 证书  
有的也会叫做域名型、企业型、增强型证书，不同的厂商叫法可能有所不同，但差别不大。
<!--more-->
### `DV` Domain Validation SSL

证书颁布机构只对域名的所有者进行在线检查，通常是验证域名下某个指定文件的内容，或者验证与域名相关的某条 TXT 记录

### `OV` Organization Validation SSL

需要购买者提交组织机构资料和单位授权信等在官方注册的凭证，证书颁发机构在签发 SSL 证书前不仅仅要检验域名所有权，还必须对这些资料的真实合法性进行多方查验，只有通过验证的才能颁发 SSL 证书。

### `EV` Extended Validation SSL

与`OV`相比 验证流程更加具体详细，验证步骤更多，这样一来证书所绑定的网站就更加的可靠、可信。它跟普通 SSL 证书的区别也是明显的，安全浏览器的地址栏变绿，如果是不受信的 SSL 证书则拒绝显示，如果是钓鱼网站，地址栏则会变成红色，以警示用户。

## 食用方法

### 生成 `CSR`

`https://csr.chinassl.net/generator-csr.html`  
`CSR` 是 `Cerificate Signing Request` 的英文缩写，即证书请求文件，也就是证书申请者在申请数字证书时由 `CSP`(加密服务提供者) 在生成私钥 Private Key 的同时也生成证书请求文件 CSR，证书申请者只需要把 CSR 文件提交给证书颁发机构后，证书颁发机构使用其根证书私钥签名就生成了证书公钥文件，也就是颁发给用户的 SSL 证书。

### 申请或购买

推荐
- **Let's Encrypt**
    - Free
- Comodo PositiveSSL
    - 1 year 9 $

### 获取证书信息 及 下载中间证书

`https://www.myssl.cn/tools/downloadchain.html`

### 部署

新建文件 `ssl.crt`（证书文件）并用记事本打开。同样方法打开下载的中间证书和根证书，然后按下列顺序在 `ssl.crt` 中排列并保存：申请得到的证书 crt \ 中间证书 crt \ 根证书 crt。  完整 KEY：新建文件 ssl.key（证书的 KEY 文件）并用记事本打开，将第一步申请到的 CSR 带的 KEY 完整复制进去并保存。