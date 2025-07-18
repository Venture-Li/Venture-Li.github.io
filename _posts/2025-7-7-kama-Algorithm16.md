---
layout: post
title: "出现频率最高的字母"
date:   2025-7-7
tags: [Kama Algorithm]
comments: true
author: Venture-Li
---

## 题目描述

> 给定一个只包含小写字母的字符串，统计字符串中每个字母出现的频率，并找出出现频率最高的字母，如果最高频率的字母有多个，输出字典序靠前的那个字母。  

## 输入描述

> 包含多组测试数据，每组测试数据占一行。   

## 输出描述

> 有多组输出，每组输出占一行。 

## 输入示例

> 2  
> abcdeef  
> aabbccddeeff  

## 输出示例

> e  
> a   

## 题解

```c++
#include <iostream>
#include <string>
using namespace std;
int main()
{   
    int n = 0;
    string s("");
    while(cin>>n)
    {
        getchar();
        while(n--)
        {
            int arry[26]={0};
            int max = 0; 
            char result = 0;
            getline(cin,s);
            for(auto i:s)
            {
                arry[i-'a']++;
            }
            for(int i = 0;i<26;i++)//哈希表-数组
            {
                if(arry[i]>max)
                {//内容与下表联系
                    max = arry[i];
                    result = i+'a';
                }
            }
            cout<<result<<endl;
        }  
    }
    return 0;
}
```

---

## 解题技巧

解题关键要有哈希表思想，并灵活运用`char`与`int`之间的转换运算关系（可根据要求转换）  

若要求输出是char，则运算结果必须归到char类型

![chart](https://venture-li.github.io/images/202507071851202.png)

## 知识背景

### 前言


我们已经学习了数组、字符串、链表等数据结构，如果我们想要找到其中某个元素或者节点，需要从索引为0的位置或者表头开始，逐一进行比较，直到找到相等的位置或者末尾才会结束。

那是否可以避免之前的比较，直接通过要查找的记录直接找到其存储位置呢？

是有的，可以通过“哈希表”来实现，哈希表是根据关键码key的值而直接进行访问的数据结构。

**哈希表的作用是快速判断一个元素是否出现在集合**里，它的核心思想是在关键码和存储位置之间建立一个确定的对应关系f, 使得每个关键字key对应一个存储位置，而这个对应关系，称之为**散列函数（哈希函数）**。

其实数组就是一张哈希表，哈希表中关键码就是数组的索引下标，然后通过下标直接访问数组中的元素。

哈希表来解决问题的时候，一般选择以下三种数据结构。

- 数组
- set集合
- map映射

### 哈希表

哈希表可以将其比喻为一个大抽屉，抽屉里面有很多小格子。每个格子可以用来存放一些东西。

- **抽屉编号：** 抽屉有编号，这个编号就是数据的key，我们通过这个key来找到对应的抽屉。
- **散列函数：** 哈希表使用一种特殊的函数（哈希函数），来决定数据应该放在哪个抽屉里。这个函数将数据的名字key转换成一个数字，然后根据这个数字来选择一个抽屉。
- **抽屉里的物品：** 在每个抽屉里，可以放一些东西，这些东西就是我们要存储的数据。
- **解决冲突：** 有时候不同的key经过散列函数后可能会得到相同的编号，这就是冲突。哈希表有方法来处理这些冲突。
- **快速查找：** 当我们需要找到某个数据时，哈希表可以通过名字key快速地找到对应的抽屉，然后取出里面的数据，这个操作非常快速，就像从抽屉中拿出东西一样。
