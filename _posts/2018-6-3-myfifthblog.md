---
layout: post
title:  "音乐研究"
date:   2018-6-3 13:23:10
categories: arithmetics
excerpt: 对两段音乐进行比较，找出最接近的一段
---

* content
{:toc}

## 《音乐研究》
链接：https://www.nowcoder.com/acm/contest/5/B
来源：牛客网

美团外卖的品牌代言人袋鼠先生最近正在进行音乐研究。他有两段音频，每段音频是一个表示音高的序列。现在袋鼠先生想要在第二段音频中找出与第一段音频最相近的部分。

具体地说，就是在第二段音频中找到一个长度和第一段音频相等且是连续的子序列，使得它们的 difference 最小。两段等长音频的 difference 定义为：
difference = SUM(a[i] - b[i])2 (1 ≤ i ≤ n),其中SUM()表示求和
其中 n 表示序列长度，a[i], b[i]分别表示两段音频的音高。现在袋鼠先生想要知道，difference的最小值是多少？数据保证第一段音频的长度小于等于第二段音频的长度。

输入描述:

第一行一个整数n(1 ≤ n ≤ 1000)，表示第一段音频的长度。
第二行n个整数表示第一段音频的音高（0 ≤ 音高 ≤ 1000）。
第三行一个整数m(1 ≤ n ≤ m ≤ 1000)，表示第二段音频的长度。
第四行m个整数表示第二段音频的音高（0 ≤ 音高 ≤ 1000）。

输出描述:

输出difference的最小值

示例：
* 输入：
** 2
** 1 2
** 4
** 3 1 2 4
* 输出：
** 0

我的看法：
我觉得可以把这个问题简化一下，把两段音乐看成两个数组，
每个数组里都有值，且第一个数组的长度比第二个数组长度小，
对两个数组进行比较，找出最接近的一段。
例如：一个数组长度为4，另一个数组长度为2，则它们只要比较4-2+1=3次就够了
看我画的图：
![illustration]({{"/css/pics/myfifthblog/illustration.png"}})

接下来，看代码实现：
    
    import java.util.Scanner;

    public class Main2 {

	public static void main(String[] args) {
		Scanner in = new Scanner(System.in);

		int m = in.nextInt();
		int[] arrm = new int[m];
		for (int i = 0; i < arrm.length; i++) {
			arrm[i] = in.nextInt();
		}

		int n = in.nextInt();
		int[] arrn = new int[n];
		for (int i = 0; i < arrn.length; i++) {
			arrn[i] = in.nextInt();
		}

		int difference = Integer.MAX_VALUE;
		// System.out.println(difference);

		// 1<=m<=n<=1000
		// 总共需要比较n-m+1次就够了
		for (int i = 0; i <= n - m; i++) {
			int k = i;
			int temp = 0;
			// 将arr数组依次与brr数组进行比较
			for (int j = 0; j < m; j++) {
				temp += (arrm[j] - arrn[k]) * (arrm[j] - arrn[k]);
				k++;
			}
			if (difference > temp) {
				difference = temp;
			}
		}
		System.out.println(difference);
	}
    }