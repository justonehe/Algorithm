# USACO 2016 January Contest, Bronze Problem 2. Angry Cows

http://www.usaco.org/index.php?page=viewproblem2&cpid=592
Bessie the cow has designed what she thinks will be the next big hit video game: "Angry Cows". The premise, which she believes is completely original, is that the player shoots a cow with a slingshot into a one-dimensional scene consisting of a set of hay bales located at various points on a number line; the cow lands on a hay bale with sufficient force to cause the bale to explode, which in turn might set of a chain reaction that causes additional nearby hay bales to explode. The goal is to use a single cow to start a chain reaction that detonates as many hay bales as possible.
There are N hay bales located at distinct integer positions x1,x2,…,xN on the number line. If a cow is launched onto a hay bale at position x, this hay bale explodes with a "blast radius" of 1, meaning that any other hay bales within 1 unit of distance are also engulfed by the explosion. These neighboring bales then themselves explode (all simultaneously), each with a blast radius of 2, so these explosions may engulf additional yet-unexploded bales up to 2 units of distance away. In the next time step, these bales also explode (all simultaneously) with blast radius 3. In general, at time t a set of hay bales will explode, each with blast radius t. Bales engulfed by these explosions will themselves explode at time t+1 with blast radius t+1, and so on.

Please determine the maximum number of hay bales that can explode if a single cow is launched onto the best possible hay bale to start a chain reaction.
#### 解题思路
根据题目描述，这段代码模拟了“愤怒的奶牛”游戏中的一个场景，其中一头奶牛被用弹弓射入一系列分布在数轴上的干草捆中，以引发连锁反应并使尽可能多的干草捆爆炸。每个干草捆的爆炸具有逐步增大的爆炸半径，随着时间的推移，爆炸半径逐步增大。代码的目的是找出在哪个干草捆上引发爆炸可以造成最大程度的连锁反应。以下是对代码的解释和注释：

```cpp
#include<bits/stdc++.h>
using namespace std;

int n, ans; // n 代表干草捆的数量，ans 用于存储最大可引发的爆炸数量
vector<int> position; // 存储每个干草捆的位置

// 计算从指定位置开始，特定方向上可以引发的连锁爆炸数量
int getNum(int pos, int direction) {
    int r = 1; // 爆炸半径，初始为 1
    int prev = pos; // 初始位置
    while (true) {
        int next = prev;
        // 检查当前爆炸半径内是否有干草捆可以爆炸
        while (next + direction >= 0 && next + direction < n && abs(position[next + direction] - position[prev]) <= r) {
            next += direction; // 移动到下一个可以爆炸的干草捆
        }
        if (next == prev) break; // 如果没有更多干草捆可以爆炸，停止循环
        prev =

next; // 更新当前位置
        r++; // 增加爆炸半径
    }
    return abs(prev - pos); // 返回在这个方向上引发的总爆炸数量
}

int main() {
    cin >> n; // 输入干草捆的数量
    position.resize(n); // 调整存储位置的向量大小
    for (int i = 0; i < n; i++) cin >> position[i]; // 输入每个干草捆的位置

    sort(position.begin(), position.end()); // 对位置进行排序

    // 遍历每个干草捆，计算在这个位置开始爆炸可以引发的最大爆炸数量
    for (int i = 0; i < n; i++) {
        ans = max(ans, getNum(i, -1) + getNum(i, 1) + 1); // 包括当前干草捆在内的总爆炸数量
    }
    cout << ans; // 输出最大可能引发的爆炸数量

    return 0;
}
```

这个代码的关键是 `getNum` 函数，它通过模拟在特定位置和方向上的连锁爆炸过程，计算可以引发的爆炸数量。对于每个干草捆位置，它都会调用两次 `getNum` 函数（一次向左，一次向右），然后将这两个方向的爆炸数量加上当前干草捆本身，以求得从该位置引发的最大爆炸数量。通过遍历所有干草捆，找出可以引发最大连锁爆炸的位置。


---

* Link: https://github.com/justonehe/Algorithm/issues/39
* Labels: `模拟`, `usaco`, `排序`
* Creation Date: 2024-01-15T07:44:18Z
