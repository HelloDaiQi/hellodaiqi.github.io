---
layout: post
title:  "ArrayIndexOutOfBoundsException"
date:   2018-6-3 15:29:20
categories: exception
excerpt: 将自己对数组下标越界异常的看法写下来
---

* content
{:toc}

## 《ArrayIndexOutOfBoundsException》
这是一个非常常见的异常，从名字上看是数组下标越界错误,
当你使用不合法的索引访问数组时会报数组越界这种错误，数组arr的合法错误范围是[0, arr.length-1];
当你访问这之外的索引时会报这个错，例如：如果索引为负或大于等于数组大小，则该索引为非法索引。
实际上，集合的不合法访问也会报这种错误，例如ArrayList(因为它就是基于数组来存储数据的)。

解决办法也很简单，找到报错信息，查看自己对数组的操作是否超过了数组的允许范围。

    import java.util.ArrayList;
    import java.util.List;

    public class ArrayIndexOutOfBoundsException {

	public static void main(String[] args) {
		// java.lang.ArrayIndexOutOfBoundsException
		// 这里定义了一个大小为3的整型数组，数组下标为0~2
		int[] arr = new int[3];
		// 在这里我对数组的第四个元素进行操作，超出了数组的范围，会报错
		System.out.println(arr[3]);
		// 在使用for循环对数组进行遍历操作时，不合法的下标也会引起这个错误
		for (int i = 0; i <= arr.length; i++) {
			// 当循环进入最后一层时，会报错，因为数组下标越界了
			System.out.println(arr[i]);
		}
		// 正常的遍历方式如下：
		for (int i = 0; i < arr.length; i++) {
			System.out.println(arr[i]);
		}

		// 集合的情况和数组基本相似，这里不做过多解释
		List list = new ArrayList();
		// 正常的遍历方式如下：
		for (int i = 0; i < list.size(); i++) {
			System.out.println(list.get(i));
		}

		// 补充
		// java.lang.OutOfMemoryError: Requested array size exceeds VM limit
		try {
			int len = Integer.MAX_VALUE;
			int largArray[] = new int[len];
			System.out.println(len);
		} catch (OutOfMemoryError e) {
			e.printStackTrace();
		}
	}
    }

###补充
如果创建的数组过大，则会产生内存溢出错误。
（tip:这个问题的解释以后补充）