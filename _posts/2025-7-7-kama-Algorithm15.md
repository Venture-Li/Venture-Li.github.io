---
layout: post
title: "链表的基本操作III"
date:   2025-7-7
tags: [Kama Algorithm]
comments: true
author: Venture-Li
---

## 题目描述

> 请编写一个程序，实现以下链表操作：构建一个单向链表，链表中包含一组整数数据。  
> 1. 实现在链表的第 n 个位置插入一个元素，输出整个链表的所有元素。  
> 2. 实现删除链表的第 m 个位置的元素，输出整个链表的所有元素。  
> 要求：  
> 1. 使用自定义的链表数据结构。  
> 2. 提供一个 linkedList 类来管理链表，包含构建链表、插入元素、删除元素和输出链表元素的方法。  
> 3. 在 main 函数中，创建一个包含一组整数数据的链表，然后根据输入的 n 和 m，调用链表的方法插入和删除元素，并输出整个链表的所有元素。  

## 输入描述

> 每次输出只有一组测试数据。  
> 每组的第一行包含一个整数 k，表示需要构建的链表的长度。  
> 第二行包含 k 个整数，表示链表中的元素。  
> 第三行包含一个整数 S，表示后续会有 S 行输入，每行两个整数，第一个整数为 n，第二个整数为 x ，代表在链表的第 n 个位置插入 x。  
> S 行输入...  
> 在 S 行输入后，后续会输入一个整数 L，表示后续会有 L 行输入，每行一个整数 m，代表删除链表中的第 m 个元素。  
> L 行输入...  

## 输出描述

> 包含多组输出。  
> 每组第一行输出构建的链表，链表元素中用空格隔开，最后一个元素后没有空格。  
> 然后是 S 行输出，每次插入一个元素之后都将链表输出一次，元素之间用空格隔开，最后一个元素后没有空格；  
> 如果插入位置不合法，则输出“Insertion position is invalid.”。  
> 然后是 L 行输出，每次删除一个元素之后都将链表输出一次，元素之间用空格隔开，最后一个元素后没有空格；如果删除元素后链表的长度为0，则不打印链表。  
> 如果删除位置不合法，则输出“Deletion position is invalid.”。  
> 如果链表已经为空，执行删除操作时不需要打印任何数据。  
> 链表为空的时候，不打印  

## 输入示例

> 5  
> 1 2 3 4 5  
> 3  
> 4 3  
> 3 4  
> 9 8  
> 2  
> 1  
> 0  

## 输出示例

> 1 2 3 3 4 5  
> 1 2 4 3 3 4 5  
> Insertion position is invalid.  
> 2 4 3 3 4 5  
> Deletion position is invalid.   

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
    int n = 0;
    cin>>n;
    ListNode *head = new ListNode(0);
    ListNode *cur  = head;
    for(int i = 0;i<n;i++)//构建链表
    {
        int x = 0;
        cin>>x;
        ListNode *p = new ListNode(x);
        cur->next = p;
        cur = cur->next;
    }
    int add = 0, a = 0, b = 0;
    cin>>add;
    while (add--)
    {

        cur = head;
        cin>>a>>b;
        if(a<1||a>n)//使用一个全局变量n维护链表长度，远简单于判断指针
        {
            cout<<"Insertion position is invalid."<<endl;
            continue;
        }
        else
        {
            for(int i = 0;i<a-1;i++)
            {
                cur = cur->next;
            }
            ListNode *temp = new ListNode(b);
            temp->next = cur->next;
            cur->next = temp;
            n++;
        }
        cur = head;
        while(cur->next!=nullptr)
        {
            cout<<cur->next->val<<" ";
            cur = cur->next;
        }
        cout<<endl;
    }
    int sub = 0;
    cin>>sub;
    while(sub--)
    {
        int L = 0;
        cin>>L;
        cur = head;
        for(int i = 0;i<L-1;i++)
        {
            cur = cur->next;
        }
        if(L <= 0 || cur->next == nullptr)//!!!
        {
            cout<<"Deletion position is invalid."<<endl;
        }
        else if(head->next == nullptr)break;
        else
        {
            cur->next = cur->next->next;
            cur = head;
            n--;
            while(cur->next!=nullptr)
            {
                cout<<cur->next->val<<" ";
                cur = cur->next;
            }
            if(head->next!=nullptr)cout<<endl;//!!!，模块化
        }
    }
    return 0;
}
```

---

## 解题技巧

掌握链表增/删操作，明确判断条件 

### 插入链表

![chart](https://venture-li.github.io/images/202507072102853.png)

### 删除链表

![chart](https://venture-li.github.io/images/202507072103603.png)
