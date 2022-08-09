---
lng_pair: id_Linux_Downloader
title: 【En】Raspi 4b Rutracker downloader（1）-- Aria2
date: 2022-03-16 11:45:14 +0900
category: guide
tags: [raspberrypi]
img: ":rutracker.png"
---

# 【En】Raspi 4b Rutracker downloader（1）-- Aria2

## Introducer

<!-- outline-start -->

I can go to rutracker !

Lets do a downloader with pi4b

<!-- outline-end -->

## Finding resources(download links)

[Rutracker](https://rutracker.org) is an Russian website, you can download many famous staem games for free by "magment:"

But i found i cannot search for resources, an account is neccessary, and the register enterance is banned

But i found a way(using microsoft edge):

search in edge ```<what you want> website:rutracker.org```

for example, Elder ring: ```Eldern Ring website:rutracker.org```

![Search for ElderRing](:2022-03-16-01.png)

use edge's function to limit results in "retracker.org"

and you'r gonna click it

copy the url of ```Download by magment``` button in the end

## Aria2 Building

```sudo apt install aria2 ```    install

```mkdir -p ~/.config/aria2/```    create a config folder

```sudo ~/.config/aria2/aria2.config```    it might by a new file

write in :
> # run in background
> 
> daemon=true
> 
> # user name
> 
> #rpc-user=user
> 
> # password
> 
> #rpc-passwd=passwd
> 
> # security password, write it down because you'r gonna use it
> 
> rpc-secret=here-password
> 
> #allow rpc
> 
> enable-rpc=true
> 
> #allow all source
> 
> rpc-allow-origin-all=true
> 
> #enable https speed-up
> 
> #rpc-secure=true
> 
> #security pulic key
> 
> #rpc-certificate=/home/pi/.config/aria2/example.crt
> 
> #security private key
> 
> #rpc-private-key=/home/pi/.config/aria2/example.key
> 
> #允许外部访问，false的话只监听本地端口
> 
> rpc-listen-all=true
> 
> #RPC port, 仅当默认端口被占用时修改
> 
> #rpc-listen-port=6800
> 
> #max count can download in same time(count of mission), recommend: 3
> 
> max-concurrent-downloads=5
> 
> #Breakpoint continuation
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
> #download speed limit
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
> #dir to download to , fix to fit your device
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

```touch /home/pi/.config/aria2/aria2.session```   create session file

```aria2c --conf-path=/home/pi/.config/aria2/aria2.config```    check if seccess(run)

i got an error here: ```continue must be either true or false```

but my continue is really true ....

and i tried to replace all ```/home/pi``` by ```~``` , and it solved

idk why.

if your done run ```ps aux|grep aria2``` ,find treads name with "aira2"

you can kill it now, 'cz we'r going to install another thing

```sudo nano /lib/systemd/system/aria.service```

fill in：(fix it to fit your situation)

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

```sudo systemctl enable aria```    auto start

start, stop or restart aira
```sudo systemctl（start、stop、restart） aria```

## use Aria-NG

this is an aria website server, you can manage missions in the browser

```wget https://github.com/mayswind/AriaNg/releases/download/0.4.0/aria-ng-0.4.0.zip -O aira-ng.zip```    download zip

```unzip aira-ng.zip -d aira-ng```    unpack

```sudo mv aira-ng /var/www/html/```    move it to a right dictionary(if you're following steps without thinking, this step cannto be skipped)

```sudo systemctl enable nginx```    start it!!

goto ```http://<ip of raspi>/aira-ng```

may auth failed, let me teach you how to fix it

![认证失败](:2022-03-16-02.png)

AriaNg set -> RPC -> Aria2 RPC key

fill password i let you to write down when you setting up Aria2

![填入秘钥](:2022-03-16-03.png)

that's done!


## Links

[aria2 building](https://blog.csdn.net/kxwinxp/article/details/80288006)

[rutracker](https://rutracker.org)

[知乎的这篇文章](https://zhuanlan.zhihu.com/p/87193566)
