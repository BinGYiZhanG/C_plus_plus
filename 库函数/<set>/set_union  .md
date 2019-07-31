使用两个排序范围[first1,last1) and [first2,last2).的集合并集，从result指向的位置开始构造一个排序范围。<br>

两个集合的并集有在一个集合中或同时在两个集合中出现的元素组成。来自第二个范围的元素有着和第一个范围的元素相同的元素，将不会被复制到结果范围内。<br>

元素使用运算符```<```来进行比较在第一个版本，在第二个版本下通过```comp```函数进行比较。
两个元素,a和b，被考虑相等，（如果(!(a<b) && !(b<a))）或者（如果!comp(a,b) && !comp(b,a)）<br>

在范围内元素根据相同的标准（operator< or comp）进行排序，结果范围根据这个进行排序。<br>

函数模板的形式和以下等价：
```
template <class InputIterator1, class InputIterator2, class OutputIterator>
  OutputIterator set_union (InputIterator1 first1, InputIterator1 last1,
                            InputIterator2 first2, InputIterator2 last2,
                            OutputIterator result)
{
  while (true)
  {
    if (first1==last1) return std::copy(first2,last2,result);
    if (first2==last2) return std::copy(first1,last1,result);

    if (*first1<*first2) { *result = *first1; ++first1; }
    else if (*first2<*first1) { *result = *first2; ++first2; }
    else { *result = *first1; ++first1; ++first2; }
    ++result;
  }
}
```

### 参数说明:
```cpp
first1,last1:
输入第一个排序序列的初始和最后迭代器位置。范围是```[first1,last1]```,包含在```[first1,last1)```范围内的全部元素，
first2,last2:
输入第二个排序序列的初始和最后迭代器位置。范围是```[first2,last2)```。包含
result:
输出存储结果序列的初始范围的迭代器。<br>
指针类型应支持从其他范围分配元素的值。
comp:
排序函数
```

### 返回值：
```cpp
指向构造范围尾部的迭代器
```

Example:
```cpp
#include <iostream>
#include <algorithm>
#include <vector>
using namespace std;

int main()
{
	int first[] = { 5,10,15,20,25 };
	int second[] = { 50,40,30,20,10 };
	vector<int> v(10);
	vector<int>::iterator it;

	sort(first, first + 5);
	sort(second, second + 5);

	it = set_union(first, first + 5, second, second + 5, v.begin());

	v.resize(it - v.begin());

	cout << "The union has " << (v.size()) << " elements:" << endl;
	for (it = v.begin(); it != v.end(); it++)
		cout << " " << (*it);
	cout << endl;

	return 0;

}


Out:
The union has 8 elements:
 5 10 15 20 25 30 40 50

```
时间复杂度（Complexity）：<br>
Up to linear in 2*(count1+count2)-1 (where countX is the distance between firstX and lastX): Compares and assigns elements.










