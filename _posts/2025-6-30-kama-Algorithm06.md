---
layout: post
title: "数组的倒序与隔位输出"
date:   2025-6-30
tags: [Kama Algorithm]
comments: true
author: Venture-Li
---

## 题目描述

> 给定一个整数数组，编写一个程序实现以下功能：
> 1. 将输入的整数数组倒序输出，每个数之间用空格分隔。
> 2. 从正序数组中，每隔一个单位（即索引为奇数的元素），输出其值，同样用空格分隔。

## 输入描述

> 第一行包含一个整数 n，表示数组的长度。
> 接下来一行包含 n 个整数，表示数组的元素。

## 输出描述

> 首先输出倒序排列的数组元素，然后输出正序数组中每隔一个单位的元素。


## 输入示例

> 5  
> 2 3 4 5 6  

## 输出示例

> 6 5 4 3 2  
> 2 4 6  

## 题解

```c++
#include <iostream>
using namespace std;
int main()
{
    int num = 0;
    int arry[num];
    for(int i = 0;i<num;i++)
    {
        cin>>arry[i];//语法糖
    }
    for(int i = num-1;i>=0;i--)
    {
        if(i!=num-1)cout<<" ";
        cout<<arry[i];
    }
    for(int i = 0;i<num;i+=2)
    {
        if(i!=0)cout<<" ";
        cout<<arry[i];
    }
    return 0;
}
```
```c++
#include <iostream>
#include <vector>
using namespace std;
int main()
{
    int n = 0;
    vector<int> vec1;
    cin>>n;
    while(n--)
    {
        int i = 0;
        cin>>i;
        vec1.push_back(i);
    }
    for(int i = vec1.size()-1;i>=0;i--)
    {
        if(i<vec1.size()-1)cout<<" ";
        cout<<vec1[i];    //此处很简洁，与vector不一样
    }
    cout<<endl;
    for(int i = 0;i<vec1.size();i+=2)
    {
        if(i>0)cout<<" ";
        cout<<vec1[i];
    }
    return 0;
}
```
---

## 解题技巧

根据数组大小是否固定选择是否使用vector

## 知识背景

### 数组

C++中的数组是一种用于存储相同数据类型的元素的数据结构。

数据结构的概念理解起来比较抽象，它表示了数据在计算中被组织和存储的形式，而数组呢就是一组按照一定次序排列的数值，数组中的每一个变量被称为元素。

相同数据类型的元素指的是数组中的所有元素都必须是相同的数据类型，也就是说如果创建了一个整型数组，数组里就不能有其他数据类型的存在。

数组的特点：

- 固定大小
- 相同数据类型
- 连续存储
- 下标访问
  
C++中声明数组的方式为`dataType arrayName[arraySize]`。

`dataType`表示数组元素的类型，比如`int、double、char`等。
`arrayName`是为数组指定的名称，类似于变量名称。
`arraySize`是数组的大小，即它可以容纳多少个元素。

```c++
// 声明一个包含5个整数的数组
int myArray[5];
```

C++中使用大括号 {} 初始化数组的元素，也可以逐个赋值。

```c++
// 使用大括号初始化一个长度为5的整型数组
int arr[5] = {1, 2, 3, 4, 5}; 

// 定义一个长度为3的整型数组，并逐个赋值
int arr1[3];//若为全局数组，默认初始化为0，若为局部数组，其值随机
arr1[0] = 10;
arr1[1] = 20;
arr1[2] = 30; 
```

访问数组中的元素，您可以使用下标操作符 []，请注意，下标从0开始，直到数组长度的前一位。

```c++
int value = arr[2]; // 获取数组 arr 的第三个元素的值，即 3
```

除了访问元素，还可以通过下标操作符 [] 修改数组中的元素的值。

```c++
arr[0] = 100;  // 修改数组 arr 的第一个元素的值为 100
```

使用循环结构，如 for 循环，可以遍历数组中的所有元素。

```c++
for (int i = 0; i < 5; i++) {
    cout << arr[i] << " ";
}
```

⚠️ 需要注意的是，C++中的数组没有提供自动的长度信息，因此在处理数组时必须小心，以避免访问越界的元素。

```c++
int a = arr[5]; // 数组长度为5，索引范围为0-4，如果尝试访问arr[5]，会越界访问数组范围，导致程序运行出错
```

### Vector

> **如果不清楚元素的确切个数，请使用vector**

vector （被称为容器），做为C++ 标准库中的一个容器类，表示对象的集合，它可以动态地存储一组元素，可以根据需要轻松地调整 vector 的大小。

和输入输出类似，如果想要使用vector, 必须包含头文件vector

```c++
#include <vector>
using std::vector;
```

容器的创建方式为vector<类型> 名称, 无需指明长度
```c++
vector<int> myVector; // 创建一个空vector, 元素是int类型的
```

除此之外，还有一些别的创建方式，常见的有
```c++
vector<int> myVector = {1, 2, 3, 4, 5}; // 创建一个包含整数元素的容器并初始化元素
vector<int> myVector(10); // 创建一个包含10个元素的容器，元素为int类型（值被系统默认初始化为0）
vector<int> myVector(10, -1); // 创建一个包含10个重复元素的容器，每个元素的值都是-1
```
我们已经知道，vector可以动态调整大小，这种调整是通过vector内置的方法push_back动态添加元素来实现的。

push_back()负责将一个值push（推送）到vector中的back(尾端)

```c++
vector<int> myVector = {1, 2, 3, 4, 5};
myVector.push_back(6); // 往容器的最末端添加数字6
```

与数组类似，仍然可以使用下标操作符 [] 访问 vector 中的元素

```c++
int value = myVector[0]; // 获取第一个元素的值，即 1
```
还可以使用内置的size()方法来获取容器当前的元素数量

```c++
int size = myVector.size(); // 获取vector的大小
```

在数组中，我们通过for循环完成了对数组的遍历，vector 遍历的方式是一样的。

```c++
for (int i = 0; i < myVector.size(); i++) {
    cout << myVector[i] << " "; // 从索引为0开始，遍历到i等于size的时候退出循环，完成整个遍历
}
```

此外，vector还内置了一些别的方法供我们使用：

```c++
myVector.pop_back(); // 删除vector末尾的元素
myVector.clear(); // 清空vector中的所有元素
myVector.empty(); // 判断vector是否不含有任何元素，如果长度为0，则返回真，否则，返回假
```
