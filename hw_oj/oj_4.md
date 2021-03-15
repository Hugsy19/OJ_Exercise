***
一个正整数有可能可以被表示为m（m >= 2）个连续正整数之和。编写程序，找出某个正整数符合这种要求的所有连续正整数序列，若不存在这种序列，则打印NONE。

* 输入：正整数n
* 输出：n的所有m个连续正整数之和表示法或NONE

* 样例：
  * 输入：<br>
    15<br>
  * 输出：<br>
    15 = 1 + 2 + 3 + 4 + 5 <br>
    15 = 4 + 5 + 6 <br>
    15 = 7 + 8 <br>
    <br>
  * 输入：<br>
    8<br>
  * 输出：<br>
    NONE<br>

***
分析：

根据等差数列公式`$S_n = na_1 + \frac{(n(n-1)}{2}d$`，n要表示为m个正整数之和，即为`$d=1$`时，`$S_n - \frac{(n(n-1)}{2}$`的值要能和`$n$`整除，由此可得题解。

实现：
```cpp
#include <iostream>
#include <cmath>

using std::cin;
using std::cout;
using std::endl;

int main(int argc, char *argv[])
{
    int n;
    while (cin >> n) {
        bool ret = 0;
        for (int i = sqrt(n)*2; i > 1; --i) {
            if(!((n - (i - 1)*i/2)%i)) {
                ret = 1;
                int a = (n - (i - 1)*i/2)/i;
                if (a > 0) {
                    cout << n << " = " << a++;
                    for (int j = 1; j < i; ++j, ++a) {
                        cout << " + " << a;
                    }
                    cout << endl;
                }
            }
        }
        if (!ret) {
            cout << "NONE" << endl;
        }
    }
}
```
