***
solo发现在每一轮Online Judge的比赛中，他的排名R都能被参赛人数N(包括solo)整除，编写程序预测他的排名情况。

* 输入：参赛人数N（0 < N < 10^9）
* 输出：可能的获得的排名数S以及有小到大输出排名Ri，用空格隔开

* 样例：
  * 输入：<br>
    10<br>
  * 输出：<br>
    4 1 2 5 10<br>

***
实现：
```cpp
#include <iostream>
#include <vector>
#include <cmath>

using std::cin;
using std::cout;
using std::endl;
using std::vector;

int main(int argc, char *argv[])
{
    int n;
    while (cin >> n) {
        vector<int> fvec, bvec;
        for (int i = 1; i <= sqrt(n); ++i) {
            if (!(n % i)) {
                fvec.push_back(i);
                bvec.push_back(n/i);
            }
        }
        cout << fvec.size() + bvec.size() << " ";
        for (const auto &v : fvec)
            cout << v << " ";
        for (auto it = bvec.crbegin(); it != bvec.crend(); ++it)
            cout << *it << " ";
        cout << endl;
    }
}
```
