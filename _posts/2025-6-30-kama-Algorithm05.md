---
layout: post
title: "卡码C++ A+B问题VIII"
date:   2025-6-30
tags: [Kama Algorithm]
comments: true
author: Venture-Li
---

## 题目描述

> 你的任务是计算若干整数的和。

## 输入描述

> 输入的第一行为一个整数N，接下来N行每行先输入一个整数M，然后在同一行内输入M个整数。

## 输出描述

> 对于每组输入，输出M个数的和，每组输出之间输出一个空行。


## 输入示例

> 3  
> 4 1 2 3 4  
> 5 1 2 3 4 5  
> 3 1 2 3   

## 输出示例

> 10  
>  
> 15  
>   
> 6  

## 提示信息

> 注意以上样例为一组测试数据，后端判题会有很多组测试数据，也就是会有多个N的输入
> 例如输入可以是：
> 3
> 4 1 2 3 4
> 5 1 2 3 4 5
> 3 1 2 3
> 3
> 4 1 2 3 4
> 5 1 2 3 4 5
> 3 1 2 3
> 输出则是
> 10
> 
> 15
> 
> 6
> 10
> 
> 15
> 
> 6
> 只保证每组数据间是有空行的。但两组数据并没有空行

## 题解

```c++
#include <iostream>
using namespace std;
int main()
{
    int n = 0;
    while(cin>>n)
    {
        while(n--)
        {
            int num = 0, sum = 0;
            cin>>num;
            while(num--)
            {
                int a = 0;
                cin>>a;
                sum += a;
            }
            
            cout<<sum<<endl;
            if(n!=0)cout<<endl;
        }
    }
    return 0;
}
```
---
## 解题技巧

本题注意输出答案空行问题，有两种思考方式

**空格+答案** or **答案+空格** ，哪个好思考用哪个
