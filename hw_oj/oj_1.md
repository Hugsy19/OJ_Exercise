*** 
编写程序实现任意十进制正小数m转换成n进制的正小数，小数点后保留10位小数。

* 输入：多组数据，每组由用空格隔开的两个数m、n（0.0000009 < m < 1, 1 < n < 10）组成
* 输出：多组转换结果

* 样例：
  * 输入：<br>
    0.795 3<br>
  * 输出：<br>
    0.2101101122<br>
    
***
实现：

```cpp
#include <iostream>

using std::cin;
using std::cout;
using std::endl;

int main(int argc, char *argv[])
{
    double m;
    int n;
    while (cin >> m >> n) {
        if (m <= 0.0000009 || m >= 1 || n <= 1 || n >= 10)
            return 1;
        cout << "0.";
        for (int i = 0; i < 10; ++i) {
            m *= n;
            int tmp = static_cast<int>(m);
            cout << tmp;
            m -= tmp;
        }
        cout << endl;
    }
    return 0;
}
```