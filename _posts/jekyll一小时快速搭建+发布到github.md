---
layout: post
title: "jekyll一小时快速搭建+发布到github!"
date: 2018-07-01 00:01:01
category: web
tags: [jekyll,博客,GitHub]
---
前言
所使用到的软件和框架
安装 jekyll 本身相当简单，但是依赖于其他的一些环境。请先确保你的系统是Linux, Unix,Mac OS X,这是 jekyll 官方推荐的系统配置， windows 不推荐搭建 jekyll 。其次需要Ruby,RubyGems，因为需要使用到gem命令安装 jekyll 。

jekyll
Ruby
RubyGems
github
Linux, Unix,Mac OS X
为什么选择jekyll
jekyll是一个静态的网页框架，简单的用模板+文本就可以生成个人博客网页，而你在配置完jekyll以后就可以专注在写博客这件事情上，而不会分散注意力到web建设上，因为jekyll是一个轻量级的框架，并不需要连接数据库，它的思想就是，每篇博客一个文件，而jekyll负责将这些一个个博客文件加载到模板中，最终生成静态网页。

github注册
首先你得有一个github的账号，因为最后生成的静态网站是要放到github pages上面运行的。不推荐使用自己的服务器运行jekyll项目，题主将jekyll放在自己的服务器上运行的时候出现了很多稀奇古怪的问题。账号注册的地址：github注册

jekyll相关配置
配置环境、安装jekyll
安装jekyll需要使用如下命令：

~ $ gem install jekyll #=> 如果没有安装ruby环境首先需要安装ruby环境，才能使用gem命令。
~ $ jekyll new myblog #=> 在当前目录下创建一个名为myblog的jekyll项目
开启jekyll的本地预览服务
安装好了jekyll以后，可以使用如下代码进行本地测试：

~ $ cd myblog
~ $ jekyll serve
然后用浏览器访问http://localhost:4000，就可以预览刚刚建立的jekyll demo网站。 demo

配置域名
如果你不想配置自定义域名，请跳过这一步，这一步并不会影响教程的进行；如果你没有域名，请先申请一个域名，域名提供商有很多，请自行百度

进入你的域名提供商的主页，并且登录进你的控制台。 控制台

进入 解析域名的配置界面，删除其他记录，并添加下列三条记录： 域名配置 红圈中记录值的格式为：{username}.github.io，username就是你的github的用户名。下面两条A记录的地址一般为192.30.252.153和192.30.252.154，当然你一可以在这里查询。

这样域名就配置完了，现在访问以下你的域名地址看看是不是已经指向了你的github。当然如果还没有指向github，请耐心等待一会儿，域名提供商设置解析DNS也需要1-15分钟不等。

建立github pages
由于本教程的定位是1小时快速建个人博客，所以不涉及从0开始建立博客，我们要做的就是引用github上开源的jekyll项目，变成自己的博客。

fork优秀的网站
jekyll的wiki网站上给出了大量的优秀的网站，我们可以选择自己喜欢的风格的网站引用过来。

这里以第一个网站为例，点击网站名可以直接跳到网站进行浏览，点击边上的souce，可以跳转到相关的github上。 jekyll-wiki

如果你想引用这个网站，点击fork，就可以把这个网站加入到你个人仓库中了： fork

点击Settings，进入设置页面： Setting

将Repository name改为{username}.github.io，点击 Rename

这时你会发现http://{username}.github.io,已经可以访问你刚刚引用过来的网站了。可能也会有服务器延时问题，一般在1小时以内。

设置自己域名指向这个网站(需要有自己的域名)
在刚刚的代码仓库中找到CNAME文件(如果没有CNAME文件可以自己新建一个): CNAME

修改CNAME文件内容为自己购买的域名： edit CNAME

写改完以后，访问你的域名，你会发现已经指向了这个网站了。可能也会有服务器延时问题，一般在1小时以内。

Post一篇文章
安装git命令
我们进入这个项目的仓库，找到_post文件夹并进入： _post 可以看到，_post文件夹下面存放了所有的文章，并且这些文章都是头+markdown语言组成的，所以如果要发表一篇文章，就相当于要创建一个markdown文件，并且文件的后缀名为.md。

如果我们要在网页上创建、修改这些文件是极其效率不高的，所以我们第一步要把文件同步到我们本地。要同步github仓库到本地首先要安装github命令行：

如果你使用Debian或Ubuntu Linux: sudo apt-get install git
如果你使用Mac OS X: brew install git(需要安装homebrew，安装homebrew自行百度)
如果你使用Windows:可以下载git Bash
其他系统安装git命令自行百度
安装完后，打开终端，输入git确认是否安装成功： git 如果出现截图上的git命令的功能介绍，那就说明git命令已经安装完成。

同步github项目到本地
先设置git的用户名和邮箱

~ $ git config --global user.name "{username}"          #=> 用你的用户名替换{username}
~ $ git config --global user.email "{name@site.com}"    #=> 用你的邮箱替换{name@site.com}
为了传输github项目，要进行SSH配置：

~ $ ssh-keygen -t rsa -C"{name@site.com}"    #=> 用你的邮箱替换{name@site.com}
create ssh cd到红框中的目录，复制红框文件中的代码。

接下来，登录github进入Settings页面： my settings 新建ssh密匙： new ssh 这样SSH就配置完成了，接下来就可以同步github上面的项目到本地了。

切换到你想放置github项目的路径下，clone你的远程仓库到本地：

~ $ git clone https://github.com/{username}/{username}.github.io.git
     #=> 用你的Github用户名替换{username}
有clone失败的可能，毕竟是国外网站，原因大家都懂，多试几次就行了。

至此，整个github项目已经同步到本地了，之后要修改项目只需要在本地修改完以后，同步到github仓库中就可以了。

撰写博客
打开本地仓库的 _posts 文件夹，你的所有博文都要放在这里，写新博文只需要新建一个标准文件名的文件，在文件中编写文章内容。文件名要严格按照年-月-日-文章标题.文档格式的格式，要注意月份和日期是两位数，比如2014-04-21-farewell-github-hello-immersive-computing.md。推荐使用markdown语言来写博客文件，如果你使用markdown语言，则文件的后缀为md。

博客文件是由YAML头信息+markdown组成的。YAML头信息在jekyll官方网站上有详细介绍，也可以参考_post文件夹下已存在的.md文件。

用markdown来写文章是一种习惯，因为markdown是非常适合来写文章的，用习惯了就再也离不开了，所以题主极力推荐markdown语言。这篇关于markdown的文章写得挺不错的。在写markdown的时候，可以使用一些工具，这样让你更加直观得写博客。Mac OS X平台推荐Mou.

测试博客
打开终端，切换到github目录下，启动jekyll本地测试服务:

~ $ jekyll serve
打开浏览器，输入http://localhost:4000，就可以浏览你的博客网站了。

每次你修改项目，只要刷新一下浏览器，就可以实时的查看结果了。

发布博客
这时，你访问你的域名，可能会感觉奇怪，我发表了一篇或者几篇博客，为什么没有任何变化呢？那是因为刚刚修改的本地项目只能在本地浏览，还没有上传到github上面。

每当你对本地仓库里的文件进行了修改，只需在Bash中依次执行以下三个命令即可将修改同步到Github，刷新网站页面就能看到修改后的网页，当然首先切换到github项目的目录下：

~ $ git add .
~ $ git commit -m "statement"   #=>此处statement填写此次提交修改的内容，作为日后查阅
~ $ git push origin master
这样你就可以发布你的博客了！