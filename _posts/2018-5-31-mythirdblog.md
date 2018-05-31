---
layout: post
title:  "农民伯伯买小鸡"
date:   2018-05-31 10:08:30
categories: arithmetics
excerpt: 一道算法面试题
---

* content
{:toc}

## 《农民伯伯买小鸡》
2018-05-30，在南京创景公司，面试时问到的一个算法问题，
在此将其记下。

public class BuyChicken {

	/**
	 * 一个农民手中有100元，想买100只鸡回来喂养， 母鸡每只5元，公鸡每只2元，小鸡每只0.25元/1一元买四只，
	 * 希望你来帮助下这位农民伯伯，给他提供集中方案
	 */
	public static void main(String[] args) {
		// 在这里，不认为小鸡的数量可以被1整出，所以需要类型强制转换
		long startTime = 0;
		long endTime = 0;

		startTime = System.currentTimeMillis();
		chicken1(100, 100, 5, 2, (double) 1 / (double) 4);
		endTime = System.currentTimeMillis();
		System.out.println("chicken1用了：" + (endTime - startTime));

		startTime = System.currentTimeMillis();
		chicken2(100, 100, 5, 2, (double) 1 / (double) 4);
		endTime = System.currentTimeMillis();
		System.out.println("chicken2用了：" + (endTime - startTime));

		startTime = System.currentTimeMillis();
		chicken3(100, 100, 5, 2, (double) 1 / (double) 4);
		endTime = System.currentTimeMillis();
		System.out.println("chicken3用了：" + (endTime - startTime));
	}

	/**
	 * 
	 * @param money总钱数
	 * @param number总的鸡的数量
	 * @param mjPrice母鸡的单价
	 * @param gjPrice公鸡的单价
	 * @param xjPrice小鸡的单价
	 */
	public static void chicken1(double money, int number, double mjPrice, double gjPrice, double xjPrice) {
		int mj, gj, xj;
		int count = 0;
		for (mj = 0; mj <= (int) Math.floor(money / mjPrice); mj++) {
			for (gj = 0; gj <= (int) Math.floor(money / gjPrice); gj++) {
				for (xj = 0; xj <= number; xj++) {
					if (xj % (1 / xjPrice) == 0) {
						if ((mj + gj + xj == number) && (mj * mjPrice + gj * gjPrice + xj * xjPrice == money)) {
							count++;
							System.out.println("方案" + count + ":母鸡：" + mj + "只，公鸡：" + gj + "只，小鸡：" + xj + "只");
						}
					}
				}
			}
		}
		System.out.println("一共" + count + "种买法");
	}

	public static void chicken2(double money, int number, double mjPrice, double gjPrice, double xjPrice) {
		int mj, gj, xj;// xj为母鸡，gj为公鸡，xj为小鸡
		int L = 0;
		for (mj = 0; mj <= (int) Math.floor(money / mjPrice); mj++) {
			for (gj = 0; gj <= (int) Math.floor(money / gjPrice); gj++) {
				xj = number - mj - gj;
				if (mj * mjPrice + gj * gjPrice + xj * xjPrice == money) {
					L++;
					System.out.println("方案" + L + ":" + "母鸡的数量为:" + mj + "," + "公鸡的数量为：" + gj + "," + "小鸡的数量为：" + xj);
				}
			}
		}
		System.out.println("一共" + L + "种买法");
	}

	public static void chicken3(double money, int number, double mjPrice, double gjPrice, double xjPrice) {
		int mj, gj, xj;
		int count = 0;
		for (mj = 0; mj <= (int) Math.floor(money / mjPrice); mj++) {
			for (gj = 0; gj <= (int) Math.floor((money - mj * mjPrice) / gjPrice); gj++) {
				for (xj = 0; xj <= (int) Math.floor((money - mj * mjPrice - gj * gjPrice) / xjPrice); xj++) {
					if ((mj + gj + xj == number) && (mj * mjPrice + gj * gjPrice + xj * xjPrice == money)) {
						count++;
						System.out.println(
								"方案" + count + ":" + "母鸡的数量为:" + mj + "," + "公鸡的数量为：" + gj + "," + "小鸡的数量为：" + xj);
					}
				}
			}
		}
		System.out.println("一共" + count + "种买法");
	}
}
