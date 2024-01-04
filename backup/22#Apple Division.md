# Apple Division

https://cses.fi/problemset/task/1623
There are n apples with known weights. Your task is to divide the apples into two groups so that the difference between the weights of the groups is minimal.
Input
The first input line has an integer n: the number of apples.
The next line has n integers p_1,p_2,\dots,p_n: the weight of each apple.
Output
Print one integer: the minimum difference between the weights of the groups.
```C++
#include<bits/stdc++.h> // 包含标准库
using namespace std;

vector<long long> weights; // 用于存储砝码的重量
int n; // 砝码的数量

// cls函数递归地寻找最小的重量差
long long cls(int index, long long sum1, long long sum2) {
    if (index == n) return abs(sum1 - sum2); // 如果所有砝码都考虑过了，返回两组重量的差的绝对值

    // 递归地将当前砝码加入到其中一组，并计算两种情况的最小重量差
    return min(cls(index + 1, sum1 + weights[index], sum2),
               cls(index + 1, sum1, sum2 + weights[index]));
}

int main() {
    cin >> n; // 输入砝码的数量
    weights.resize(n); // 调整weights向量的大小以匹配砝码数量
    for (int i = 0; i < n; i++) {
        cin >> weights[i]; // 输入每个砝码的重量
    }
    
    // 调用cls函数并从索引0和初始重量0开始
    cout << cls(0, 0, 0) << endl; // 输出最小重量差
    return 0;
}
```

---

* Link: https://github.com/justonehe/Algorithm/issues/22
* Labels: `递归`, `usaco`, `全搜索`
* Creation Date: 2024-01-04T14:41:36Z
