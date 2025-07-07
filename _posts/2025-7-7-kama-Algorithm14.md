---
layout: post
title: "链表的基础操作II"
date:   2025-7-7
tags: [Kama Algorithm]
comments: true
author: Venture-Li
---

## 题目描述

> 请编写一个程序，实现以下操作:  

> 构建一个单向链表，链表中包含一组整数数据，输出链表中的第 m 个元素（m 从 1 开始计数）。  

> 要求：  
> 1. 使用自定义的链表数据结构  
> 2. 提供一个 linkedList 类来管理链表，包含构建链表、输出链表元素以及输出第 m 个元素的方法  
> 3. 在 main 函数中，创建一个包含一组整数数据的链表，然后输入 m，调用链表的方法输出第 m 个元素  

## 输入描述

> 第一行包含两个整数 n 和 k，n 表示需要构建的链表的长度，k 代表输入的 m 的个数。  

> 接下来一行包含 n 个整数，表示链表中的元素。  

> 接下来一行包含 k 个整数，表示输出链表中的第 m 个元素。   

## 输出描述

> 测试数据输出占 k 行。  

> 每行输出链表中的第 m 个元素。如果 m 位置不合法，则输出“Output position out of bounds.”。  

## 输入示例

> 5 5  
> 1 2 3 4 5  
> 4 3 2 9 0  

## 输出示例

> 4  
> 3  
> 2  
> Output position out of bounds.  
> Output position out of bounds.  

## 题解

```c++
#include <iostream>
using namespace std;
struct ListNode
{
    int val;
    ListNode *next;
    ListNode(int x):val(x), next(nullptr){}
};
int main()
{   
    int n = 0, m = 0;
    cin>>n>>m;
    ListNode *head = new ListNode(0);
    ListNode *cur = head;
    while(n--)
    {
        int x = 0;
        cin>>x;
        ListNode *node = new ListNode(x);
        cur->next = node;
        cur = cur -> next;
    }
    while(m--)
    {
        int index = 0;
        cin>>index;
        cur = head;
        while(index--)
        {
            cur = cur->next;
            if(cur == nullptr)break;
        }
        if(cur == head || cur == nullptr)cout<<"Output position out of bounds."<<endl;
        else cout<<cur->val<<endl;
    }
    return 0;
}
```

---

## 解题技巧

关键在于取第`m`个元素，并写好判断条件

```c++
int index = 0;
cin>>index;
cur = head;
while(index--)
{
    cur = cur->next;//将cur移转到m位置
    if(cur == nullptr)break;
}
if(cur == head || cur == nullptr)cout<<"Output position out of bounds."<<endl;
else cout<<cur->val<<endl;
```

![chart](https://venture-li.github.io/images/202507071802681.png)
