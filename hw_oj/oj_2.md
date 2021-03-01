***
一个句子由多个单词组成，假设每个单词的长度Ni为该单词的重量，编写程序计算整个句子的平均重量V。

* 输入：一个由空格分隔的字符串S
* 输出：S的平均重量V（保留两位小数）

* 样例：
  * 输入：<br>
    Who Love Solo<br>
  * 输出：<br>
    3.67<br>

***
实现：

```cpp
#include <iostream>
#include <sstream>
#include <string>
#include <iomanip>

using std::cin;
using std::cout;
using std::endl;
using std::getline;
using std::string;
using std::stringstream;
using std::fixed;
using std::setprecision;

int main(int argc, char *argv[])
{
    string str;
    while (getline(cin, str)) {
        string wd;
        int cnt = 0;
        double weight = 0;
        stringstream sstr(str);
        while (sstr >> wd) {
            weight += wd.length();
            ++cnt;
        }
        cout << fixed << setprecision(2) << weight / cnt << endl;
    }
}
```