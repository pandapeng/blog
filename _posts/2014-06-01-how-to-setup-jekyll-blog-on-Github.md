---
bg: "jekyll_github.jpg"
layout: post
summary: "Setup jekyll blog in details(Chinese)"
crawlertitle: "How to setup jekyll Blog on Github -- by Pan Dapeng"
title:  "How to setup jekyll Blog on Github"
date:   2014-06-01 09:30:00
categories: posts
tags: ['jekyll']
author: Pan Dapeng
---
今天试着建立一个基于Github的Blog。过程并不复杂，并对Ruby，RubyGems，jekyll，Markdown等有了初步的了解，以后就可以通过git来管理自己的Blog了！安装及配置过程如下，作为Github Blog的第一个post。

**系统**：OSX 10.9.3
**开发环境**：Python 2.7.5, Ruby 2.0.0

## 1. 注册Github账户，并且配置Github Pages信息

此处不细说，参见[Github Pages Basics](https://help.github.com/categories/20/articles),和[使用Github Pages建独立博客](http://beiyuu.com/github-pages/)。

## 2. jekyll installation pre-condition

*2.1* Install Xcode

*2.2* Install Xcode Command Line Tools. These can either be installed by downloading them from the Apple Developer site or from running xcode-select --install. This will trigger a popup. Click on install and it will download & install the tools.

*2.3* Install Homebrew. 

`ruby -e "$(curl -fsSL https://raw.github.com/Homebrew/homebrew/go/install)"`

*2.4* Run brew doctor to check that Homebrew is installed correctly.

*2.5* Because Mavericks, like Mountaion Lion, doesn't come with GCC 4.2, it needs to be installed and linked to the correct place. Some packages require it so it's best to install it now `brew install apple-gcc42` and `sudo ln -s /usr/local/bin/gcc-4.2 /usr/bin/gcc-4.2`

*2.6* Install RVM - `curl -L https://get.rvm.io | bash -s stable --autolibs=enabled`

*2.7* You may need to run `source $HOME/.rvm/scripts/rvm` after (replacing YOUR-USERNAME with the username of your machine)

*2.8* To install Ruby 2.0.0 - ```rvm install 2.0.0```

*2.9* Set Ruby 2.0.0 as the default - ```rvm use 2.0.0 --default```

## 3. Install and use jekyll

*3.1* ```sudo gem install jekyll``` 参见[安装jekyll](http://jekyllcn.com/docs/installation/)

*3.2* 安装markdown语法解析工具rdiscount - ```sudo gem install rdiscount```

*3.3* jekyll基本用法：

* 新建一个jekyll文件夹：```jekyll new <MySiteName>```

* 执行```jekyll build```。此处会生成```_site```文件夹。后面会提到，当git push到Github时，此文件夹应该在.gitignore中声明，防止push到远端repo中。

* 启动jekyll开发服务器：```jekyll serve``` 参加(http://jekyllcn.com/docs/usage/)

* **问题一**：jekyll build error: Liquid Exception Failed to get header. 解决方法是卸载pygments.rb 0.5.4版本 ```sudo gem uninstall pygments.rb```，安装pygments.rb 0.5.0版本 ```sudo gem install pygments.rb --version "=0.5.0"```。参见<http://stackoverflow.com/questions/17816499/jekyll-on-windows-liquid-exception-failed-to-get-header>

* **问题二**：jekyll serve error: Address already in use - bind(2). 解决办法是关掉相应进程或重启terminal，参见<http://stackoverflow.com/questions/10261477/tcpserver-error-address-already-in-use-bind2>

* **问题三**：如果遇到gem安装失败，请到[RubyGems](http://rubygems.org/)中搜索相应package name和version，下载本地后，通过```sudo gem install <PkgName> -l```安装。

##4. 上传到Github

*4.1* 在本地新建一个folder并进行git初始化。

```
$ mkdir blog
$ cd blog
$ git init
```

*4.2* 创建一个没有父节点的分支gh-pages。因为github规定，只有该分支中的页面，才会生成网页文件。以下所有动作，都在该分支下完成。
    ```git checkout --orphan gh-pages```
    
*4.3* 将第三步中生成的内容copy到blog目录下。

*4.4* 前往github的网站，在网站上创建一个名为blog的库。接着，再将本地内容推送到github上你刚创建的库。注意，下面命令中的username，要替换成你的username。

```
git remote add origin https://github.com/pandapeng/blog.git
git push origin gh-pages
```


参考网站：

* [jekyll Official Site](http://jekyllrb.com/)

* [jekyllcn](http://jekyllcn.com/)

* [jekyllbootstrap](http://jekyllbootstrap.com/)

* [Disqus](http://disqus.com/)

* [Markdown](http://daringfireball.net/projects/markdown/)

参考文章：

* [Setting up a Ruby on Rails development environment on Mavericks](http://dean.io/setting-up-a-ruby-on-rails-development-environment-on-mavericks/)

* [使用Github Pages建独立博客](http://beiyuu.com/github-pages/)

* [搭建一个免费的，无限流量的Blog----github Pages和Jekyll入门](http://www.ruanyifeng.com/blog/2012/08/blogging_with_jekyll.html)

* [使用jeklly搭建自己的blog](http://jolestar.com/use-jekyll-as-blog/)

* [Jekyll本地调试之若干问题](http://chxt6896.github.io/blog/2012/02/13/blog-jekyll-native.html)