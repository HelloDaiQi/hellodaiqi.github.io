---
layout: post
title:  "我的第一个Kotlin程序"
date:   2018-7-15 20:48:48
categories: code
excerpt: 我的第一个Kotlin程序
---

* content
{:toc}

## 《我的第一个Kotlin程序》
1.Kotlin环境：
 在写第一个Kotlin程序之前，要确保计算机中安装了kotlin-compiler:<br/>
 ![kotlincode1]({{"/css/pics/mytwelfthblog/kotlincode1.png"}})<br/>
 运行cmd，输入kotlin -version，出现上图提示，表示kotlin环境变量配置正确。

2.Kotlin简介：<br/>
 (1)Kotlin是一种在Java虚拟机上运行的静态类型编程语言，被称之为Android世界的Swift，由JetBrains设计开发并
    开源。<br/>
 (2)Kotlin可以编译成Java字节码，也可以编译成JavaScript，方便在没有JVM的设备上运行。<br/>
 (3)在Google I/O 2017中，Google 宣布 Kotlin 成为 Android 官方开发语言。<br/> 

3.编写第一个Kotlin程序：
 在F盘下新建一个文件夹kotlin，在此文件夹下新建一个文本文档，命名为HelloWorld，如图：<br/>
 ![kotlincode2]({{"/css/pics/mytwelfthblog/kotlincode2.png"}})<br/>
 打开该文件，写入如下代码：<br/>
 ![kotlincode3]({{"/css/pics/mytwelfthblog/kotlincode3.png"}})<br/>
 编写完毕后保存，将文件后缀修改为kt后缀<br/>
 ![kotlincode4]({{"/css/pics/mytwelfthblog/kotlincode4.png"}})
 
 <br/>
4.运行cmd，使用cd命令进入该文件所在文件夹下，如图：<br/>
 ![kotlincode5]({{"/css/pics/mytwelfthblog/kotlincode5.png"}})<br/>
 使用kotlinc命令编译kt文件(编译完毕后在与kt文件同一目录下会出下一个同名的jar文件),紧接着使用java运行
 jar文件，如图：<br/>
 ![kotlincode6]({{"/css/pics/mytwelfthblog/kotlincode6.png"}})
 ![kotlincode7]({{"/css/pics/mytwelfthblog/kotlincode7.png"}})
 (Tip:-d:用来设置编译输出的名称,可以是class或jar文件,也可以是目录。-include-runtime:让jar文件包含Kotlin运行库，从而可以直接运行。)

 <br/>
5.如此,第一个Kotlin程序就完成啦！