
迭代器：<br>
```inserter(container,pos) ```
如何工作：<br>
返回通用插入型迭代器，内部会调用容器container的insert(pos)方法将数据插入到pos位置。<br>

[C++之inserter函数与插入迭代器](https://blog.csdn.net/m0_37456764/article/details/83019250)

```cpp
#include <iostream>
#include <algorithm>
#include <vector>
#include <iterator>
using namespace std;

int main()
{
	vector<int> s{ 1,2,3,4 };
	fill_n(s.begin(), 2, 5);
	for (int i = 0; i < (int)s.size(); i++) {
		cout << " " << s[i];
	}
	cout << endl;
	vector<int> t{ 1,2,3,4 };
	fill_n(inserter(t,t.begin()), 2, 5);
	for (int i = 0; i < (int)t.size(); i++) {
		cout << " " << t[i];
	}

	return 0;

}
```
