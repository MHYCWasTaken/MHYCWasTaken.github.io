---
lng_pair: id_Open_Up_Your_Website
title: 【En】Open up website
date: 2022-04-22 11:45:14 +0900
category: projects
tags: [website, software]
img: ":natfrp.png"
---

# Warning! This page is auto translated by [GoogleTranslate](https://translate.google.cn)

#### OK is back

<!-- outline-start -->

Going through a long period of research, overcoming obstacles, and haggling with parents

The website is finally online

Today, let’s talk about how this website was launched and what unexpected twists and turns it has experienced.

If you want to learn website online, this article can help you

<!-- outline-end -->

(The previous section describes how to access your website on the external network, and the end of the article explains how to configure the domain name and the DNS service of the domain name.)

First of all, if we want to launch a website, we need to understand

# The principle of visiting the website

*Automatically fill in cool music and flashing titles*

You know, a website is a file on the server (static pages only), through a complex path to find the browser that accesses the website and render the screen.

Then, if the website on the LAN cannot be accessed, of course, the browser cannot find the server.

So we have to build a pathway :)

First, let's take a look:

## The easiest one

![Pathway - the simplest one](:2022-04-22-02.png)

In this picture, the user visits ````www.baidu.com```, finds the server with ipv4 address ```220.181.38.148``` through some complex network communication methods, obtains data (page) and renders it .

If it is more precise (I don't know the virtual operator of the domain name baidu.com, assuming it is Aliyun)

After visiting ``baidu.com```, the user finds Alibaba Cloud's DNS server, and through the DNS server learns that the ipv4 address of the Baidu server is ```220.181.38.148```, and then goes to the server to obtain data

If your server is a cloud server, the path is the same, so congratulations, your problem has been solved, there will be no problem in following the service provider's documentation or something (this method needs to record the domain name, at the service provider)

Sadly, my situation is not so simple, so let's continue:

## Not a cloud server

This means your server is in your own home or somewhere else (crap)

Then, your server may not have a suitable network environment

Don't worry, we make our own without the environment :)

### public network ip

Please check whether your home is a public network ip

If yes, then congratulations, your situation is relatively simple

If not, please skip to apply for a non-public network ip, and then reading may make you busy

Actually, you just need to configure the domain name in the same way as the cloud server

point the domain name to the ip address

But obviously, the ip address is not set in stone

So we need to use:

__DDNS__

The DNS server is always on, and the ip address does not change frequently

But your server may not be

So we can add dynamic "D" in front of DNS, it becomes "dynamic domain name resolution"

How to configure it?

Since I don't have an available router other than tplink, I will use tplink (cloud routing interface) to demonstrate, which should be similar. If it is really different, you can try to contact the customer service of the router's official website.

First, log in to the router management interface (tplogin.cn or 192.168.1.1 etc.)

The password should be on the back of the router

Then, click on the application management below

Click "Enter" under DDNS

![Click](:2022-04-22-01.png)

There are two options here: tplink router provides DDNS and peanut shell provides DDNS

![DDNS provided by tplink](:2022-04-22-03.png)

Please note that a router account can only have one and __ cannot be deleted! ! __ caution! Please be careful before registering

You can also use the DDNS provided by Peanut Shell, but the management interface of DDNS will be on the official website of Peanut Shell

DDNS can only allow the external network to access your router, and cannot access your server from the external network

So please configure the virtual host

![Virtual host configuration](:2022-04-22-04.png)

The external port is the port when accessing

The internal port is the intranet service port

The ip address is the intranet server ip

Please select TCP for protocol type

External port selection 80 (the common server is automatically set to HTTP) can be accessed without port in the browser

But ports below 9000 may be blocked, here I choose 9090

If there is no problem, you can directly access the domain name set by DDNS at this time.

If there's a problem:

1. The intranet service is not configured, how to access if there is no service

