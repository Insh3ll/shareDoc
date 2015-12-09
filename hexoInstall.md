title: hexoInstall
date: 2015-12-02 17:05:25
tags: Hexo
---
# hexo 安装教程

## 以下步骤完成搭建本地Hexo
安装git并配置  
>apt-get install git
>git config --global user.email "example@gmail.com"
>git config --global user.name "Gitname"

安装node.js  
>add-apt-repository ppa:chris-lea/node.js  
>apt-get update  
>apt-get install nodejs  

安装Hexo
>npm install -g hexo

创建hexo文件夹并初始化
>mkdir hexo
>cd hexo
>hexo init

安装依赖包
>npm install

本地测试浏览hexo博客
>hexo g  
>hexo s

## 部署到Github

### Github端设置
注册Github帐号  
已有帐号,没有的请注册

创建repository和个人page
![](http://i5.tietuku.com/1093b05eb0a1a2b6.png)
![](http://i5.tietuku.com/9a2bc68eeec3e750.png)
![](http://i5.tietuku.com/1496da31b2daa652.png)

生成SSH-Key
>ssh-keygen -t rsa -C "example@gmail.com"

添加公钥到Github  
![](http://i5.tietuku.com/9a2bc68eeec3e750.png)

### 本地端设置
编辑hexo目录下_config.yml文件(注意hexo配置文件中冒号后有一个空格)  
```
deploy:
  type: git
  repository: git@github.com:Insh3ll/insh3ll.github.io.git
  branch: master
```

部署到Github
>npm install hexo-deployer-git --save
>hexo g
>hexo d


### _config.yml配置文件说明
```
# Hexo Configuration
## Docs: http://hexo.io/docs/configuration.html
## Source: https://github.com/hexojs/hexo/

# Site	站点设置
title: InsBlog	#博客名
subtitle: 笔记.备忘.心情	#副标题
description:  #用于搜索，没有直观表现
author: Ins	#作者
language: zh-Hans	#语言
timezone:  #时区，此处不填写，hexo会以你目前电脑的时区为默认值
avatar: http://i12.tietuku.com/d8301e6016fae87a.jpg  #侧栏头像

# URL	暂不配置，使用默认值
## If your site is put in a subdirectory, set url as 'http://yoursite.com/child' and root as '/child/'
url: http://yoursite.com
root: /
permalink: :year/:month/:day/:title/
permalink_defaults:

# Directory		暂不配置，使用默认值
source_dir: source
public_dir: public
tag_dir: tags
archive_dir: archives
category_dir: categories
code_dir: downloads/code
i18n_dir: :lang
skip_render:

# Writing	文章布局等，使用默认值
new_post_name: :title.md # File name of new posts
default_layout: post
titlecase: false # Transform title into titlecase
external_link: true # Open external links in new tab
filename_case: 0
render_drafts: false
post_asset_folder: false
relative_link: false
future: true
highlight:
  enable: true
  line_number: true
  tab_replace:

# Category & Tag	暂不配置，使用默认值
default_category: uncategorized
category_map:
tag_map:

# Date / Time format	时间格式，使用默认值
## Hexo uses Moment.js to parse and display date
## You can customize the date format as defined in
## http://momentjs.com/docs/#/displaying/format/
date_format: YYYY-MM-DD
time_format: HH:mm:ss

# Pagination	
## Set per_page to 0 to disable pagination
per_page: 10	#每页显示的文章数，0表示不分页
pagination_dir: page

# Extensions	插件配置，暂时不配置
## Plugins: http://hexo.io/plugins/
## Themes: http://hexo.io/themes/
plugins:
- hexo-generator-feed
theme: light	#使用的主题

feed:	#之后配置rss会用，此处先不配置这个
  type: atom
  path: atom.xml
  limit: 20  

# Deployment	用于部署到github，之前已经配置过
## Docs: http://hexo.io/docs/deployment.html

deploy:
  type: git
  repository: git@github.com:Insh3ll/insh3ll.github.io.git
  branch: master
```

关于Next主题的使用请查看[http://theme-next.iissnan.com/](http://theme-next.iissnan.com/)
