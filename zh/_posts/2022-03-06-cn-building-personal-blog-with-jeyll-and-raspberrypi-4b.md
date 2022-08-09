---
lng_pair: id_Building_personal_blog_With_Jekyll_And_Raspberrypi_4b
title: 【中】树莓派4b和Jekyll搭建个人博客
date: 2022-03-06 11:45:14 +0900
category: guide
tags: [raspberrypi, jekyll, website]
img: ":jekyll.png"
---

# 【中】树莓派4b和Jekyll搭建个人博客

<!-- outline-start -->
GithubPages太慢了，正好树莓派4b买回来正在吃灰，搭个博客吧。
<!-- outline-end -->

## 选择博客平台

[这里](https://zhuanlan.zhihu.com/p/25280413)有一些博客平台，我看了看，就Jekyll和WordPress比较好，但是WordPress用到SQL，我打算以后再学，所以就用Jekyll了。

## 安装Jekyll
**注意：我的设备是树莓派4b，如果你使用更低版本且完全不会自行百度，请跳过此部分**

### 你需要安装什么（以及如何安装）

- Ruby(Jekyll2 需要版本 >= 1.9.3, Jekyll3 需要版本 >=2)
- RubyGems
- NodeJS
- Python(我使用python3)

[Jekyll Docs](https://jekyllcn.com/docs/)

如果你的系统不是Debain，请参阅[文档（前置安装）](https://jekyllrb.com/docs/installation/) 并选择你的系统

#### 树莓派4b安装步骤:

1.	```sudo apt-get install ruby-full build-essential```
2.	```echo '# Install Ruby Gems to ~/gems' >> ~/.bashrc```
3.	```echo 'export GEM_HOME="$HOME/gems"' >> ~/.bashrc```
4.	```echo 'export PATH="$HOME/gems/bin:$PATH"' >> ~/.bashrc```
5.	```source ~/.bashrc```
6.	```gem install jekyll bundler```

## 创建网站:

### Jekyll开发者

如果你想制作一个Jekyll主题并造福人类(我认为你不是), 运行 ```jekyll new myblog``` 他会在当前目录创建一个名为 `myblog` 的目录，你可以开始表演了。

### 普通玩家

如果你只是简单地搭个博客或者完全不想看见代码的话：

#### 寻找你的主题

在以下链接里寻找合适的主题（部分可能上不去）

- [Github Jekyll Themes](https://github.com/topics/jekyll-theme)
- [Jamstack Themes](https://jamstackthemes.dev/ssg/jekyll/)
- [Jekylltheme.org](http://jekyllthemes.org/)
- [Jekylltheme.io](https://jekyllthemes.io/)
- [Jekyll-theme.com](https://jekyll-themes.com/)

不管你选了什么，最后都应该指向一个主题的Github仓库

点击 `Code`  然后复制 `git link`

![复制这个链接(点击查看图片)](:2022-03-06-01.png)

运行 ```git clone [your theme git link]```

例如我的 'SerialProgrammer': 
 `git clone https://github.com/sharadcodes/jekyll-theme-serial-programmer.git`

进入你的目录: `cd [your theme dir]`

运行 `bundle install` 然后等一会

现在你可以修改 `_config.yml` 来客制化你的网站

你所见的网站上的一切都可以更改（需要会代码，我回头会浅讲一下），但是不要违反LINCENS

运行 `bundle exec jekyll serve` 启动服务器

在浏览器输入 `127.0.0.1:4000` 就可以看见你的网站了！恭喜！

[常见问题-未完成]()

[绑定域名教程-未完成]()
