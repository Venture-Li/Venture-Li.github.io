---
layout: post
title: "奇怪的信"
date:   2025-7-3
tags: [Kama Algorithm]
comments: true
author: Venture-Li
---

## 题目描述

> 有一天, 小明收到一张奇怪的信, 信上要小明计算出给定数各个位上数字为偶数的和。  
> 例如：5548，结果为12，等于 4 + 8 。  
> 小明很苦恼，想请你帮忙解决这个问题。  

## 输入描述

> 输入数据有多组。每组占一行，只有一个整整数，保证数字在32位整型范围内。  

## 输出描述

> 对于每组输入数据，输出一行，每组数据下方有一个空行。  

## 输入示例

> 415326  
> 3262  

## 输出示例

> 12  
>   
> 10  

## 题解

```c++
#include <iostream>
using namespace std;
int main()
{
    int num = 0;
    while(cin>>num)
    {
        int result = 0, part = 0;
        while(num != 0)
        {
            if( (num%10)%2 == 0)result+=num%10;
            num /= 10;
        }
        cout<<result<<endl<<endl;
    }
    return 0;
}
```

---

## 解题技巧

乾象投资面试题弱化版，关键为用 `while % /`处理一个整数的各个位

```c++
while(num != 0)
    {
        part = num%10;//取余数
        num /= 10;    //先取余再舍位
    }
```

## 题目分析

题目要求我们计算出给定数各个位上数字为偶数的和。

单个数字不像数组可以遍历取到每一位的值，但是可以通过取模运算和整数除法来分解一个整数并获取其各位数字，主要的过程有以下两步：

- 通过取余num % 10获取最后一位数字，%表示取模/取余运算，即一个整数除以另一个整数后的余数，最后一位是个位，无法被10整除，所以就成了余数，进而可以通过%取余运算取到。
- 使用整数除法 number /= 10 来去掉 number 的最后一位数字。这个过程会一直重复，直到 number 变成0为止。

![compute](https://venture-li.github.io/images/202507031604595.png)
