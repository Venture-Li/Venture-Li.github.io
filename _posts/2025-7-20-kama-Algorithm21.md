---
layout: post
title: "图形的面积"
date:   2025-7-20
tags: [Kama Algorithm]
comments: true
author: Venture-Li
---

## 题目描述

> 考虑一个简单的图形类层次，包括基类 `Shape` 和两个派生类 `Rectangle` 和 `Circle`结构。  
> 每个类都有一个用于计算面积的方法。你的任务是编写一个程序，根据输入数据创建一个图形对象，然后计算并输出其面积。  

## 输入描述

> 输入包括多行，每行包含一个图形的描述。 描述的第一个单词是图形类型（"`rectangle`"或"`circle`"），然后是与该图形相关的参数。 对于矩形，参数是宽度和高度，对于圆形，参数是半径。输入以单词"`end`"结束。  

## 输出描述

> 对于每个图形描述，输出其类型和面积。使用两位小数点精度输出面积。

## 输入示例

> rectangle 5 3  
> circle 2  
> end  

## 输出示例

> Rectangle area: 15.00  
> Circle area: 12.56  

## 题解

```c++
#include <iostream>
#include <vector>
#include <iomanip>
using namespace std;
class Shape
{
    public:
    virtual double CalculateArea() const = 0;
    virtual string GetType() const = 0;
};
class Rectangle:public Shape
{
    public:
    Rectangle(int width, int height): width(width), height(height){}

    double CalculateArea() const override
    {
        return static_cast<double>(width*height);
    }
    string GetType() const override
    {
        return "Rectangle";
    }

    private:
    int width;
    int height;
};
class Circle: public Shape
{
    public:
    Circle(int radius): radius(radius){}

    double CalculateArea() const override
    {
        return static_cast<double>(3.14*radius*radius);
    }
    string GetType() const override
    {
        return "Circle";
    }
    private:
    int radius;
};
int main()
{   
    string s;
    vector<Shape*> shapes;
    while(true)
    {
        cin>>s;
        if(s == "end")break;
        if(s == "rectangle")
        {
            int width,height;
            cin>>width>>height;
            shapes.push_back(new Rectangle(width,height));//注意new的用法与时机
        }
        else if(s == "circle")
        {
            int radius;
            cin>>radius;
            shapes.push_back(new Circle(radius));
        }
    }
    for (auto shape : shapes) 
    {
    cout << shape->GetType() << " area: " << fixed << setprecision(2) << shape->CalculateArea() << endl;
    }
    return 0;
}
```


