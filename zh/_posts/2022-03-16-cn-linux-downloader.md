---
lng_pair: id_Linux_Downloader
title: 【汉】树莓派下载站白嫖Rutracker（1）-- Aria2搭建
date: 2022-03-16 11:45:14 +0900
category: guide
tags: [raspberrypi]
img: ":rutracker.png"
---

# 【汉】树莓派下载站白嫖Rutracker -- Aria2搭建

## 引

<!-- outline-start -->
俄乌大战打了有一段时间了，RUTRACKER我也知道的，只不过一直上不去，所以放弃了

直到今天，我试着在树莓派上进入了rutracker，竟然成功了！

来吧直接开整
<!-- outline-end -->

## 找资源（来看下载站搭建的跳过）

[Rutracker](https://rutracker.org)是个俄国网站，里面全是俄文，看不懂嘛，于是我就装了一个翻译插件

插件是Chrome版本的，树莓派自带的浏览器

接下来发现rutracker不能搜索，需要账号，注册入口封了

网上一通查找，发现一个edge方法：

edge地址栏（上面那个）直接打： ```<你要搜索的> website:rutracker.org```

例如我要找老头环： ```Eldern Ring website:rutracker.org```

![老头环示例（点击查看图片）](:2022-03-16-01.png)

原理是通过edge自带的功能将搜索范围限制在rutracker里

找到以后复制链接到树莓派的浏览器里（vnc）

讲一大堆只有最下面的 ```通过磁力链接下载``` 有用

把他复制下来，备用

## Aria2 搭建

```sudo apt install aria2 ```    安装

```mkdir -p ~/.config/aria2/```    创建配置文件夹，哪里都可以但是最好养成配置文章在.config文件夹的好习惯

```sudo ~/.config/aria2/aria2.config```    应该是一个新文件

写入：(最好不要复制进中文)
> #后台运行
> 
> daemon=true
> 
> #用户名
> 
> #rpc-user=user
> 
> #密码
> 
> #rpc-passwd=passwd
> 
> #设置加密的密钥,注意这里！记住这里你设置的rpc-secret
> 
> rpc-secret=here-password
> 
> #允许rpc
> 
> enable-rpc=true
> 
> #允许所有来源, web界面跨域权限需要
> 
> rpc-allow-origin-all=true
> 
> #是否启用https加密，启用之后要设置公钥,私钥的文件路径
> 
> #rpc-secure=true
> 
> #启用加密设置公钥
> 
> #rpc-certificate=/home/pi/.config/aria2/example.crt
> 
> #启用加密设置私钥
> 
> #rpc-private-key=/home/pi/.config/aria2/example.key
> 
> #允许外部访问，false的话只监听本地端口
> 
> rpc-listen-all=true
> 
> #RPC端口, 仅当默认端口被占用时修改
> 
> #rpc-listen-port=6800
> 
> #最大同时下载数(任务数), 路由建议值: 3
> 
> max-concurrent-downloads=5
> 
> #断点续传
> 
> continue=true
> 
> #同服务器连接数
> 
> max-connection-per-server=5
> 
> #最小文件分片大小, 下载线程数上限取决于能分出多少片, 对于小文件重要
> 
> min-split-size=10M
> 
> #单文件最大线程数, 路由建议值: 5
> 
> split=10
> 
> #下载速度限制
> 
> max-overall-download-limit=0
> 
> #单文件速度限制
> 
> max-download-limit=0
> 
> #上传速度限制
> 
> max-overall-upload-limit=0
> 
> #单文件速度限制
> 
> max-upload-limit=0
> 
> #断开速度过慢的连接
> 
> #lowest-speed-limit=0
> 
> #验证用，需要1.16.1之后的release版本
> 
> #referer=*
> 
> #文件保存路径, 默认为当前启动位置(我的是外置设备，请自行坐相应修改)
> 
> dir=/media/piusb/TDDOWNLOAD
> 
> #文件缓存, 使用内置的文件缓存, 如果你不相信Linux内核文件缓存和磁盘内置缓存时使用,  需要1.16及以上版本
> 
> #disk-cache=0
> 
> #另一种Linux文件缓存方式, 使用前确保您使用的内核支持此选项, 需要1.15及以上版本(?)
> 
> #enable-mmap=true
> 
> #文件预分配, 能有效降低文件碎片, 提高磁盘性能. 缺点是预分配时间较长
> 
> #所需时间 none < falloc ? trunc << prealloc, falloc和trunc需要文件系统和内核支持
> 
> file-allocation=prealloc
> 
> #不进行证书校验
> 
> check-certificate=false
> 
> #保存下载会话
> 
> save-session=/home/pi/.config/aria2/aria2.session
> 
> input-file=/home/pi/.config/aria2/aria2.session
> 
> #断电续传
> 
> save-session-interval=60

```touch /home/pi/.config/aria2/aria2.session```   然后创建会话文件

```aria2c --conf-path=/home/pi/.config/aria2/aria2.config```    查看是否配置成功（就开始运行了）

这一步我卡了好久，我遇到的问题是他提示 ```continue must be either true or false```

释义：continue一项必须是true或者false

但是我的continue确实是true啊。。。

后来我尝试从头来过但是把所有的 ```/home/pi``` 换成了 ```~``` 就解决了。。。

不是很能理解。。。

好了的话运行 ```ps aux|grep aria2``` ，此命令是在进程中寻找带有aria2字样的显示

现在可以先kill掉，因为aria运行会一直占据终端，这样你就不能运行接下来的aria-NG了

（装了screen或者装图形系统的忽略，但是要配置开机自启的接着往下看）

```sudo nano /lib/systemd/system/aria.service```

填入：（视情况改）

> [Unit]
> 
> Description=Aria2 Service
> 
> After=network.target
> 
> 
> [Service]
> User=pi
> 
> Type=forking
> 
> ExecStart=/usr/bin/aria2c --conf-path=/home/pi/.config/aria2/aria2.config
> 
> [Install]
> 
> WantedBy=multi-user.target

```sudo systemctl daemon-reload```

```sudo systemctl enable aria```    这一步是开机自启，不要可以忽略

开，关，重启aria
```sudo systemctl（start、stop、restart） aria```

## 配置Aria-NG

这是一个aria的页面服务器（是这么叫吧），可以在浏览器里直观的管理下载任务

```wget https://github.com/mayswind/AriaNg/releases/download/0.4.0/aria-ng-0.4.0.zip -O aira-ng.zip```    下载压缩包

```unzip aira-ng.zip -d aira-ng```    解压

```sudo mv aira-ng /var/www/html/```    移动（如果你什么都不懂，这一步不能省略）

```sudo systemctl enable nginx```    启动！啊哈哈

前往 ```http://<树莓派的ip>/aira-ng``` 摸索摸索可以改中文的

可能会认证失败，我来教你怎么解决

![认证失败（点击查看图片）](:2022-03-16-02.png)

AriaNg 设置 -> RPC -> Aria2 RPC秘钥

填入之前配置Aria2时让你记住的密码

![填入秘钥（点击查看图片）](:2022-03-16-03.png)

完成了！

点击新建就可以下载了！贴入在rutracker复制到的"magment:"打头的链接

注意：下载时不要着急，不要看100%就结束或者把文件拿走！等下载任务自动结束！血与泪的教训！

2022-4-7补充：下载完成可能会在100%卡住，任务不结束，下载速度0，不过在上传。

这是下载bt任务的做种环节，目的是让其他用户下载更快，所以还是最好等他做种完成.

## 后

（2022-4-7）

有人可能会问，迅雷下载更快啊，费这么大劲整这个干什么

第一，最开始买树莓派的时候就听说过可以当做下载站来使用，折腾的快乐

第二，迅雷的吸血鬼行为太可恶了（今天才刚刚知道这件事，就当给你加一个理由吧）

更详细可以阅读：[知乎的这篇文章](https://zhuanlan.zhihu.com/p/87193566)

## 参考资料

[aria2搭建部分](https://blog.csdn.net/kxwinxp/article/details/80288006)

[rutracker](https://rutracker.org)

[知乎的这篇文章](https://zhuanlan.zhihu.com/p/87193566)
