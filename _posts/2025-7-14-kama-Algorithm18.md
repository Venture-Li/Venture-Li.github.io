---
layout: post
title: "开房门"
date:   2025-7-14
tags: [Kama Algorithm]
comments: true
author: Venture-Li
---

## 题目描述

> 假设你手里有一串钥匙，这串钥匙上每把钥匙都有一个编号，对应着一个房门的编号。现给你一个房门编号，你需要判断是否能够打开该房门。

## 输入描述

> 测试数据共有多组。  
> 第一行为一个整数 s，表示共有多少组测试数据。  
> 每组第一行有一个整数 n，表示钥匙串上有多少把钥匙。  
> 后面共有 n 行输入，每行两个整数，第一个整数 k 表示钥匙编号，第二个整数 d 表示房门编号。  
> 最后一行有一个整数 x，表示需要打开的房门编号。  

## 输出描述

> 有多组输出，每组输出占一行。 

## 输入示例

> 2  
> abcdeef  
> aabbccddeeff  

## 输出示例

> e  
> a   

## 题解

```c++
// #include <iostream>
// #include <vector>
// using namespace std;
// int main()
// {
//     int s = 0, n = 0;
//     cin>>s;
//     while(s--)
//     {
//         vector<int> vec1;
//         vector<int> vec2;
//         cin>>n;
//         for(int i = 0;i<n;i++)
//         {
//             int a = 0, b = 0;
//             cin>>a>>b;
//             vec1.push_back(a);
//             vec2.push_back(b);
//         }
//         int x = 0;
//         cin>>x;
//         for(int i = 0;i<n;i++)
//         {
//             if(vec2[i] == x){cout<<vec1[i]<<endl;break;}
//             if(i == n-1)cout<<"Can't open the door."<<endl;
//         }
//     }
//     return 0;
// }
#include <iostream>
#include <unordered_map>
#include <map>
using namespace std;
int main()
{
    int s = 0, n = 0, key = 0, door = 0;
    cin>>s;
    while(s--)
    {   
        int flag = 0;
        cin>>n;
        unordered_map<int,int> umap;
        while(n--)
        {
            cin>>key>>door;
            umap[door] = key;
        }
        int x = 0;
        cin>>x;
        for(const pair<int,int>& KV : umap)
        {
            if(KV.first == x)
            {
                cout<< KV.second << endl;
                flag = 1;
                break;
            }
        }
        if(!flag)cout<< "Can't open the door." << endl;
    }
    return 0;
}
```

---

## 解题技巧

很明显的字典，需要掌握`map`容器数据类型

## 知识背景

### map容器介绍

我们常常把`map`称之为映射，就是将一个元素（通常称之为`key`键）与一个相对应的值（通常称之为`value`）关联起来，比如说一个学生的姓名（`key`）有与之对应的成绩(`value`)，它们是一一对应的，就好像一把钥匙开一扇门，在`map`中键是唯一的，也只有一个唯一的确定的值。

在C++中，`map`提供了以下三种数据结构，其底层实现以及优劣如下表所示：

> map中的键是唯一的，但是multimap则没有此限制

![chart](https://venture-li.github.io/images/202507141524183.png)

`std::unordered_map` 的`key`值存储是**无序**的，底层实现为**哈希表**，查找速度更快，如果不需要排序而只是快速查找键对应的值，可以考虑使用。

`std::map` 和`std::multimap` 的底层实现是红黑树，它的`key`值存储是**有序**的，如果需要对键值对进行自定义排序，可以考虑使用`std::map`。

### map的使用

使用映射容器需要引入头文件`<unordered_map>`或者`<map>`

```c++
// 引入unordered_map头文件，包含unordered_map类型
#include <unordered_map>
// 引入map头文件，包含map类型和multimap类型
#include <map>
```

想要声明`map`映射关系，需要指定键的类型和值的类型。

```c++
// 声明一个整数类型映射到整数类型的 无序映射
unordered_map<int, int> uMap;
// 声明一个将字符串映射到整数的`map`，可以这样声明：
map<string, int> myMap;
```

想要插入键值对`key-value`, 需要使用`insert()`函数或者使用`[]`操作符来插入。如果键不存在，`[]`操作符将会创建一个新的键值对，将其插入到`map`中，并将值初始化为默认值（对于整数来说，默认值是**0**）。

```c++
uMap[0] = 10;
uMap[10] = 0;
myMap["math"] = 100;
myMap["english"] = 80;
```

和`set`类似，可以使用`find`函数来检查某个键是否存在于`map`中，它会返回一个**迭代器**。如果键存在，迭代器指向该键值对，否则指向map的末尾。

```c++
if (myMap.find("math") != myMap.end()) {
    // 键存在
} else {
    // 键不存在
}
```

你可以使用范围`for`循环来遍历`map`中的所有键值对，进行各种操作。

```c++
for(const pair<int,int>& kv:umap) {
  
}
```

当使用范围`for`循环遍历`map`时，我们需要声明一个变量`kv`来存储每个键值对。这个变量的类型通常是`pair`**类型**，下面就让我们详细解释一下`const pair<int,int>& kv:umap`

`const`用于声明一个**不可修改**的变量，这意味着一旦变量被初始化，就不能再修改其值。常量通常用大写字母表示

因为`const`声明的变量一旦创建后就无法修改值，所以**必须初始化**。

在这里，`const`关键字表示你**只能读取容器中的元素，而不能修改**它们。

而`pair<int, int>`定义了kv也就是键值对的数据类型是`pair`, C++中的`pair`类型会将两个不同的值组合成一个单元， 常用于存储键值对，创建`pair`的时候，也必须提供两个类型名，比如上面的`pair`对象，两个值的类型都是`int`， 在使用时通过`first` 和 `second` 成员来访问 `pair` 中的第一个和第二个元素, 它的 `first` 成员存储键，而 `second` 成员存储值。

`&`：这个符号表示`kv`是一个引用（`reference`），而不是值的拷贝, 如果不使用引用的话，那在每次循环迭代中都会重新创建一个新的`pair`对象来复制键值对，而这会导致不必要的内存分配和拷贝操作。

### 范围for循环(C++11)

C++11引入了范围`for`循环，用于更方便地遍历容器中的元素。这种循环提供了一种简单的方式来迭代容器中的每个元素，而不需要显式地使用迭代器或索引。

```c++
for (类型 变量名 : 容器) {
    // 在这里使用一个变量名，表示容器中的每个元素
}
```

比如下面的代码就表示使用范围`for`循环遍历一个容器

```c++
std::vector<int> numbers = {1, 2, 3, 4, 5};

// 使用范围for循环遍历向量中的元素
for (int num : numbers) {
    std::cout << num << " ";
}
```

范围`for`循环**不会修改容器中的元素**，它只用于读取元素。如果需要修改容器中的元素，需要使用传统的`for`循环或其他迭代方式。

此外，还可以使用`auto`关键字来让编译器自动推断元素的类型，这样代码会更通用

```c++
// 使用auto关键字自动推断元素的类型
for (auto num : numbers) {
    std::cout << num << " ";
}
```

## 总结
到此，哈希表的三种实现，数组、set, map的基本使用都已经全部讲解完了，哈希表有三种实现，那什么时候用数组，什么时候用set，什么时候用map呀，这个问题，在后面去刷代码随想录的 哈希表章节时，就会了解的更深入了。
