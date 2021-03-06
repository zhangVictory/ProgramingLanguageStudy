<center><font size="8" color="#007acc">C++ vector的API</font></center>
[TOC]

# 1 定义一个vector

- ```C++
  vector<int> iv(10);//定义一个长度为10的列表,初始值不确定
  ```

- ```C++
  vector<int> a(10,1);//定义长度为10的列表,初始值为1
  ```

- ```C++
  vector<int> a(b);//用vector b来初始化vector a
  ```

- ```C++
  vector<int> a(b.begin(),b.begin()+3);//可以使用vector b的一部分来初始化a 包左不包右
  ```

- ```C++
  int b[7]={1,2,3,4,5,9,8};
  vector<int> a(b,b+7); //从数组中获得初值 包左不包右
  ```



# 2 重要操作

- ```C++
  a.assign(b.begin(), b.begin()+3); //b为向量，将b的0~2个元素构成的向量赋给a 包左不包右
  ```

- ```C++
  a.assign(4,2); //生成一个只含4个元素，且每个元素为2的向量赋值给 a
  ```

- ```c++
  a.back(); //返回a的最后一个元素
  ```

- ```C++
  a.front(); //返回a的第一个元素
  ```

- ```C++
  a[i]; //返回a的第i个元素，当且仅当a[i]存在
  ```

- ```C++
  a.clear(); //清空a中的元素
  ```

- ```C++
  a.empty(); //判断a是否为空，空则返回ture,不空则返回false
  ```

- ```C++
  a.pop_back(); //删除a向量的最后一个元素,返回值void
  ```

- ```C++
  a.push_back(5);//在a的最后一个向量后插入一个元素，其值为5
  ```

- ```C++
  a.erase(a.begin()+1,a.begin()+3);//删除范围内的元素,包左不包右
  ```

- ```C++
  a.insert(a.begin(),5);//在a.begin()的位置前插入数字5
  ```

- ```C++
  a.insert(a.begin(),3,5);//在a.begin()的位置前插入三个数字,都是5
  ```

- ```C++
  a.insert(a.begin(),b+3,b+6); //b为数组，在a的a.begin()的位置前插入b的第3个元素到第5个元素
  ```

- ```C++
  a.size(); //返回a中元素的个数.
  ```

- ```C++
  a.capacity(); //返回a在内存中总共可以容纳的元素个数 即容量
  ```

- ```C++
  a.resize(10);//把a的容量设置为10,多则删，少则补，其值随机
  ```

- ```C++
  a.resize(10,2); //将a的现有元素个数调至10个，多则删，少则补，其值为2
  ```

vector是动态数组,当插入空间不足时,会动态扩容,当扩容次数多的时候,会影响性能. 当我们能估计存储的元素数目时,就可以使用这个函数先分配空间,这样就减少多次扩容的开销

reserve函数，表示为vector预留空间，会增加capacity的值，但不会增大size的值