2. The gateway configuration problem, I don’t understand it very well. Generally, the server can connect to the network, and the Internet can be accessed normally.

3. The port development is not complete, and the DMZ host is configured on the router to solve the problem

4. Non-public IP

### Non-public IP

Option 1, apply for one without a public IP

I'm here with Tianjin Unicom, here for a prostitution

1. Visit [China Unicom's official website](10010.com), contact customer service -> transfer to labor -> tell him to apply for a public network ip, you may be asked to find a business hall

2. Visit Baidu Map, find the nearest business hall, and make a call

3. Saying to apply for a public network ip, he may not recognize this business, tell him 10010 to let you find him

4. Create a work order

5. Wait

6. The master called and added the master WeChat

7. Send the front and back of the ID card, hold the photo of the upper body of the ID card, the use of public network ip

. . .

Then. . Then I don't know, I'm stuck here. . .

Negotiation with parents failed. . .

The next step is probably for the master to come to the door, change it for you, disconnect the network for a while, and then it will be fine

Then since the negotiation fails, let's change a plan.

Option 2, intranet penetration

It is a killer, except for the shortcomings, there are basically no shortcomings.

This scheme even works on minecraft servers

First introduce a useful intranet penetration: [Sakura penetration SakuraFrp](https://natfrp.com)

Intranet penetration, as the name implies, breaks through the restrictions of the intranet, so that you can only open specific ports of specific devices just like the public network ip

Register, log in, spend a dollar for real name, click Help -> Help Documentation

Just follow what he did (I won't go into details here, the documentation is very detailed)

Reading order:

HTTP(S) penetration

Linux installation and use of the launcher

After completion, use the number in the colon category that appears on the mouseover node to access

At this point, the public network is already accessible

Then the next step is to beautify this smelly and long address :)

# Attach -- domain name and DNS server configuration

You know, baidu.com and www.baidu.com are two different addresses

Buying the domain name baidu.com will get all subdomains (level three, level four, level five)

www is the third-level domain name of baidu.com

(Demo using Alibaba Cloud)

Open Alibaba Cloud official website, log in, console in the upper right corner, domain name, domain name resolution

Add parsing records

Resolution type CNAME, record value baidu.com, hostname@

Such a resolution will redirect your domain name to baidu.com

@ means direct access to your domain name without prefix

For example, my domain name is mhyc.tech, after adding this analysis, the browser will directly go to Baidu home by entering mhyc.tech

Now that you can understand the analysis principles and features of Alibaba Cloud, it is time to solve practical problems.

# The domain name is too ugly

Happy to enter the domain name and port for intranet penetration in the Alibaba Cloud console, but found that CNAME resolution cannot add the port

What to do, visit mhyc.tech: port number is too inelegant

. .

Can we add another server and make this server point to the web server and make the domain name point to this server?

Grand introduction:

## URL forwarding

Definition and classification can be Baidu.

A tool for URL forwarding is recommended here [Mifa URL Forwarding](https://mfpad.com)

Through him, you can point the domain name to another domain name plus port

Now, the flow of accessing your website looks like this:

![The most complicated case](:2022-04-22-05.png)

Note: the current problems with this method:

1. There is no icon on the webpage

2. Refresh the page to go back to the home page (really uncomfortable)

3. Does not appear. . .

Now trying to solve these problems, if there is progress, I will add it immediately

---

# 2022-06-17 22:05

Just found out, the natfrp documentation was updated with a couple of additions to the https tutorial, so I remembered if it was possible to use an overseas tunnel

Create an overseas tunnel (possibly with the suffix "by wall")

Follow the documentation and you can completely resolve all questions about the website

Congratulations!
-----

Links

[Tplink DDNS Guide](https://service.tp-link.com.cn/detail_article_69.html)

[tplink端口映射failed（Guide）](https://service.tp-link.com.cn/detail_article_427.html)

[Aliyun](cn.aliyun.com)

[MFpad URL](https://mfpad.com)
