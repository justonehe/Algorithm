# Problem: Kayaking

https://codeforces.com/contest/863/problem/B
Vadim is really keen on travelling. Recently he heard about kayaking activity near his town and became very excited about it, so he joined a party of kayakers.

Now the party is ready to start its journey, but firstly they have to choose kayaks. There are 2·n people in the group (including Vadim), and they have exactly n - 1 tandem kayaks (each of which, obviously, can carry two people) and 2 single kayaks. i-th person's weight is wi, and weight is an important matter in kayaking — if the difference between the weights of two people that sit in the same tandem kayak is too large, then it can crash. And, of course, people want to distribute their seats in kayaks in order to minimize the chances that kayaks will crash.

Formally, the instability of a single kayak is always 0, and the instability of a tandem kayak is the absolute difference between weights of the people that are in this kayak. Instability of the whole journey is the total instability of all kayaks.

Help the party to determine minimum possible total instability!

```c++
#include<iostream>
#include<algorithm>
#include<vector>
using namespace std;

int main() {
    int n; // n表示配对的数量
    cin >> n; // 读取n
    int p[55] = {0}; // 存储所有元素的数组，初始化为0

    // 读取2n个元素
    for(int i = 0; i < 2 * n; i++) cin >> p[i];

    // 对数组进行排序
    sort(p, p + 2 * n);

    int ans = 1e9; // 存储最小差值和的变量，初始化为一个很大的数（1e9）

    // 遍历所有可能排除的元素对
    for(int i = 0; i < 2 * n; i++) {
        for(int j = i + 1; j < 2 * n; j++) {
            vector<int> s; // 存储除了排除的两个元素外的其他元素

            // 将除了i和j之外的元素添加到s中
            for(int k = 0; k < 2 * n; k++) {
                if(k != i && k != j) s.push_back(p[k]);
            }

            int tmp = 0; // 存储当前排除元素对的差值和

            // 计算剩余元素两两配对的差的绝对值之和
            for(int k = 0; k < 2 * n - 2; k += 2) {
                tmp += s[k + 1] - s[k];
            }

            // 更新最小差值和
            ans = min(ans, tmp);
        }
    }

    // 输出最小差值和
    cout << ans << "\n";

    return 0;
}
```

---

* Link: https://github.com/justonehe/Algorithm/issues/35
* Labels: `usaco`, `贪心`, `排序`
* Creation Date: 2024-01-12T01:42:49Z
