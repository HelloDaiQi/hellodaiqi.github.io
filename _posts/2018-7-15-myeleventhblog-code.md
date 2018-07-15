---
layout: post
title:  "我的第一个Java程序"
date:   2018-7-15 19:56:56
categories: code
excerpt: 我的第一个Java程序
---

* content
{:toc}

## 《我的第一个Java程序》
1.Java环境：
 在写第一个Java程序之前，要确保计算机中安装了jdk:<br/>
 ![javacode1]({{"/css/pics/myeleventhblog/javacode1.png"}})<br/>
 运行cmd，输入java -version，出现上图提示，表示jdk环境变量配置正确。

2.运行java文件的两个命令：
 (1)javac:编译java文件，使用方法：javac HelloWorld.java，如果不出错，在于HelloWorld.java同一目录下会生成
    一个HelloWorld.class文件，这个class文件是操作系统能够使用和运行的文件。
 (2)java:运行class文件，使用方法：java HelloWorld，如果不出错的话，会执行HelloWorld.class文件，注意：这里
    的HelloWorld后面不需要扩展名。
 (Tip:这里的HelloWorld是文件名，可以根据需要自己定义。)

3.编写第一个Java程序：
 在F盘下新建一个文件夹java，在此文件夹下新建一个文本文档，命名为HelloWorld，如图：<br/>
 ![javacode2]({{"/css/pics/myeleventhblog/javacode2.png"}})<br/>
 打开该文件，写入如下代码：<br/>
 ![javacode3]({{"/css/pics/myeleventhblog/javacode3.png"}})<br/>
 编写完毕后保存，将文件后缀修改为java后缀<br/>
 ![javacode4]({{"/css/pics/myeleventhblog/javacode4.png"}})

4.运行cmd，使用cd命令进入该文件所在文件夹下，如图：<br/>
 ![javacode5]({{"/css/pics/myeleventhblog/javacode5.png"}})<br/>
 使用javac命令编译java文件(编译完毕后在于java文件同一目录下会出下一个同名的class文件),紧接着使用java运行
 class文件，如图：<br/>
 ![javacode6]({{"/css/pics/myeleventhblog/javacode6.png"}})

 ![javacode7]({{"/css/pics/myeleventhblog/javacode7.png"}})

5.如此,第一个Java程序就完成啦！