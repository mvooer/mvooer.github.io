---
title: Hexo 安装,配置,部署
date: 2017-08-01 16:46:51
tags:
- blog
- hexo
- pages
---

## 环境 (Windows)

- [Git](https://git-for-windows.github.io/)
    - 推荐使用 `Git Bash` 作为命令行
- [Node.js](https://nodejs.org/zh-cn/)
    - 一路 `next`

## 配置 `npm`

- 墙内推荐 `cnpm` 或者你用 `taobao` 都可以
    - `npm config set registry "https://r.cnpmjs.org/"`
    - `npm config set registry "https://registry.npm.taobao.org/"`
- 如果有点追求?的同学
    - `npm config set proxy http://server:port`
    - `npm config set https-proxy http://server:port`

## 安装和配置 `hexo`

- `npm install hexo-cli -g` 安装 `hexo`
-  `cd` 存放Blog的目录下,直接运行 `hexo init` ,或者 `hexo init <folder>`
- 接下来配置,具体请看[官方文档](https://hexo.io/zh-cn/docs/configuration.html)

## 配置 `git`

- `git config --global user.name "你的名字或昵称"`
- `git config --global user.email "你的邮箱"`
- `ssh-keygen -t rsa -C "你的邮箱" -f name`
- `ssh key` 可以多用,如果没有特殊情况,一般同用一个就可以
- 如果你想同步多个 `pages` ,比如 `github` 和 `oschina` (码云) 请参考
    - `http://git.mydoc.io/?t=153707`
- 想学习 `git` 推荐 `pro git` 或者参考码云或Coding的文档 也可以去看廖雪峰的Git教程

## 同步到 `pages`

- 主要是部署,参考`https://hexo.io/zh-cn/docs/deployment.html`
- 安装 hexo-deployer-git `npm install hexo-deployer-git --save`
- 配置 `type` 和 `repo` ,注意 `yml` 的语法
- ```
  deploy:
  type: git
  repo: <repository url>
  branch: [branch]
  message: [message]
  ```

## Thanks

- 参考
    - https://hexo.io/zh-cn/docs/
    - http://git.mydoc.io/