---
layout: post
title: GithubPages搭建个人博客
date: 2022-08-25
category: guide
tags: 
- jekyll
- website
- software
excerpt: "看看GithubPages的搭建，还有Github加速方法"
image: images/headimg/github_pages.png
---


## 为什么使用GithubPages

优点：  
- Github提供服务器和域名，你甚至一分钱不用交  
- 写完之后ctrl+s然后点击推送直接看到结果，炫酷的工作流  

缺点:  
- 写的时候无法预览  
- 出了问题修改后等差不多5分钟才能看见修改生没生效:(

两个缺点可以修复，但略麻烦，以后可能在此文章更新

## Github太慢了

下载 [Watt Toolkit（原Steam++）](https://steampp.net/)

还可以加速Steam(以及steam社区)，GOG，Epic，暴雪战网，pixiv(?)，google的一部分api

火狐浏览器注意，需要按照[官网的教程](http://steampp.net/faq)安装证书并卸载安全模块

## 开始搭建博客

在[这里](https://mhyc.eu.org/zh/2022-03-06-cn-building-personal-blog-with-jeyll-and-raspberrypi-4b#%E5%AF%BB%E6%89%BE%E4%BD%A0%E7%9A%84%E4%B8%BB%E9%A2%98)找一个中意的主题，最终应该来到一个github的仓库页面，(例如我的[jekyll-theme-chirpy](https://github.com/cotes2020/jekyll-theme-chirpy))点击 `fork`

![fork按钮](/images/post/2022-08-25-01.png)

Repository Name 一项填入 `<自己的名字>.github.io`

例如我的github名字叫做 `MHYCWasTaken` ，我就填入 `MHYCWasTaken.github.io`

![fork名](/images/post/2022-08-25-02.png)

完成后来到自己的仓库页面，如果看见有一个小绿勾，代表你的页面已经部署完毕了，可以前往 `https://<你的名字>.github.io` 访问

![小绿勾](/images/post/2022-08-25-03.png)

如果是个小黄点，多刷新几次，如果是个红叉，删除此仓库重试一次

还是不行点击小红叉查看报错并向百度求助

实在不行换一个主题吧，可能这个build有问题

## 添加内容

两种方法奥:)

### 本地修改

你需要如下几个软件：

- Git/GithubDesktop
  - 用于clone和commit和push，githubDesktop更加亲民直观
- VisualStudio Code
  - 注意不是vs，是vs code，用于直观修改markdown以及一键commit push
- Notepad
  - markdown修改器乞丐版

notepad和vs code选装

#### 接下来以GithubDesktop和vs code示范

开启GithubDesktop，登录，点击Clone a repository，复制 `<你的仓库链接>.git` 例如我的 `https://github.com/MHYCWasTaken/MHYCWasTaken.github.io.git` 

等待clone...

完成后可以从本地的克隆目录看见仓库内的文件

进行修改...

完成后在GithubDesktop填写一个commit内容，就是你这一次修改干了什么事情，点击commit

![GithubDesktop的commit](/images/post/2022-08-25-04.png)

点击右上角push

过一会即可看见页面出现了改变

此外你还可以在vscode中点击github按钮，填入commit内容，点击小三角，点击 `commit+push`

![vscode的commit&push](/images/post/2022-08-25-05.png)

可以达到一样的效果

### 在线修改

#### 使用小书童

链接找不到了  
怎么用忘了  
甚至具体什么名字都忘了

...

下一个

#### 使用WebEditor

在浏览器中打开你的仓库

按下句号按键

ta-da！

这是Github自带的在线vscode

怎么使用见上文

:)

## 美化访问方式

我的名字太长了，访问的二级域名更长，我不高兴:(

参见[这篇文章(TODO)](TODO)来获取*永久免费*的.eu.org域名

前往仓库，点击settings，点击Pages

CustomDomain填入你的域名，二级域名也可以，前提是域名是你的/域名拥有者授权

例如我的域名实际上是 `mhyc.eu.org` 但是我可以填写 `blog.mhyc.eu.org` 甚至 `1.1.4.5.1.4.mhyc.eu.org` ，而这个在域名前面的字段就叫做子域名

(即便这样， `.eu.org` 仍是顶级域名，意味着我的 `mhyc.eu.org` 不是二级域名)

2023-1-28:

euorg确实是二级域名，见nic.eu.org的描述：

![nic.eu.org](/images/post/2022-08-25-07.png)

开启你的域名DNS控制台，新建一个记录，记录类型填写CNAME，主机记录视情况填写:

例如我希望直接使用 `mhyc.eu.org` ，填写 `@`
我希望使用 `blog.mhyc.eu.org` ，填写 `blog`
使用 `1.1.4.5.1.4.mhyc.eu.org` ，填写 `1.1.4.5.1.4`
我希望不论什么前缀(二级域名)都可以访问，填写 `*`

域名（记录（指向哪里））填写你原来访问的域名( `https://MHYCWasTaken.github.io` )

保存这个记录

回到github，稍等一会应该可以看见绿色的 `DNS Check successful` 的字样

现在可以使用你的域名访问了

还可以在下面勾上 `Enforce HTTPS` 这样Github会送你一个ssl证书，访问时可以用 `https://<domain>` 来访问，浏览器也会给出护盾的标志表示网站安全

![ssl效果](/images/post/2022-08-25-06.png)

可是你发现使用原来的域名也可以访问，那在github检查dns有什么用吗

实践出真知，于是你把github的域名解绑试了一下

好像。。。还是没区别？？

好吧，github绑定域名之后使用原来的.github.io访问会把你直接带到新的域名去，仔细看，搜索框里是不是变成了优雅的 `1.1.4.5.1.4.mhyc.eu.org` ？



(doge)

## 参考资料

[Watt Toolkit（原Steam++）](https://steampp.net/)  
[官网的教程](http://steampp.net/faq)

## 解决缺点

使用本地修改方案并本地搭建服务来达到本地实时渲染显示的效果

参考 [这里](https://mhyc.eu.org/zh/2022-03-06-cn-building-personal-blog-with-jeyll-and-raspberrypi-4b#%E5%AF%BB%E6%89%BE%E4%BD%A0%E7%9A%84%E4%B8%BB%E9%A2%98)