---
lng_pair: id_Building_personal_blog_With_Jekyll_And_Raspberrypi_4b
title: 【English】Building personal blog with jekyll and raspberrypi 4b
date: 2022-03-06 11:45:14 +0900
category: guide
tags: [raspberrypi, jekyll, website]
img: ":jekyll.png"
---

<!-- outline-start -->
My Raspberrypi 4b is for a minecraft server at first, but soon i found it isn't qualified the task, so i decided to give it a new mission.

Im in China so github is slow(really slow!!), my github pages is done but i cant push anything onto it, so im going to build my website on my raspberrypi.
<!-- outline-end -->


# Choosing Blog platform
(Can i call jekyll 'Blog Platform'?)

I found some blog platform [here](https://zhuanlan.zhihu.com/p/25280413)(Open it in a new tab) . My two best choice are 'Jekyll' and 'WordPress'. I want to use wordpress at first but soon i noticed it uses SQL -- i dont need it.

So i choose jekyll.

# Installing Jekyll
###### Attention! Im using **pi 4b**, if your pi is 3b or lower, **dont** follow my step!

### What you need to install:

- Ruby(Jekyll2 needs version >= 1.9.3, Jekyll3 needs version >=2)
- RubyGems
- NodeJS
- Python(im using 3)

[Jekyll Docs](https://jekyllrb.com/docs/)

If you aren't using raspi but using other OS: See [Docs(Inatallation)](https://jekyllrb.com/docs/installation/) and choose your System then follow it.

### Install steps for 4b Debain:

1.	```sudo apt-get install ruby-full build-essential```
2.	```echo '# Install Ruby Gems to ~/gems' >> ~/.bashrc```
3.	```echo 'export GEM_HOME="$HOME/gems"' >> ~/.bashrc```
4.	```echo 'export PATH="$HOME/gems/bin:$PATH"' >> ~/.bashrc```
5.	```source ~/.bashrc```
6.	```gem install jekyll bundler```

### Create your website:

##### Programmer

If you are a programmer want to create a jekyll theme and upload it to github for everyone(I think you're not), run ```jekyll new myblog``` and it will create a dir in your console location now named `myblog`. And you can start your coding now.

##### Simple user

If you are just using jekyll as a blog or you dont want to see any codes, follow me:

###### Find your theme

Find your favourite theme in these links:

- [Github Jekyll Themes](https://github.com/topics/jekyll-theme)
- [Jamstack Themes](https://jamstackthemes.dev/ssg/jekyll/)
- [Jekylltheme.org](http://jekyllthemes.org/)
- [Jekylltheme.io](https://jekyllthemes.io/)
- [Jekyll-theme.com](https://jekyll-themes.com/)

Whatever which one you choose, it should finally link to a github repository.

Click `Code`  and the copy the `git link`

![CopyThisLink](/assets/images/uploads/2022-03-06-01.png)

run ```git clone [your theme git link]```

Such as my 'SerialProgrammer': 
```git clone 
https://github.com/sharadcodes/jekyll-theme-serial-programmer.git```

Then move into your clone dir: ```cd [your theme dir]```

Run ```bundle install``` and wait for a while

Now you can edit `_config.yml` to custom your website.

All you can see on your website can be edit, but be careful of your LINCES.

Run `bundle exec jekyll serve` in your blog dir to start server.

Now you can see your website by entering `127.0.0.1:4000` in your browser, congratulations!

[common problems--not complete]()

[url toturial--not complete]()
