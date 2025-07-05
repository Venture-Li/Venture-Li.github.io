---
layout: post
title: "位置互换"
date:   2025-7-5
tags: [Kama Algorithm]
comments: true
author: Venture-Li
---

## 题目描述

> 给定一个长度为偶数位的字符串，请编程实现字符串的奇偶位互换。

## 输入描述

> 输入包含多组测试数据。  
> 输入的第一行是一个整数n，表示有测试数据。（整个输入中，只有一个n）  
> 接下来是n组测试数据，保证串长为偶数位(串长<=50)。  

## 输出描述

> 请为每组测试数据输出奇偶位互换后的结果，每组输出占一行。  

## 输入示例

> 2  
> 0aa0  
> bb00  

## 输出示例

> a00a  
> bb00  

## 题解

```c++
#include <iostream>
#include <string>
using namespace std;
void swap(char &a, char &b)
{
    char temp = a;
    a = b;
    b = temp;
}
int main()
{
    int num = 0;
    cin>>num;
    while(num--)
    {
        string s("");
        cin>>s;
        for(int i = 0;i<s.size();i+=2)
        {
            swap(s[i],s[i+1]);
        }
        cout<<s<<endl;
    }
    return 0;
}
```

---

## 解题技巧

最简单的交换问题
