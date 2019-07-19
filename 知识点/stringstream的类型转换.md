* char类型转换为string 类型:

```cpp
#include <iostream>
#include <string>
#include <sstream>

using namespace std;


int main(){
    char c[5]="1000";
    string str;
    stringstream stream;
    stream<<c;
    str=stream.str();
    cout<<str<<endl;
}

```
[C++中string、char *、char[]的转换](https://www.cnblogs.com/Pillar/p/4206452.html)

* string到int的转换
```cpp
#include <iostream>
#include <string>
#include <sstream>

using namespace std;


int main(){
    string res="10000";
    int n=0;
    stringstream stream;
    stream<<res;
    stream>>n;
    cout<<n<<endl;
}
```
