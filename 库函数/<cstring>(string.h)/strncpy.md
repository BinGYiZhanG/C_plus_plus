```cpp
char * strncpy ( char * destination, const char * source, size_t num );
```

* destination
指向要复制内容的目标数组的指针。（Pointer to the destination array where the content is to be copied.）
* source
被复制的C字符串
* num
要从源文件复制的最大字符数。<br>
size_t是一个无符号整数类型。

Example
```cpp
/* strncpy example */
#include <stdio.h>
#include <string.h>

int main ()
{
  char str1[]= "To be or not to be";
  char str2[40];
  char str3[40];

  /* copy to sized buffer (overflow safe): */
  strncpy ( str2, str1, sizeof(str2) );

  /* partial copy (only 5 chars): */
  strncpy ( str3, str2, 5 );
  str3[5] = '\0';   /* null character manually added */

  puts (str1);
  puts (str2);
  puts (str3);

  return 0;
}
```
