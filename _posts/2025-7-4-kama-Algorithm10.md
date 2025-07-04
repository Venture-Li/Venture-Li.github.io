---
layout: post
title: "平均绩点"
date:   2025-7-4
tags: [Kama Algorithm]
comments: true
author: Venture-Li
---

## 题目描述

> 每门课的成绩分为A、B、C、D、F五个等级，为了计算平均绩点，规定A、B、C、D、F分别代表4分、3分、2分、1分、0分。  

## 输入描述

> 有多组测试样例。每组输入数据占一行，由一个或多个大写字母组成，字母之间由空格分隔。

## 输出描述

> 每组输出结果占一行。如果输入的大写字母都在集合｛A,B,C,D,F｝中，则输出对应的平均绩点，结果保留两位小数。否则，输出“Unknown”。 

## 输入示例

> A B C D F  
> B F F C C A  
> D C E F  

## 输出示例

> 2.00  
> 1.83  
> Unknown  




## 题解

```c++
#include <iostream>
#include <string>
using namespace std;
int main()
{
    string s("");
    while(getline(cin,s))
    {
        bool flag = true;
        float sum = 0,avage = 0;
        for(int i = 0;i<s.size();i++)
        {
            if(s[i] == 'A')sum += 4;
            else if(s[i] == 'B')sum += 3;
            else if(s[i] == 'C')sum += 2;
            else if(s[i] == 'D')sum += 1;
            else if(s[i] == 'F')sum += 0;
            else if(s[i] == ' ')continue;
            else {cout<<"Unknown"<<endl;flag = false;break;}
        }
        if(flag)
        {
            avage = sum/((s.size()+1)/2);
            printf("%.2f\n",avage);
        }
    }
    return 0;
}
```

---

## 解题技巧

开始引入cin(geiline)输入字符串处理；注意size不计算回车符；getline使用时注意遗留回车符问题

格式化输出时使用printf控制（包含在stdio.h库中）

flag标志位用法，一般不可解决时用，用多了比较混乱

```c++
for(int i = 0;i<n;i++)
{
    if(s[i] == ' ')break;
    //手动跳过空格
}
```

## 知识背景

### String的使用

> 字符表示单个字符，每个字符用单引号扩起来，比如'a', 而字符串是一个可变长度的字符序列，可以包含多个字符，用双引号扩起来，比如"hello"。

1. 引入头文件
   
使用string类型必须包含头文件<string>, 作为标准库的一部分，string也被定义在命名空间std中。

```c++
#include <string>
using std::string;
```
2. 声明和初始化
   
可以通过多种方式来声明和初始化string变量，下面是比较常用的几种方式：

```c++
string s1; // 默认初始化，s1是一个空的字符串
string s2 = "hello"; // 初始化一个值为hello的字符串
string s3(5, 'a') // 连续5个字符a组成的串，即'aaaaa'
```
3. 字符串操作
   
和数组类似，字符串也提供了一系列对字符串的操作方法，常见的有以下几种

使用+对字符串进行拼接操作，返回字符串连接之后的结果

```c++
string s1 = "hello";
string s2 = "world";
string s3 = s1 + " " + s2; // 对字符串进行连接，拼接之后的字符串是"hello world", 中间加了空格
```

使用size()获取字符串的长度

```c++
int length = s1.size(); // 字符串的长度即字符串中字符的个数，"hello"的长度为5

```

使用下标操作符 []访问字符串中的每一位字符

```c++
char c1 = s1[1]; // 下标从0开始，表示字符串的第一个字符
```

使用empty()来判断字符串是否为空

```c++
if (s1.empty()) {
  // 如果字符串为空则返回true, 否则返回false
}
```

4. 输入输出string

依旧可以使用标准库中的iostream来读写string， 比如使用 std::cin 从标准输入读取字符串，使用 std::cout 将字符串输出到标准输出。

```c++
int main() {
  string s; // 定义空字符串
  // 将标准输入的内容读入到字符串s中，从第一个真正的字符（去掉空格、换行等）开始读取，直到遇到空白停止
  cin >> s; 
  cout << s << endl; // 输出s
  return 0;
}
```

下面的程序仿照整数的读取，实现了从标准输入中读取文本，并将读取到的每个单词（以空格分隔）逐行输出到屏幕。

```c++
int main() {
  string word;
  while(cin >> word) { // 反复读取，直到到达末尾
    cout << word << endl; // 读取一个字符串并将其存储在 word 变量，然后输出，会附加一个换行符
  }
}
```

因为字符串读取遇到空格就会停止，表示这是一个单词，但有的时候我们想读取完整的一行，这就要求我们的读取不会在空格处停止，这种情况下可以使用到getline()，它会一直读取字符，直到遇到换行符（Enter键）或文件结束符（如果从文件读取）才结束。

```c++
#include <iostream>
#include <string>
using namespace std;
int main() {
  string line;
  // 获取用户输入的一行文本,并将其存储到line变量中
  getline(cin, line);
  // 输出读取的一行文本
  cout << line << endl;
}
```

### 令牌思路

我们可以采用这样一种思路，事先给每一行字符串一个“真的令牌”，字符串遍历处理过程中，如果有哪一行字符串中有{A, B, C, D, F}以及空格之外的字符，则把“真令牌”替换成“假令牌”，这样当走出循环之后再进行输出处理时，就会因为不认识这个“假令牌”而不进行输出。

```c++
int main() {
  // 初始化一个 "真令牌"
  bool flag = true;
  // 在某种情况下真令牌被替换成假令牌
  flag = false;
  // 无法执行下面的逻辑
  if (flag) {}
}
```

不过我们经常使用0/1来代替布尔值。

```c++
int flag = 1;
// 在某种情况下 1 被修改为0
// flag为0，表示false, 无法执行下面的逻辑
if (flag) {}
```

### 格式化输出与类型转换
在最后的输出中，我们使用printf("%.2f\n", sum / count),希望能输出一个两位有效数字的浮点数，但是我们在定义变量的时候sum和count都是整数, 在C++中，**整数除法（即两个整数相除）会截断小数部分，只保留整数部分**。因此，表达式 3 / 2 的结果将是 1，而不是 1.5。如果想要得到浮点数结果，可以将操作数中至少一个强制转换为浮点数类型，例如：

```c++
float result = 3.0 / 2;
//所以我们需要将sum定义成浮点数类型。在嵌入式大作业吃过大亏
float sum = 0;
```
