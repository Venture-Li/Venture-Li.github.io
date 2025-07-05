---
layout: post
title: "句子缩写"
date:   2025-7-5
tags: [Kama Algorithm]
comments: true
author: Venture-Li
---

## 题目描述

> 输出一个词组中每个单词的首字母的大写组合。  

## 输入描述

> 输入的第一行是一个整数n，表示一共有n组测试数据。（输入只有一个n，没有多组n的输入）
> 接下来有n行，每组测试数据占一行，每行有一个词组，每个词组由一个或多个单词组成；每组的单词个数不超过10个，每个单词有一个或多个大写或小写字母组成；
> 单词长度不超过10，由一个或多个空格分隔这些单词。

## 输出描述

> 请为每组测试数据输出规定的缩写，每组输出占一行。

## 输入示例

> 1  
> ad dfa     fgs  

## 输出示例

> ADF   

## 题解

```c++
#include <iostream>
#include <string>
using namespace std;
char getbig(char &c)
{
    if(c>='a'&&c<='z')return c-32;
    else return c;
}
int main()
{
    int n = 0;
    cin>>n;
    getchar();
    while(n--)
    {
        string result("");
        string s("");
        getline(cin,s);
        for(int i = 0;i<s.size();i++)
        {
            if(i==0)result += getbig(s[0]);
            else
            {
                if(s[i-1]==' '&& s[i]!=' ') result += getbig(s[i]);
            }
        }
        cout<<result<<endl;
    }
    return 0;
}
```

---

## 解题技巧

getline使用时注意遗留回车符问题;以及熟练掌握字符与ASCII码的运用，谨记小写比大写多32

![ASCII](https://venture-li.github.io/images/202507051427726.png)

```c++
if(c>='a'&&c<='z')
{//大小写转换
  return c-32;
}
```
