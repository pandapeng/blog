---
layout: post
title:  "How to install Appium on Mac"
date:   2014-08-29 10:53:47
categories: Automation Appium
---


* Install node.js
    * Download Mac installer of node.js. [Click to download](http://nodejs.org/dist/v0.10.31/node-v0.10.31.pkg)
    * After downloading is finished successfully, click to install it.
    * Because node istallation needs root permission, I have to modify node's permissions as below:
        * Change the owner of `node`: 
        ```
            $ cd /usr/local/lib 
            $ sudo chown -R <username> node_modules
        ```
        * Find `npm` and change its owner:
        ```
            $ which npm
            $ cd /usr/local/bin
            $ sudo chown -R <username> npm
        ```
* `npm install -g appium`
* `appium -v` to check if installation is successful or not.
* `appium-doctor` to check if ios or android setup is ok or not.
* `appium &` to start appium. Open browser to access http://0.0.0.0:4723/ to check if the text *That URL did not map to a valid JSONWP resource* is displayed.
* `npm install wd` # **I don't know the purpose here yet**



References:
* [appium踩过的坑](http://blog.csdn.net/wirelessqa/article/details/29188665)
* [Mac OS 上设置 JAVA_HOME](http://han.guokai.blog.163.com/blog/static/136718271201301183938165/)
