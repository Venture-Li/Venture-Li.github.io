---
layout: post
title: "判断集合成员"
date:   2025-7-10
tags: [Kama Algorithm]
comments: true
author: Venture-Li
---

## 题目描述

> 请你编写一个程序，判断给定的整数 n 是否存在于给定的集合中。  

## 输入描述

> 有多组测试数据，第一行有一个整数 k，代表有 k 组测试数据。  
> 每组数据第一行首先是一个正整数 m，表示集合中元素的数量（1 <= m <= 1000）。   
> 接下来一行包含 m 个整数，表示集合中的元素。    
> 最后一行包含一个整数 n，表示需要进行判断的目标整数。   

## 输出描述

> 包含多组输出，每组输出占一行。  
> 如果集合中存在 m，输出“YES”，否则输出“NO”。  

## 输入示例

> 2  
> 5  
> 1 2 3 4 5  
> 3  
> 6  
> 1 2 3 4 5 6  
> 7  

## 输出示例

> YES  
> NO    

## 题解

```c++
#include <iostream>
#include <set>
using namespace std;
int main()
{   
    int k = 0, m = 0, num = 0,n = 0;
    cin>>k;
    while(k--)
    {
        set<int> uset;
        cin>>m;
        while(m--)
        {
            cin>>num;
            uset.insert(num);
        }
        cin>>n;
        if(uset.find(n)!=uset.end())cout<<"YES"<<endl;
        else cout<<"NO"<<endl;
    }
    return 0;
}
```

---

## 解题技巧

新了解掌握set容器，以及常用的方法

## 知识背景

### 前言

之前我们讲到，哈希表的主要作用是判断给定的整数是否存在于给定的数据中, 哈希表常使用的数据结构有数组、set集合、map映射, 上节课我们学习了数组作为哈希表，这节课我们来学习set集合, 具体包括下列内容

- `set`、`unordered_set`,` multiset `的概念和特点
- `set`、`unordered_set`, `multiset `的基本操作，比如创建、插入、删除、查找
- 迭代器`iterator`

### Set

和数学中的集合一样，**C++中的集合set用于允许存储一组不重复的元素**, 并且元素的值按照**有序排列**， `set`基于红黑树实现，支持高效的关键字查询操作, 可以用来检查一个给定关键字是否在`set`中。

无序集合`unordered-set`类似于集合`（Set）`，但不会按照元素的值进行排序，而是由哈希函数的结果决定的。

`multiset` 则是一个用于存储一组元素，允许元素重复，并按照元素的值进行有序排列的集合。

![chart](https://venture-li.github.io/images/202507100042692.png)

### Set常用方式

使用集合set需要先引入头文件

```c++
// 引入<unordered_set>头文件
#include <unordered_set>
// 引入set头文件
#include <set>
```

创建一个集合的写法如下

```c++
// 创建一个存储整数的无序集合
unordered_set<int> mySet;
// 创建一个存储整数的set
set<int> mySet;
// 创建一个存储整数的 multiset
multiset<int> myMultiSet; 
```

想要向集合中插入元素需要使用`insert()`方法

```c++
 // 向集合中插入元素
mySet.insert(1);
mySet.insert(2);
mySet.insert(3);
```

想要往集合中删除元素需要使用`erase`方法

```c++
mySet.erase(1);
```

`find()`方法用于查找特定元素是否存在于集合中，**如果`find()`方法找到了要查找的元素，它会返回指向该元素的迭代器，如果未找到要查找的元素，它会返回一个指向集合的 `end()`的迭代器，表示未找到**。通过比较`find()`方法返回的迭代器是否等于 `end()`，可以确定集合中是否有查找的元素。

```c++
// 判断元素是否在集合中, 只要不等于end(), 说明元素在集合中
if (mySet.find(i) != mySet.end()) {
}
```

### 迭代器iterator

迭代器`iterator`提供了一种类似**指针**的接口，可以用来遍历访问容器（比如数组、集合）中的元素，并执行各种操作。

> 可以理解为，迭代器和下标运算符的作用一样，用来访问容器中的元素，并且迭代器可以从一个元素移动到另外一个元素。

迭代器都拥有名为`begin()`和`end()`的成员，表示指向第一个元素和最后一个元素的下一个元素的迭代器（尾后迭代器），如果容器为空，则begin和end返回的是同一个迭代器。

可以使用比较运算符来判断两个迭代器是否相等，如果迭代器想要从一个元素移动到另外一个元素，**可以使用递增++运算符和递减--运算符**，表示向前（后）移动一个位置。

通过解引用`*`可以获取迭代器所指的对象，下面的示例表示了`vector`的遍历。

```c++
#include <iostream>
#include <vector>
using namespace std; 

int main() {
    vector<int> myVector = {1, 2, 3, 4, 5};

    // 使用迭代器遍历容器
      // vector<int>::iterator it  用于创建一个能读取<vector>int 元素的迭代器it，最初指向begin()
      // ++it表示迭代器的移动
      //使用auto也很爽，关键要记住迭代器是一种特殊类型
    for (vector<int>::iterator it = myVector.begin(); it != myVector.end(); ++it) {
        cout << *it << " "; // 通过解引用获取迭代器所指的对象
    }

    cout << endl; 

    return 0;
}
```
