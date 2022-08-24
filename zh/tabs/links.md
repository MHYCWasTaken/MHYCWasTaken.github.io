---
layout: links
# multilingual page pair id, this must pair with translations of this page. (This name must be unique)
lng_pair: id_links

# publish date (used for seo)
# if not specified, site.time will be used.
#date: 2022-03-03 12:32:00 +0000

# for override items in _data/lang/[language].yml
#title: My title
#button_name: "My button"
# for override side_and_top_nav_buttons in _data/conf/main.yml
#icon: "fa fa-bath"

# seo
# if not specified, date will be used.
#meta_modify_date: 2022-03-03 12:32:00 +0000
# check the meta_common_description in _data/lang/[language].yml
#meta_description: ""

# optional
# if you enabled image_viewer_posts you don't need to enable this. This is only if image_viewer_posts = false
#image_viewer_on: true
# if you enabled image_lazy_loader_posts you don't need to enable this. This is only if image_lazy_loader_posts = false
#image_lazy_loader_on: true
# exclude from on site search
#on_site_search_exclude: true
# exclude from search engines
#search_engine_exclude: true
# to disable this page, simply set published: false or delete this file
#published: false


# you can always move this content to _data/content/ folder
# just create new file at _data/content/links/[language].yml and move content below.
###########################################################
#                Links Page Data
###########################################################
page_data:
  main:
    header: "链接"
    info: "MHYC自己收藏的一些有趣的网站，当作工具箱吧（ps.直接点击链接会在新标签页打开）
    如果某链接失效或指向不正确，请发送标题为“Links werent working”的邮件至MHYC"

  # To change order of the Categories, simply change order. (you don't need to change list order.)
  category:
    - title: "奇妙资源"
      type: id_resources
      color: "#AC3232"
    - title: "奇妙工具"
      type: id_tools
      color: "#DF7126"
    - title: "奇妙软件"
      type: id_apps
      color: "#FBF236"
    - title: "好的文章"
      type: id_good_articles
      color: "#99E550"
    - title: "奇妙的网页设计"
      type: id_website_design
      color: "#6ABE30"
    - title: "消磨时间"
      type: id_time_killer
      color: "#37946E"

  list:
  
    # apps
    - type: id_apps
      title: "KiCAD"
      url: "https://www.kicad.org/"
      info: "开源的pcb及原理图设计软件，也基本是linux系统上的唯一选择"
    - type: id_apps
      title: "Lunar客户端"
      url: "https://www.lunarclient.com/"
      info: "Lunar是一个便于pvp和提高帧率的minecraft java启动器/客户端"
    - type: id_apps
      title: "Labymod客户端"
      url: "https://www.labymod.net/en/"
      info: "Labymod也是一个便于pvp和提高帧率的minecraft java客户端"
    - type: id_apps
      title: "Motrix"
      url: "https://motrix.app/"
      info: "基于Aria的开源下载器，和迅雷说拜拜"
    - type: id_apps
      title: "在Linux下安装Aseprite"
      url: "https://docs.shanyuhai.top/design/pixel/install-aseprite-on-linux.html#%E5%AE%89%E8%A3%85"
      info: "来自飞跃高山与大海的鱼的博客"
  
    # website design
    - type: id_website_design
      title: "奇妙鼠标指针"
      url: "https://www.cnblogs.com/zhaoqingqing/p/11546010.html"
      info: "非常抱歉我的关注点在鼠标指针上面"
    - type: id_website_design
      title: "奇妙鼠标指针(二度)"
      url: "https://www.cnblogs.com/Potrem/p/51_6.html"
      info: "真的非常抱歉我的关注点在鼠标指针上面"
    - type: id_website_design
      title: "很好看的页面排版和字体"
      url: "https://embersword.com/"
      info: "真的非常抱歉我的关注点在排版和字体上面"
    - type: id_website_design
      title: "非常牛逼的网页版win11"
      url: "https://win11.blueedge.me/"
      info: "真的TNND牛逼"
  

    # resources
    - type: id_resources
      title: "Jetbrains Mono"
      url: "https://www.jetbrains.com/lp/mono/"
      info: "Jetbrain自带的等宽字体，专为程序员设计"
    - type: id_resources
      title: "基本操作——可以玩的大学课程"
      url: "https://jibencaozuo.com/zh-Hans/"
      info: "已经没用咧，默哀3秒钟"
    - type: id_resources
      title: "ZX Spectrum 说明书目录"
      url: "https://worldofspectrum.org/ZXBasicManual/"
      info: "一台上世纪8位计算机的说明书"
    - type: id_resources
      title: "FontAwesome"
      url: "https://fontawesome.com"
      info: "再也不用为图标发愁辣～"
    - type: id_resources
      title: "ALL NEW ELECTRONICS SELF-TEACHING GUIDE (1)"
      url: "assets/ALL NEW ELECTRONICS SELF-TEACHING GUIDE (1).pdf"
      info: "电子学自学指南（1）（pdf）"
    - type: id_resources
      title: "ALL NEW ELECTRONICS SELF-TEACHING GUIDE (2)"
      url: "assets/ALL NEW ELECTRONICS SELF-TEACHING GUIDE (2).pdf"
      info: "电子学自学指南（2）（pdf）"
    - type: id_resources
      title: "OI WIKI"
      url: "https://oi-wiki.org/"
      info: "c++竞赛wiki，设计各种算法详解及STL讲解，再也不用去CSDN辣"
    - type: id_resources
      title: "Havok Physics"
      url: "https://www.havok.com/"
      info: "震荡波物理引擎，此外震荡波还有npc的AI和布料模拟，塞尔达botw使用了全部3个"
  
  
    # articles
    - type: id_good_articles
      url: "https://www.zhihu.com/question/20112194"
      title: "为什么计算机能够读懂0和1？(知乎)"
      info: "一篇从逻辑门开始讲起的计算机构成（简单易懂）"
    - type: id_good_articles
      url: "https://zhuanlan.zhihu.com/p/423120746"
      title: "从零手写游戏引擎21：物理引擎基础(知乎)"
      info: "游戏引擎物理部分基础"
    - type: id_good_articles
      url: "http://allenchou.net/game-physics-series/"
      title: "游戏物理系列 | 明伦“艾伦”周 | 周明伦"
      info: "物理引擎系列"
    - type: id_good_articles
      url: "https://ubuntu.com/blog/linux-gaming-tutorial-raspberry-pi-minecraft-server-on-ubuntu-desktop"
      title: "Raspberry Pi 教程：在 Ubuntu 桌面上托管 Minecraft 服务器 Ubuntu
      info: "简单直接的mc开服教程，其他地方大同小异"
  

    # tool
    - type: id_tools
      title: "VERSUS对比"
      url: "https://versus.com/cn/"
      info: "万物皆可对比，包括城市，大学和GPU"
    - type: id_tools
      title: "狗屁不通文章生成器"
      url: "https://suulnnka.github.io/BullshitGenerator/index.html"
    - type: id_tools
      title: "我的世界字体包生成"
      url: "https://codepen.io/devbobcorn/full/YzZMZvV"
      info: "上传ttf文件即可制作字体资源包"
    - type: id_tools
      title: "山峰寻找器"
      url: "https://www.peakfinder.org/"
      info: "找到你最熟悉的那座山（基于bgfx渲染且开源）"
    - type: id_tools
      title: "GodoterCN"
      url: "https://godoter.cn/"
      info: "国内的Godot社区，氛围很好"
    - type: id_tools
      title: "Alternative To"
      url: "https://alternativeto.net/"
      info: "当你发现需要的软件在linux/mac上没有时，就来这里"
    - type: id_tools
      title: "jsfxr"
      url: "https://sfxr.me/"
      info: "8bit音效生成，有专业版，似乎不需要付费"
    - type: id_tools
      title: "Jitsi Meetings"
      url: "https://meet.jit.si/"
      info: "腾讯会议替代品，免费无需账号的视频会议"
    - type: id_tools
      title: "BigBlueButton"
      url: "https://bigbluebutton.org/"
      info: "为教师设计的虚拟教室（视频会议）"
    - type: id_tools
      title: "最佳 Minecraft 服务器托管 - RAMShard"
      url: "https://ramshard.com/hosting/minecraft?referrer=ga"
      info: "我的世界服务器托管"
    - type: id_tools
      title: "ScalaCube - Game Server Hosting"
      url: "https://scalacube.com/"
      info: "我的世界服务器托管"
  
  
    # time killer
    - type: id_time_killer
      title: "Spirisut of sound"
      url: "https://pos.biborg.com/fr/"
      info: "不知道哪国的强大开发者制作的三道跑酷"
    - type: id_time_killer
      title: "DLS Sandbox"
      url: "https://dls.makingartstudios.com/sandbox/"
      info: "逻辑门的沙盒，建议搭配“为什么计算机能够读懂0和1？(知乎)”食用"
    - type: id_time_killer
      title: "EmberSword"
      url: "https://embersword.com/"
      info: "一款基于bgfx的网游，似乎无法注册但是宣传页面很好看"
    - type: id_time_killer
      title: "Lichess"
      url: "https://lichess.org/"
      info: "开源免费在线国际象棋，比国内的那些奇妙的广告喧宾夺主的平台好多了"
    - type: id_time_killer
      title: "和Stockfish下棋"
      url: "https://listudy.org/en/play-stockfish"
      info: "与最强国象AI(开源)对弈(虽然lichess也行)"
    - type: id_time_killer
      title: "Chess Wars"
      url: "https://dt-mark.itch.io/chess-wars"
      info: "RPG和回合制与国际象棋的奇妙融合（免费）"
    - type: id_time_killer
      title: "ULTRAKILL"
      url: "https://hakita.itch.io/ultrakill-prelude"
      info: "打击感非常好但是略恐怖的极好fps游戏"
    - type: id_time_killer
      title: "RE:RUN"
      url: "https://hakita.itch.io/ultrakill-prelude"
      info: "跑酷飞刀游戏"
    - type: id_time_killer
      title: "Checkmate"
      url: "https://charlie-morel.itch.io/checkmate"
      info: "国际象棋+tps"
    - type: id_time_killer
      title: "eldritch-eclipse"
      url: "https://crowbarska.itch.io/eldritch-eclipse"
      info: "像素风类doom的fps游戏"
    - type: id_time_killer
      title: "Mindustry"
      url: "https://anuke.itch.io/mindustry"
      info: "混合塔防沙盒工厂游戏，创建传送带供应链，将弹药送入炮塔，生产材料，保护你的建筑"
    - type: id_time_killer
      title: "A short hike"
      url: "https://adamgryu.itch.io/a-short-hike"
      info: "3维，自由探索，登山，卡通画风(7.99USD)"
    - type: id_time_killer
      title: "Desktop Goose"
      url: "https://samperson.itch.io/desktop-goose"
      info: "桌面宠物，鹅"
    - type: id_time_killer
      title: "Mobs inc"
      url: "https://overboy.itch.io/mobs-inc"
      info: "冲刺杀人，打工"
    - type: id_time_killer
      title: "Rougelight"
      url: "https://managore.itch.io/roguelight"
      info: "卷轴视角地牢，像素画风，低对比度"
    - type: id_time_killer
      title: "Force Reboot"
      url: "https://ln404.itch.io/force-reboot"
      info: "肉鸽fps，也有极好打击感，但无恐怖元素"
    - type: id_time_killer
      title: "Overboy"
      url: "https://overboy.itch.io/"
      info: "不错的游戏工作室，大部分游戏可以在线游玩，下载需money"
    - type: id_time_killer
      title: "Bruno-Simon"
      url: "https://bruno-simon.com/"
      info: "网页端的开越野车游戏"
---
