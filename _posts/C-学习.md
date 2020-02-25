---
title: C++学习
tags:
  - C++
abbrlink: 8279
date: 2020-02-25 00:13:02
---

## 静态链接库和动态链接库

<!--more-->

静态链接库在所开发的程序中通过程序接口来调用库函数，这些库函数只有在连接时才会真正连接到应用程序中。

静态链接库的缺陷：假设两个应用程序同时运行，并且使用了相同的静态链接库，那么实际上静态链接库要被加载到内存中两次，从而浪费内存空间。

动态链接库与静态链接库类似，都是以二进制的方式存在，所不同的是编译器在编译调用了动态链接库的程序时，并不将库文件中的函数执行体链接到可执行文件中，而只在可执行文件中保留一个函数调用的标记。当程序运行时，才有操作系统将动态链接库文件一并加载到内存，并映射到程序的地址空间中，这样就保证了程序能够正常调用到库文件中的函数。同时，当有多个调用动态链接库的程序运行时，也只有一份动态链接库在内存中，即动态链接库在运行期是共享的。

动态链接库的优点：动态链接库在编译链接时并不直接连接到应用程序中，这样就使得目标可执行程序比使用静态链接库要小，同时运行期间又是共享动态链接，所以节省了磁盘存储空间和运行时的内存空间。另外，修改动态链接库时，在保证接口不变的情况下，主程序无需重新编译，只需替换新的动态链接库即可。

## 继承

继承代表了 **is a** 关系。例如，哺乳动物是动物，狗是哺乳动物，因此，狗是动物，等等。

### 基类 & 派生类

形式：

```
class derived-class: access-specifier base-class
```

access-specifier 是 **public、protected** 或 **private** 其中的一个，base-class 是之前定义过的某个类的名称。如果未使用访问修饰符 access-specifier，则默认为 private。

例子：基类 **Shape**，**Rectangle** 是它的派生类

```
#include <iostream>
 
using namespace std;
 
// 基类
class Shape 
{
   public:
      void setWidth(int w)
      {
         width = w;
      }
      void setHeight(int h)
      {
         height = h;
      }
   protected:
      int width;
      int height;
};
 
// 派生类
class Rectangle: public Shape
{
   public:
      int getArea()
      { 
         return (width * height); 
      }
};
 
int main(void)
{
   Rectangle Rect;
 
   Rect.setWidth(5);
   Rect.setHeight(7);
 
   // 输出对象的面积
   cout << "Total area: " << Rect.getArea() << endl;
 
   return 0;
}
```

输出：

```
Total area: 35
```

## 多继承

语法：

```
class <派生类名>:<继承方式1><基类名1>,<继承方式2><基类名2>,…
{
<派生类类体>
};
```

中间由逗号隔开。

## 参考

 [C++  继承|菜鸟教程](https://www.runoob.com/cplusplus/cpp-inheritance.html)

