---
title: c++11 random
date: 2021-11-28 13:12:11
tag: c++
categories: c++
---
random中组件分为随机数引擎类，随机数分部类。
随机数引擎类是可以独立运行的随机数发生器，它以均匀的概率生成某一类型的随机数，但无法指定随机数的范围、概率等。通常不使用，，因为无法指定生成随机数的范围。
<!--more-->
随机数分布类是一个需要于随机数引擎类的支持才能运行的类，但是它能根据用户的需求利用随机数引擎生成符合条件的随机数。例如某一区间、某一分布概率的随机数。将这些数值映射到位于固定范围的某一数学分布中。关于分布的例子有：unifrom_int (所有的整数倍都被以相等的概率产生)以及normal_distribution (分布的概率密度函数曲线呈钟形)；每一种分布都处于某一特定的范围之内。

## 随机非负数
default_random_engine 是一个随机数引擎类。它定义的调用运算符返回一个随机的 unsigned 类型的值。
```cpp
#include <iostream>
#include <random>
using namespace std;
int main() {
    default_random_engine e;
    for ( int i = 0; i < 10; ++i) {
        cout << e() << endl;
    }
    return 0;
}
```
## 特定范围的非负数——uniform_int_distribution
```cpp
#include <iostream>
#include <random>
using namespace std;
int main() {
    default_random_engine e;
    uniform_int_distribution<unsigned> u (0, 9);//生成随机1到9
}
```
## 种子
```cpp
std::default_random_engine generator(time(NULL));  
std::uniform_int_distribution<int> dis(0,100);  
auto dice= std::bind(dis,generator);  
for(int i=0;i<5;i++)  
{  
    std::cout<<dice()<<std::endl;  
} 
```
