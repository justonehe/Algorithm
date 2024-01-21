# USACO 2020 January Contest, Bronze Problem 3. Race

http://www.usaco.org/index.php?page=viewproblem2&cpid=989&lang=en
Bessie 正在参加一场 K（1≤K≤109）米的跑步比赛。她从 0 米每秒的速度开始比赛。在每一秒中，她可以选择将她的速度增加 1 米每秒，保持速度不变，或者将她的速度减少 1 米每秒。例如，在第一秒中，她可以将她的速度增加到 1 米每秒，跑 1 米，或者保持她的速度 0 米每秒不变，跑 0 米。Bessie 的速度不会降低到小于零。
Bessie 始终朝着终点线的方向跑，她想要花费整数秒的时间完成比赛。此外，她不想在终点时跑得太快：在 Bessie 跑完 K 米的时刻，她希望她的速度不超过 X（1≤X≤105）米每秒。Bessie 想要对于 N（1≤N≤1000）个不同的 X 值知道她多快可以完成比赛。

测试点性质：
测试点 2-4 满足 N=X=1。
测试点 5-10 没有额外限制。
输入格式（文件名：race.in）：
输入的第一行包含两个整数 K 和 N。
以下 N 行每行包含一个整数 X。

输出格式（文件名：race.out）：
输出 N 行，每行包含一个整数，表示 Bessie 完成比赛时的速度小于或等于 X 的情况下跑完 K米需要的最小时间。
#### 题解和分析
这段代码的目的是为了解决一个关于赛跑的问题，其中赛跑者贝西（Bessie）在一场长度为 `K` 米的赛跑中以特定的速度运动规则参赛。贝西的速度每秒可以增加 1 米/秒、保持不变或减少 1 米/秒，但速度不能降至零以下。她想在整数秒数结束时完成比赛，并且在终点时的速度不超过 `X` 米/秒。代码的任务是对 `N` 个不同的 `X` 值，计算贝西完成比赛的最快时间。以下是代码的解释和注释：

```cpp
#include<bits/stdc++.h>
using namespace std;

// 解决贝西完成赛跑的函数，参数为赛道长度
int solve(int dist) {
  int minspeed;
  scanf("%d", &minspeed); // 读取贝西在终点时的最大速度限制
  int lhstravel = 0; // 左半部分行进的距离（速度递增）
  int rhstravel = 0; // 右半部分行进的距离（速度递减）
  int timeused = 0; // 已用时间

  // 循环增加贝西的速度直到满足条件
  for(int currspeed = 1;; currspeed++) {
    lhstravel += currspeed; // 增加左半部分的距离
    timeused++; // 增加用时
    // 检查是否已经达到或超过终点
    if(lhstravel + rhstravel >= dist) return timeused;

    // 当当前速度达到或超过最大速度限制时，开始减速
    if(currspeed >= minspeed) {
      rhstravel += currspeed; // 增加右半部分的距离
      timeused++; // 增加用时
      // 再次检查是否已经达到或超过终点
      if(lhstravel + rhstravel >= dist) return timeused;
    }
  }
}

int main() {
  long long k, n;
  cin >> k >> n; // 读取赛道长度和不同速度限制的数量

  // 对于每个速度限制，计算完成比赛的最快时间
  for (int i = 0; i < n; i++) {
    printf("%d\n", solve(k));
  }

  return 0;
}
```

在这个代码中，`solve` 函数用于计算在特定的速度限制下，贝西完成赛跑的最快时间。它通过模拟在速度递增和递减的两个阶段中贝西的运动来实现。当贝西的速度达到或超过给定的速度限制时，她开始减速。函数返回她达到或超过终点时所需的最少秒数。`main` 函数从输入读取赛道长度和速度限制的数量，并对每个速度限制调用 `solve` 函数来计算和输出完成比赛的最快时间。

---

* Link: https://github.com/justonehe/Algorithm/issues/49
* Labels: `usaco`, `贪心`
* Creation Date: 2024-01-21T04:55:42Z
