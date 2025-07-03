---
layout: post
title: "打印正方形"
date:   2025-7-3
tags: [Kama Algorithm]
comments: true
author: Venture-Li
---

## 题目描述

> 编写一个程序，模拟打印一个正方形的框。程序应该接受用户输入的正整数作为正方形的边长，并打印相应大小的正方形框。 请注意，内部为空白，外部是由 "*" 字符组成的框。  

## 输入描述

> 输入只有一行，为正方形的边长 n  

## 输出描述

> 输出正方形组成的框  

## 输入示例

> 5  

## 输出示例

> `******`  
> `*`&emsp; `*`  
> `*`&emsp; `*`  
> `*`&emsp; `*`  
> `******`  




## 题解

```c++
#include <iostream>
using namespace std;
int main()
{
    int n = 0;
    cin>>n;
    for(int i = 0;i<n;i++)
    {
        for(int j = 0;j<n;j++)
        {
            if(i==0 || i==n-1 || j==0 ||j==n-1)cout<<'*';
            else cout<<' ';
        }
        cout<<endl;
    }
}
```

---

## 解题技巧

若题目要求输出二维类型，考虑使用二维数组（循环嵌套）+控制条件

```c++
for(int i = 0;i<n;i++)
{
    for(int j = 0;i<m;j++>)
    {

    }
}
```


