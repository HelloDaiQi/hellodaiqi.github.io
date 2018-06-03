---
layout: post
title:  "带权中位数算法"
date:   2018-05-27 13:28:30
categories: arithmetics
excerpt: 一道算法笔试题
---

* content
{:toc}

## 《带权中位数算法》

 如图![zp1526885428622]({{"/css/pics/mysecondblog/zp1526885428622.jpg"}})
     ![zp1526882540030]({{"/css/pics/mysecondblog/zp1526882540030.jpg"}}) 

废话不多说，下面就是我的代码实现：
/**因为包的存在
 * 如果要在cmd下运行该文件，先要在basic6下使用javac FindMdlLnArray5.java进行编译
 * 然后再包的上一层目录使用java com.daiqi.basic6进行运行
 * */
	
	package com.daiqi.basic6;

	//根据权值求中间值
	public class FindMdlLnArray5 {

	public static void main(String[] args) {
	//	double []num = {0.5,1.24,18,1.4,2.1,3.2,2.5,13,2.6,18,2.55,1.2,1.83,1.3,2.1};
	//	double []weight = {0.8,0.2,1.98,1.4,2.1,3.8,2.1,2.12,0.5,5.6,1.1,1.2,3.5,1.2,1.5};
	
		double[] num = new double[] {6000,7000,8000,9000,30000};
		double[] weight = new double[] {100,50,40,5,3};
		double total = 0.0;
		double mid = 0.0;
		for (int i = 0; i < num.length; i++){
		for (int j = 1; j < num.length - i; j++){
			
			if (num[j - 1] > num[j]){
			double k = num[j - 1];
			num[j - 1] = num[j];
			num[j] = k;
			
			k = weight[j - 1];
			weight[j - 1] = weight[j];
			weight[j] = k;
		    }
		}  
	    }
		
		for(int i=0;i<weight.length;i++) {
			total+=weight[i];
		}
		mid = total/2;
		
		for(int i=0;i<weight.length;i++) {
			double temp=0.0;
			for(int j=0;j<=i;j++) {
				temp+=weight[j];
			}
			if(temp>=mid) {
				System.out.println(num[i]);
				break;
			}
		}
	    }
	}

/**
 * 由于JDK是国际版的，在编译的时候，如果我们没有用-encoding参数指定我们的JAVA源程序的编码格式，
 * 则javac.exe首先获得我们操作系统默认采用的编码格式，也即在编译java程序时，若我们不指定源程序文件的编码格式，
 * JDK首先获得操作系统的file.encoding参数(它保存的就是操作系统默认的编码格式，如WIN2k，它的值为GBK)，
 * 然后JDK就把我们的java源程序从file.encoding编码格式转化为JAVA内部默认的UNICODE格式放入内存中。
 * 然后，javac把转换后的unicode格式的文件进行编译成.class类文件，此时.class文件是UNICODE编码的，它暂放在内存中，
 * 紧接着，JDK将此以UNICODE编码的编译后的class文件保存到我们的操作系统中形成我们见到的.class文件。
 * 对我们来说，我们最终获得的.class文件是内容以UNICODE编码格式保存的类文件，它内部包含我们源程序中的中文字符串，
 * 只不过此时它己经由file.encoding格式转化为UNICODE格式了。当我们不加设置就编译时，相当于使用了参数：javac -encoding gbk XX.java，
 * 当然就会出现不兼容的情况。
 *
 * 解决办法是：应该使用-encoding参数指明编码方式：javac -encoding UTF-8 XX.java，这下没警告了，运行也正确了
 * 在JCreator 4中设置：菜单：Configure --> Options --> JDK Tools --> Compiler，选中<Default>，
 * 然后选Edit，Parameters里面，最前面添加：-encoding UTF-8。
 */
