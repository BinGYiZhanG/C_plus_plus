* [C++中list的erase()函数问题](https://blog.csdn.net/nanfeng224/article/details/40355465)

* 典型错误

```cpp
#include <iostream>
#include <list>
using namespace std;
int main()
{
    list<int> test_list;
    list<int>::iterator test_list_it;
    test_list.push_back(1);
    test_list_it = test_list.begin();
    for(;test_list_it != test_list.end();test_list_it++)
    {
        test_list.erase(test_list_it);
    }
}

```

* 问题：该程序不能跳出循环
* 原因：test_list.erase(test_list_it);每次做erase时都有可能使迭代器失效，test_list_it++就发生错误了。可以参见effective stl一书。所有容器做erase操作时都有可能使迭代器失效。

* 改正的原理是使当前迭代器失效时能指向下一个位置，具体实现：
* [CCF2018-3-CIDR]()使用的第一种方法，```if-else```

```cpp
#include<iostream>
#include<list>
using namespace std;
int main()
{
	int i;
	list<int> list1;
	list<int> ::iterator it;
	for(i = 0; i < 8; i++)
		list1.push_back(i);
	
	for(it = list1.begin(); it != list1.end(); ++ it)
	{
		cout <<*it<<" ";
	}
	cout<<endl;
 
	/*
	//写法一
	for(it=list1.begin(); it!= list1.end(); )
		if (*it % 2)
		{
			list1.erase(it++);
		}
		else
			it++;
	//写法二
	for(it=list1.begin();it!=list1.end();)
	{
		if(*it%2)
			it=list1.erase(it);
		else it++;
	}
	*/
	//写法三
	for(it=list1.begin();it!=list1.end();)
	{
		if(*it%2)
		{
			list<int>::iterator tmp=it++;
			list1.erase(tmp);
		}
		else
			it++;
	}
 
	for (it = list1.begin(); it != list1.end(); ++ it)
	{
		cout <<*it<<" ";
	}
	cout<<endl;
	return 1;
}
```
