# USACO 2017 US Open Contest, Silver Problem 2. Bovine Genomics

http://www.usaco.org/index.php?page=viewproblem2&cpid=739
Farmer John owns N cows with spots and N cows without spots. Having just completed a course in bovine genetics, he is convinced that the spots on his cows are caused by mutations in the bovine genome.
At great expense, Farmer John sequences the genomes of his cows. Each genome is a string of length M built from the four characters A, C, G, and T. When he lines up the genomes of his cows, he gets a table like the following, shown here for N=3:

Positions:    1 2 3 4 5 6 7 ... M

Spotty Cow 1: A A T C C C A ... T
Spotty Cow 2: G A T T G C A ... A
Spotty Cow 3: G G T C G C A ... A

Plain Cow 1:  A C T C C C A ... G
Plain Cow 2:  A G T T G C A ... T
Plain Cow 3:  A G T T C C A ... T
Looking carefully at this table, he surmises that positions 2 and 4 are sufficient to explain spottiness. That is, by looking at the characters in just these two positions, Farmer John can predict which of his cows are spotty and which are not (for example, if he sees G and C, the cow must be spotty).

Farmer John is convinced that spottiness can be explained not by just one or two positions in the genome, but by looking at a set of three distinct positions. Please help him count the number of sets of three distinct positions that can each explain spottiness.
### 代码分析
这段代码实现的是一种特定的序列分析算法，但它并不直接对应于传统算法的经典分类，如排序或搜索算法。相反，它采用了一种特定的策略来比较两组DNA序列，并识别独特的三位点组合。下面是这段代码所采用的算法的关键特点和步骤：

1. **数据预处理**：将DNA序列中的每个字符（'A', 'C', 'G', 'T'）转换为一个整数（0, 1, 2, 3）。这样做是为了便于后续的计算和比较。

2. **组合生成**：代码在序列的每个可能的三位点组合上进行迭代。这些组合是通过三个嵌套的循环生成的，分别对应于序列中的三个不同位置（`j1, j2, j3`）。

3. **唯一性检验**：对于每个生成的三位点组合，算法检查这个组合在第一组序列（`spot`）中是否存在，同时在第二组序列（`plain`）中是否不存在。这是通过一个辅助数组（`A`）来实现的，该数组用于记录特定的三位点组合是否在`spot`序列中出现过。

4. **计数和输出**：每当找到一个符合条件的组合（即在`spot`中出现但在`plain`中未出现），算法就增加计数器（`answer`）。最后，输出这个计数器的值，即满足条件的组合总数。

总的来说，这个算法是为了解决一个特定的问题（在两组DNA序列中识别独特的三位点组合）而设计的，它结合了数据预处理、组合生成、唯一性检验和结果计数等步骤。这种方法在生物信息学和序列分析中是常见的，尽管它不属于任何传统算法分类。
```c++
#include<bits/stdc++.h> // 包含常用的库
using namespace std;

// 声明全局变量
int N, M; // N 和 M 分别表示序列的数量和长度
string spot[500], plain[500]; // 存储两组序列
int S[500][50], P[500][50]; // 将字符序列转换成整数序列
int A[64]; // 用于测试位置的辅助数组

// 测试给定位置组合 (j1, j2, j3) 是否满足条件
bool test_location(int j1, int j2, int j3) {
    bool good = true;
    for (int i = 0; i < N; i++) {
        // 将spot序列中的特定位置转换为一个整数，并标记在A中
        A[S[i][j1] * 16 + S[i][j2] * 4 + S[i][j3]] = 1;
    }
    for (int i = 0; i < N; i++) {
        // 检查plain序列是否有与spot序列在A中相同的组合
        if (A[P[i][j1] * 16 + P[i][j2] * 4 + P[i][j3]])
            good = false;
    }
    for (int i = 0; i < N; i++) {
        // 清除数组A的标记
        A[S[i][j1] * 16 + S[i][j2] * 4 + S[i][j3]] = 0;
    }
    return good;
}

int main() {
    cin >> N >> M; // 输入序列数量和长度
    for (int i = 0; i < N; i++) {
        cin >> spot[i]; // 输入spot序列
        for (int j = 0; j < M; j++) {
            // 将字符转换为对应的整数
            if (spot[i][j] == 'A') S[i][j] = 0;
            if (spot[i][j] == 'C') S[i][j] = 1;
            if (spot[i][j] == 'G') S[i][j] = 2;
            if (spot[i][j] == 'T') S[i][j] = 3;
        }
    }
    for (int i = 0; i < N; i++) {
        cin >> plain[i]; // 输入plain序列
        for (int j = 0; j < M; j++) {
            // 同样地将字符转换为对应的整数
            if (plain[i][j] == 'A') P[i][j] = 0;
            if (plain[i][j

```

---

* Link: https://github.com/justonehe/Algorithm/issues/17
* Labels: `usaco`, `暴力`
* Creation Date: 2023-12-31T08:03:08Z
