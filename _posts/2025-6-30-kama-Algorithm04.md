---
layout: post
title: "卡码C++ A+B问题IV"
date:   2025-6-30
tags: [Kama Algorithm]
comments: true
author: Venture-Li
---

## 题目描述

> 你的任务是计算若干整数的和。

## 输入描述

> 每行的第一个数N，表示本行后面有N个数。
> 如果N=0时，表示输入结束，且这一行不要计算。

## 输出描述

> 对于每一行数据需要在相应的行输出和。


## 输入示例

> 4 1 2 3 4  
> 5 1 2 3 4 5  
> 0   

## 输出示例

> 10  
> 15  

## 题解

```c++
#include <iostream>
using namespace std;
int main()
{
    int num = 0;
    while(cin>>num)
    {
        if(num == 0)break;
        int sum = 0;
        while(num--)
        {
            int a = 0;
            cin>>a;
            sum += a;
        }
        cout<<sum<<endl;
    }
    return 0;
}
```
---
## 解题技巧

与第二题类似，固定循环解除

累加问题需要两个变量，并注意每次清零
