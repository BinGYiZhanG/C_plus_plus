```cpp
const char * strstr ( const char * str1, const char * str2 );
      char * strstr (       char * str1, const char * str2 );
```
Return：第一个在字符串str1中出现字符串str2的位置指针，如果字符串str2不是字符串str1的部分，发送返回一个空指针<br>
匹配过程不包括终止的空字符，但它在这里停止。<br>

在C中，这个函数只被声明为<br>
```cpp
char * strstr ( const char *, const char * );
```
在C++中有两个重载函数<br>

举例:[POJ 3080](https://github.com/BinGYiZhanG/aoapc-book/blob/master/To%20Be%20a%20ACMer/7%E6%9C%88/07_10/POJ%203080%20Blue%20Jeans.md)
判断是否包含子串<br>
```if(!strstr(str[k],dna))```

#### 英语翻译极差，将就着看吧
