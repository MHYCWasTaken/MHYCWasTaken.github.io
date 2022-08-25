<!-- readme -->

<!-- outline-start -->

关于树莓派新手遇到的问题，包括红灯长亮，系统烧录，后续使用

<!-- outline-end -->

（网站建成之后按照log补的）

## 02-15

树莓派到货，烧录系统

查了一圈，方法各不相同，主要是需要很多软件

```
我给大家整理了一套最简约最方便的软件
```
![树莓派使用软件套餐](:2022-02-17-01.png)
```
从左到右，从上到下是：

1. ParagonExtFS

2. 一个存放各种系统文件的文件夹

3. DiskGenius

4. BalenaEtcher

5. Putty

6. VNCViewer

可以先全部安装，也可以等到用时安装，使用时我会讲解
```

首先，下载BalenaEtcher，这是向sd卡烧录系统的软件。

接下来，前往[树莓派官网](https://raspberrypi.org)下载你需要的系统

也可以尝试直接点击下面的链接下载（第一次使用这个功能，如果有问题，请联系MHYC133@outlook.com告知)

[树莓派系统--raspios--无图形化仅命令行（lite）(出于服务器带宽考虑，此链接已经无法下载)](/assets/files/uploads/2022-01-28-raspios-bullseye-armhf-lite.zip)

[树莓派系统--raspios--图形化系统(出于服务器带宽考虑，此链接已经无法下载)](/assets/files/uploads/2022-01-28-raspios-bullseye-armhf.zip)

安装DiskGenius，删除sd卡所有分区（选中分区按delete或者右键删除分区）

新建分区（FAT32，最大分区）

保存更改

格式化

重新插入sd卡（是为了让电脑重新识别一下，忘了也没关系）

打开BalenaEtcher，进行烧录(记得先解压得到iso文件)

网上有说一些别的软件，但是都没BalenaEtcher稳定

## 02-16

焯炸了

突然的，一夜之间，树莓派炸了，重启之后只亮红灯，绿灯闪几下就灭了

找了一天问题

## 02-17

ok解决了，来看看我找到了些什么

首先，是树莓派官网论坛的[帖子](https://forums.raspberrypi.com/viewtopic.php?p=1971581&hilit=red+light#p1971581)

他把我引到了[这里](https://forums.raspberrypi.com/viewtopic.php?f=28&t=58151)

经过阅读，我找到了：

![官方问题描述](:2022-02-17-02.png)

因为我使用的是pi4b，所以可见是EEPROM损坏

其实这里我纠结很久，因为我的问题和网上没有完全一样的情况

最后是使用EEPROM的方式解决，并且再也没有损坏过，如果你手头有空闲sd卡，何不一试？

从MHYC.TECH下载此[zip文件](/assets/files/uploads/rpi-boot-eeprom-recovery-2022-01-25-vl805-000138a1-sd.zip)

或使用官方的[链接](https://github.com/raspberrypi/rpi-eeprom/)

解压会得到iso文件，按照烧录系统的方式烧录此iso文件

关闭树莓派，插上卡，打开树莓派，等待一会（大概十几秒），直到绿色led有规律闪烁

关闭树莓派，插上正常系统sd卡，成功!

[官方的问题解决](https://www.raspberrypi.com/documentation/computers/raspberry-pi.html#raspberry-pi-4-boot-eeprom)(往下翻一点)

## 参考资料

[树莓派官网](https://raspberrypi.org)  
[树莓派官网论坛的帖子](https://forums.raspberrypi.com/viewtopic.php?p=1971581&hilit=red+light#p1971581)  
[EEPROM修复iso](https://github.com/raspberrypi/rpi-eeprom/)
[官方的问题解决](https://www.raspberrypi.com/documentation/computers/raspberry-pi.html#raspberry-pi-4-boot-eeprom)