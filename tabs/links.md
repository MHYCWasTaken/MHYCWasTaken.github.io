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
    header: "Links"
    info: "Some of MHYC's website collection."

  # To change order of the Categories, simply change order. (you don't need to change list order.)
  category:
    - title: "Useful Resources"
      type: id_resources
      color: "#AC3232"
    - title: "Useful Tools"
      type: id_tools
      color: "#DF7126"
    - title: "Useful Applications"
      type: id_apps
      color: "#FBF236"
    - title: "Useful Articles"
      type: id_good_articles
      color: "#99E550"
    - title: "Good Website Design"
      type: id_website_design
      color: "#6ABE30"
    - title: "Time Killer"
      type: id_time_killer
      color: "#37946E"

  list:
  
    # apps
    - type: id_apps
      title: "KiCAD"
      url: "https://www.kicad.org/"
      info: "Open source pcd and schmetics designer, and the only choice on linux."
    - type: id_apps
      title: "Lunar Client"
      url: "https://www.lunarclient.com/"
      info: "Lunar is a Minecraft Java Client/Launcher for PVP and high FPS"
    - type: id_apps
      title: "Labymod Client"
      url: "https://www.labymod.net/en/"
      info: "Labymod is also a Minecraft Java Client for PVP and high FPS"
    - type: id_apps
      title: "Motrix"
      url: "https://motrix.app/"
      info: "A downloader based by Aria, Say GOODBYE to thunder."
    - type: id_apps
      title: "Install Aseprite on Linux"
      url: "https://docs.shanyuhai.top/design/pixel/install-aseprite-on-linux.html#%E5%AE%89%E8%A3%85"
      info: "From Blog of 飞跃高山与大海的鱼"
    
    # website design
    - type: id_website_design
      title: "Interesting Cursor"
      url: "https://www.cnblogs.com/zhaoqingqing/p/11546010.html"
      info: "I'm sorry about my focus is on the mouse pointer"
    - type: id_website_design
      title: "Interesting Cursor * 2"
      url: "https://www.cnblogs.com/Potrem/p/51_6.html"
      info: "I'm very sorry about my focus is on the mouse pointer"
    - type: id_website_design
      title: "Interesting design of site"
      url: "https://embersword.com/"
      info: "I'm really sorry. My focus is on typesetting and fonts"
      

    # resources
    - type: id_resources
      title: "Jetbrains Mono"
      url: "https://www.jetbrains.com/lp/mono/"
      info: "Jetbrain's mono font. Designed for programmer"
    - type: id_resources
      title: "基本操作——可以玩的大学课程"
      url: "https://jibencaozuo.com/zh-Hans/"
      info: "died"
    - type: id_resources
      title: "ZX Spectrum Contents of instructions"
      url: "https://worldofspectrum.org/ZXBasicManual/"
      info: "Instructions for an 8-bit computer of the last century"
    - type: id_resources
      title: "FontAwesome"
      url: "https://fontawesome.com"
      info: "No more worrying about icons"
    
      
    # articles
    - type: id_good_articles
      url: "https://www.zhihu.com/question/20112194"
      title: "为什么计算机能够读懂0和1？(知乎)"
      info: "A computer composition starting with logic gates (easy to understand)(in Chinese)"
      

    # tool
    - type: id_tools
      title: "VERSUS Compare"
      url: "https://versus.com/cn/"
      info: "Compare everything, including cities, universities and GPUs"
    - type: id_tools
      title: "Bullshit Generator"
      url: "https://suulnnka.github.io/BullshitGenerator/index.html"
    - type: id_tools
      title: "Minecraft font pack generator"
      url: "https://codepen.io/devbobcorn/full/YzZMZvV"
      info: "Upload ttf file and download font resources pack"
    - type: id_tools
      title: "Mountain Finder"
      url: "https://www.peakfinder.org/"
      info: "Find you favourite mountain(based on bgfx and opensource)"
    - type: id_tools
      title: "GodoterCN"
      url: "https://godoter.cn/"
      info: "The domestic Godot community has a good atmosphere"
    - type: id_tools
      title: "Alternative To"
      url: "https://alternativeto.net/"
      info: "When you find that the required software is not available on linux/mac, come here"
      
      
    # time killer
    - type: id_time_killer
      title: "Spirisut of sound"
      url: "https://pos.biborg.com/fr/"
      info: "I don't know which country's powerful developers made three Parkour"
    - type: id_time_killer
      title: "DLS Sandbox"
      url: "https://dls.makingartstudios.com/sandbox/"
      info: "Logic gate sandbox, It is suggested to use with “为什么计算机能够读懂0和1？(知乎)”"
    - type: id_time_killer
      title: "EmberSword"
      url: "https://embersword.com/"
      info: "An online game based on bgfx. It seems that it can't be registered, but the publicity page is very nice"
    - type: id_time_killer
      title: "Lichess"
      url: "https://lichess.org/"
      info: "Online free opensource Chess"
    - type: id_time_killer
      title: "Play Chess with Stockfish"
      url: "https://listudy.org/en/play-stockfish"
      info: "Play Chess against Stockfish(strongest Chess AI, opensource)"
    - type: id_time_killer
      title: "Chess Wars"
      url: "https://dt-mark.itch.io/chess-wars"
      info: "RPG And Items crack with Chess (free)"
---
