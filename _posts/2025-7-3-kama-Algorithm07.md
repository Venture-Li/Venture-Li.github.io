---
layout: post
title: "摆平积木"
date:   2025-7-3
tags: [Kama Algorithm]
comments: true
author: Venture-Li
---

## 题目描述

> 小明很喜欢玩积木。一天，他把许多积木块组成了好多高度不同的堆，每一堆都是一个摞一个的形式。然而此时，他又想把这些积木堆变成高度相同的。但是他很懒，他想移动最少的积木块来实现这一目标，你能帮助他吗？
> ![Building blocks](https://venture-li.github.io/images/202507031541113.png)

## 输入描述

> 输入包含多组测试样例。每组测试样例包含一个正整数n，表示小明已经堆好的积木堆的个数。
> 接着下一行是n个正整数，表示每一个积木堆的高度h，每块积木高度为1。其中1<=n<=50,1<=h<=100。
> 测试数据保证积木总数能被积木堆数整除。
> 当n=0时，输入结束。

## 输出描述

> 对于每一组数据，输出将积木堆变成相同高度需要移动的最少积木块的数量。
> 在每组输出结果的下面都输出一个空行。


## 输入示例

> 6  
> 5 2 4 1 7 5  
> 0  

## 输出示例

> 5

## 题解

```c++
#include <iostream>
#include <vector>
using namespace std;
int main()
{
    int num = 0, val = 0;
    while(cin>>num)
    {
        if(num == 0)break;
        vector<int> vec;
        int sum = 0, result = 0;
        for(int i = 0;i<num;i++)
        {
            cin>>val;
            vec.push_back(val);
            sum += val;
        }
        sum /= num;
        for(int i = 0;i<num;i++)
        {
            if(vec[i]<sum)result += sum-vec[i];
        }
        cout<<result<<endl<<endl;
    }
    return 0;
}
```

---

## 解题技巧

简单的模拟，想到求解方法搭配数组知识求解即可

> 懒惰的小明



