Constructs a sorted range beginning in the location pointed by result with the set intersection of the two sorted ranges [first1,last1) and [first2,last2).
<br>
又是这番话，奈何我理解不了。<br>

### 取交集

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

	it = set_intersection(first, first + 5, second, second + 5, v.begin());

	v.resize(it - v.begin());

	cout << "The union has " << (v.size()) << " elements:" << endl;
	for (it = v.begin(); it != v.end(); it++)
		cout << " " << (*it);
	cout << endl;

	return 0;

}


Out:

The union has 2 elements:
 10 20
 
 
```

