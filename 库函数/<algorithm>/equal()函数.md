比较[first,last1)范围的元素，从$first2$开始，如果在所有范围内元素匹配则返回true<br>

元素间使用$运算符==$进行比较<br>

函数模板的行为是相同的
```
template <class InputIterator1, class InputIterator2>
  bool equal ( InputIterator1 first1, InputIterator1 last1, InputIterator2 first2 )
{
  while (first1!=last1) {
    if (!(*first1 == *first2))   // or: if (!pred(*first1,*first2)), for version 2
      return false;
    ++first1; ++first2;
  }
  return true;
}
```
### 参数
#### ```first1,last1```
第一个序列输入迭代器的起始位置和终止位置。范围是```[first1,last1)```，包含在```first```和```last1```之间的所有元素，
包含从first1到不包括last1的所有元素。

#### ```first2```
第二个序列的起始位置的输入迭代器。比较至多在范围[first1,last1)的元素

#### ```pred```（不会用）
二进制函数，它接受两个元素作为参数(两个序列中的一个，以相同的顺序)，并返回一个可转换为bool的值。返回的值指示是否考虑在此函数的上下文中匹配元素。<br><>
函数不能修改它的任何参数。<br>
它可以是函数指针，也可以是函数对象。<br>

### 返回值
如果比较相等，则返回```true```<br>
如果比较不相等，则返回```false```<>


### 举例
```cpp
// equal algorithm example
#include <iostream>     // std::cout
#include <algorithm>    // std::equal
#include <vector>       // std::vector

bool mypredicate (int i, int j) {
  return (i==j);
}

int main () {
  int myints[] = {20,40,60,80,100};               //   myints: 20 40 60 80 100
  std::vector<int>myvector (myints,myints+5);     // myvector: 20 40 60 80 100

  // using default comparison:
  if ( std::equal (myvector.begin(), myvector.end(), myints) )
    std::cout << "The contents of both sequences are equal.\n";
  else
    std::cout << "The contents of both sequences differ.\n";

  myvector[3]=81;                                 // myvector: 20 40 60 81 100

  // using predicate comparison:
  if ( std::equal (myvector.begin(), myvector.end(), myints, mypredicate) )
    std::cout << "The contents of both sequences are equal.\n";
  else
    std::cout << "The contents of both sequences differ.\n";

  return 0;
}
```

