---
# multilingual page pair id, this must pair with translations of this page. (This name must be unique)
lng_pair: id_Chess_How_01
title: "【中】原理图设计的学习笔记（01）"

# post specific
# if not specified, .name will be used from _data/owner.yml
author: MHYC133
# multiple category is not supported
category: projects
# multiple tag entries are possible
tags: [hardware, pcb]
# thumbnail image for post
img: ":sch-learn.png"
# disable comments on this page
#comments_disable: true

# publish date
date: 2022-06-11 11:45:14 +0900

# seo
# if not specified, date will be used.
#meta_modify_date: 2022-03-03 10:04:19 +0900
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
---

{%- capture readme_file -%}{%- include_relative Chess-How-01.md -%}{%- endcapture -%}
{%- assign tmp_content = readme_file | split: "<!-- readme -->" -%}
{{tmp_content[1]}}