***
假设奖牌榜的排名规则如下：
1、首先金牌数量多的排在前面；
2、其次银牌数量多的排在前面；
3、然后铜牌数量多的排在前面；
4、若以上三个条件仍无法区分名次，则以国家名称的字典序排定。

假设国家名称不超过20个字符、各种奖牌数不超过100，且大于等于0，编写程序给奖牌榜排名。

* 输入：第一行为代表国家数量的整数N(0 < N < 21)，接下来的N行，每行包含一个字符串Namei表示每个国家的名称，和三个整数Gi、Si、Bi表示每个获得的金牌、银牌、铜牌的数量
* 输出：排名后的奖牌榜，只输出国家名
  
* 样例：
  * 输入：<br>
    5<br>
    China 32 28 34<br>
    England 12 34 22<br>
    France 23 33 2<br>
    Japan 12 34 25<br>
    Rusia 23 43 0<br>
  * 输出：<br>
    China<br>
    Rusia<br>
    France<br>
    Japan<br>
    England<br>

***
实现：
```cpp
#include <iostream>
#include <string>
#include <vector>
#include <utility>
#include <algorithm>

using std::cin;
using std::cout;
using std::endl;
using std::string;
using std::vector;
using std::pair;
using std::make_pair;
using std::sort;

bool cmp(const pair<string, int> &p1, const pair<string, int> &p2)
{
    if (p1.second < p2.second) {
        return false;
    } else if (p1.second > p2.second) {
        return true;
    } else {
        return p1.first > p2.first;
    }
}

int main(int argc, char *argv[])
{
    int n;
    while (cin >> n) {
        string name;
        int g, s, b;
        vector<pair<string, int>> vec;
        for (int i = 0; i < n; ++i) {
            cin >> name >> g >> s >> b;
            vec.push_back(make_pair(name, 100*g + 10*s + b));
            sort(vec.begin(), vec.end(), cmp);
        }
        
        for (const auto &v : vec) {
            cout << v.first << endl;
        }
    }
}
```