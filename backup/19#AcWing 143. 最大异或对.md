# AcWing 143. 最大异或对

https://www.acwing.com/problem/content/145/
在给定的 N个整数 A1，A2……AN中选出两个进行 xor（异或）运算，得到的结果最大是多少？

输入格式
第一行输入一个整数 N。

第二行输入 N 个整数 A1～AN。

输出格式
输出一个整数表示答案。

数据范围
1≤N≤105,
0≤Ai<231
```c++
#include<bits/stdc++.h> // 包含标准库
using namespace std;

int n, a[100005]; // n是数组长度，a存储数组元素
int son[3000000][2], idx; // son数组作为字典树的节点，idx用于记录当前节点的索引

// 将一个数x插入字典树
void insert(int x) {
    int p = 0;
    for (int i = 30; i >= 0; i--) {
        int &s = son[p][x >> i & 1]; // 取x的第i位的值（0或1）
        if (!s) s = ++idx; // 如果这个节点不存在，则创建它
        p = s; // 移动到下一个节点
    }
}

// 查询与x异或值最大的数
int query(int x) {
    int res = 0, p = 0;
    for (int i = 30; i >= 0; i--) {
        int s = x >> i & 1; // 取x的第i位的值
        if (son[p][!s]) {
            // 如果存在相反的位，则选择它来最大化异或结果
            res += 1 << i;
            p = son[p][!s];
        } else {
            // 否则，只能选择相同的位
            p = son[p][s];
        }
    }
    return res;
}

int main() {
    cin >> n; // 输入数组长度
    for (int i = 0; i < n; i++) {
        cin >> a[i]; // 输入数组元素
        insert(a[i]); // 将每个元素插入字典树
    } 
    int res = 0;
    for (int i = 0; i < n; i++) {
        res = max(res, query(a[i])); // 查询并更新最大异或值
    }
    cout << res; // 输出结果

    return 0;
}
```

---

* Link: https://github.com/justonehe/Algorithm/issues/19
* Labels: `AcWing`, `字典树`
* Creation Date: 2024-01-01T04:36:52Z
