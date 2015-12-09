title: Ubuntu14.04  使用root用户的一些Solution
date: 2015-12-03 09:27:06
tags: [Ubuntu14.04,root]
---
# Ubuntu14.04  使用root用户的一些Solution

### 启用root并解决开机声音问题  
1. 首先为root设置密码  
`sudo passwd root`

2. `nano /usr/share/lightdm/lightdm.conf.d/50-ubuntu.conf`  
末尾添加如下内容    
`greeter-show-manual-login=true`

3. 重启就可以输入root用户名和密码登录,但是没有声音  
root登录打开终端输入:  
`pulseaudio --start --log-target=syslog`

4. 添加开机启动命令,避免每次都要输入  
按下super键搜索`启动应用程序` 添加开机启动,在命令一项中输入`pulseaudio --start --log-target=syslog`保存重启就可以了

### ubuntu自带中文输入法的输入错乱问题  
1. 打开终端输入:  
`ibus-daemon -drx`

### 启用chromium-browser 提示  
1. `不能以根用户身份运行，要以根用户身份运行，您必须为个人资料信息的存储指定其他的“–user-data-dir”`  
进入计算机，打开usr文件夹，打开share文件夹，打开applications文件夹，找到chromium图标，然后在命令那个选项修改为`chromium-browser %U - -user-data-dir=/root/.config/chromium`

### 备份Linux系统
##### 1. 备份 
 
        cd /
        tar cvpzf backup.tgz / --exclude=/proc --exclude=/lost+found --exclude=/backup.tgz --exclude=/mnt --exclude=/sys

>'tar'部分就是我们将要使用的软件  
>'cvpfz'是我们给tar加的选项，像“创建一个压缩文档”（这是显然的），“保存权限”（以便使每一个相同的文件有相同的权限），以及“gzip”（缩减大小）  
>接下来，是压缩文档将获得的名称，在我们的例子中是backup.tgz。  
>紧随其后的是我们想要备份的根目录。既然我们想备份所有东西：/  
>接着就是我们要剔除的目录了。我们不想备份每一样东西，因为包括有些目录不是非常有用。同时确保你没有把备份文件本身也加进去了，否则，你会得到怪异的结果的。你也许同样不打算把/mnt文件夹包括进来——如果你在那儿挂载了其他分区——否则最终你会把那些也备份的。同时确保你没有任何东西挂载在 /media(即没有挂载任何cd或可移动介质）。否则，剔除/media。

##### 2. 恢复  

        tar xvpfz backup.tgz -C /
        cd /
        mkdir proc lost+found mnt sys

>只要敲一下确定／回车／你的兄弟／随便什么，然后去看焰火吧。同样，这会花一段时间。等它完成了，你就有了一个完全恢复的Ubuntu系统！只需确保在你做其他任何事情之前，重新创建你剔除的目录：mkdir proc mkdir lost+found mkdir mnt mkdir sys etc...当你重启以后，所以的事情都会和你备份的时候一模一样。


    
