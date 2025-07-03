---
layout: post
title: "卡码C++ A+B问题Ⅱ"
date:   2025-6-30
tags: [Kama Algorithm]
comments: true
author: Venture-Li
---

## 题目描述

> 计算a+b，但输入方式有所改变。

## 输入描述

> 第一行是一个整数N，表示后面会有N行a和b，通过空格隔开。

## 输出描述

> 对于输入的每对a和b，你需要在相应的行输出a、b的和。
> 如第二对a和b，对应的和也输出在第二行。


## 输入示例

> 2  
> 2 4  
> 9 21  

## 输出示例

> 6  
> 30  

## 题解

```c++
#include <iostream>
using namespace std;
int main()
{
    int num = 0;
    while(cin>>num)
    {
        while(num--)
        {
            int a = 0, b = 0;
            cin>>a>>b;
            cout<<a+b<<endl;
        }
    }
    return 0;
}
```
---
## 解题技巧

本题考查最简单的循环解除，每N行一个循环

```c++
// 使用while拿走循环,是n--不是--n
while(n--) 
{
}
// 使用for拿走循环
for(int i = 0;i<n;i++)
{
}
```

---

## 知识背景

### 数据类型转换

`while(n)`中的n会从整形转换为布尔型

有且仅有0才会转换成flase，其余均为true（如1、100、-7）

### do while补充

```c++
do
{

}while(判断条件);
```

