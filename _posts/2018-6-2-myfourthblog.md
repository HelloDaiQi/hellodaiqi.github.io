---
layout: post
title:  "NullPointerException"
date:   2018-6-2 22:09:05
categories: exception
excerpt: 将自己对空指针异常的一点看法写下来
---

* content
{:toc}

## 《NullPointerException》
我们都知道java是没有指针的，这里说的"java指针"指的就是java的引用。
空指针就是空引用，java空指针异常就是引用本身为空，却调用了方法，这个时候就会出现空指针异常。
可以理解，成员变量和方法是属于对象的（除去静态），在对象中才存在相对应的成员变量和方法，然后通过对象去调用这些成员变量和方法。
对于空指针来说，它不指向任何对象，也就没有所谓的成员变量和方法，这个时候用它去调用某些属性和方法，当然会出现空指针异常。

所谓空指针异常，是因为用空（null）去调用属性或方法。null表示没有这个对象，既然没有这个对象，那么去调用他的属性和方法，就会报异常。
主要有以下几种原因：
1、使用了未初始化的变量（虽然已经声明）
2、使用了未初始化的对象（虽然已经声明）
（tip:本人测试了一下，以上两种原因再编译时就不能通过，会报局部变量未初始化错误）
3、使用了关键字或已存在的类名作变量对象方法或类名。   
（tip:这是我摘抄其他博客上的，我没看懂啥意思）
当应用程序试图在需要对象的地方使用 null 时，抛出该异常。
这种情况包括：
1、调用 null对象的实例方法。
2、访问或修改null对象的字段。
3、将null作为一个数组，获得其长度。
4、将null作为一个数组，访问或修改其时间片。
5、将null作为Throwable值抛出。
不多说了，看代码吧

    public static void main(String[] args) {
	        // 如果只声明不调用，编译是可以通过的（但是这也没啥意义了，因为根本就没用到）
	        Student student;
	        // 如果对其进行操作，编译则不能通过，报如下错误
		// The local variable student may not have been initialized
		// student.getAge();

		// 如果对其赋空值，再进行操作，编译会通过
		student = null;
		// 此处会报空指针错误，因为调用的对象本身是null（java.lang.NullPointerException）
		student.getName();

		int ceshi;
		// 局部变量只声明不定义，编译无法通过
		// The local variable ceshi may not have been initialized
		System.out.println(ceshi);
		// 对其进行赋值操作，则可以正常执行
		ceshi = 0;
		System.out.println(ceshi);

    }

###总结
空指针异常并不可怕，只要我们在编码时养成良好的变成习惯。
例如：声明变量以及对象实例时不要忘记对其进行正常初始化(不要对其进行null初始化)，
      在javaweb编程时，从前台接收到数据时可以多加一层判断是否为null的操作。