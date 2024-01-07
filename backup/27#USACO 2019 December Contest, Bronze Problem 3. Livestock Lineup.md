# USACO 2019 December Contest, Bronze Problem 3. Livestock Lineup

http://www.usaco.org/index.php?page=viewproblem2&cpid=965&lang=zh
每天，Farmer John 都要给他的 8 头奶牛挤奶。她们的名字分别是 Bessie，Buttercup，Belinda，Beatrice，Bella，Blue，Betsy，和 Sue。
不幸的是，这些奶牛相当难以伺候，她们要求 Farmer John 以一种符合 N条限制的顺序给她们挤奶（1≤N≤7
）。每条限制的形式为“X必须紧邻着 Y挤奶”，要求奶牛 X在挤奶顺序中必须紧接在奶牛 Y之后，或者紧接在奶牛 Y 之前。

请帮助 Farmer John 求出一种满足所有限制的奶牛挤奶顺序。保证这样的顺序是存在的。如果有多种顺序都满足要求，请输出字典序最小的一种。也就是说，第一头奶牛需要是所有可能排在任意合法奶牛顺序的第一位的奶牛中名字字典序最小的。在所有合法的以这头字典序最小的奶牛为首的奶牛顺序中，第二头奶牛需要是字典序最小的，以此类推。
这段代码的目的是在给定一些牛名和它们之间的特定排列要求的情况下，找出这些牛的一个有效排列。这些牛的名字存储在一个字符串向量 `cows` 中，而它们之间的排列要求则存储在一个包含字符串对的向量 `res` 中。以下是代码的逐行解释和注释：

```cpp
#include<bits/stdc++.h> // 包含所有标准库
using namespace std;

// 初始牛的名字
vector<string> cows = {"Bessie", "Buttercup", "Belinda", "Beatrice", "Bella", "Blue", "Betsy", "Sue"};

int main() {
    int n; // 输入的条件数量
    vector<pair<string, string>> res; // 存储牛的排列要求
    cin >> n; // 读取条件数量
    sort(cows.begin(), cows.end()); // 对牛名进行排序以便生成全排列

    while (n--) {
        string a, b, t; // 用于读取输入
        cin >> a; // 读取第一头牛的名字
        cin >> t >> t >> t >> t; // 跳过无关的单词（"must be milked beside"）
        cin >> b; // 读取第二头牛的名字
        res.push_back({a, b}); // 将这对牛的排列要求存储到res中
    }

    // 生成cows的全排列，并检查每个排列是否满足条件
    while (next_permutation(cows.begin(), cows.end())) {
        bool pass = true; // 标记当前排列是否满足所有条件
        for (auto p : res) {
            string cow1 = p.first;
            string cow2 = p.second;
            auto a = find(cows.begin(), cows.end(), cow1);
            auto b = find(cows.begin(), cows.end(), cow2);
            if (abs(a - b) != 1) pass = false; // 如果两头牛不是相邻的，则这个排列不满足条件
        }
        if (pass == true) break; // 如果找到一个满足所有条件的排列，终止循环
    }

    // 输出有效排列
    for (auto cow : cows) {
        cout << cow << endl;
    }

    return 0;
}
```

在这个程序中：

- `cows` 是一个包含所有牛名的向量。
- `res` 用来存储牛之间的排列要求，每个要求是一对相邻的牛。
- 程序首先将 `cows` 排序，以便生成全排列。
- 在 `while` 循环中，程序读取每对相邻牛的名字，并将它们存储在 `res` 中。
- 然后，程序使用 `next_permutation` 生成 `cows` 的所有排列，并对每个排列检查是否满足 `res` 中的所有要求。
- 一旦找到一个满足所有要求的排列，程序就会跳出循环并输出这个排列。

这个代码片段是解决特定类型的排列问题的一个例子，其中有一组初始元素和一些特定的排列条件。通过生成所有可能的排列并检查每个排列是否满足条件，程序能够找到一个有效的解决方案。

---

* Link: https://github.com/justonehe/Algorithm/issues/27
* Labels: `usaco`, `全排列`
* Creation Date: 2024-01-07T00:58:19Z
