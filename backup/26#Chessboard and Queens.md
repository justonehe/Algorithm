# Chessboard and Queens

https://cses.fi/problemset/task/1624
Your task is to place eight queens on a chessboard so that no two queens are attacking each other. As an additional challenge, each square is either free or reserved, and you can only place queens on the free squares. However, the reserved squares do not prevent queens from attacking each other.

How many possible ways are there to place the queens?

Input
The input has eight lines, and each of them has eight characters. Each square is either free (.) or reserved (*).
#### 解释
在这个代码中：

col, diag1, diag2 分别用于标记列和两个对角线方向上是否已经有皇后。这是为了确保放置的每个皇后都不会与已经放置的皇后在同一列或对角线上。
board 用于存储棋盘的初始状态，包括不能放置皇后的位置（用 '*' 表示）。
solve 函数是递归函数，用于逐行尝试放置皇后，并通过回溯算法找出所有可能的解决方案。
在 main 函数中，首先读取棋盘的输入，然后调用 solve 函数开始解决问题，最后输出解的总数。
这种方法利用了递归和回溯，是解决八皇后问题的一种典型和有效方式。
```c++
#include<bits/stdc++.h> // 包含标准库
using namespace std;

// 辅助数组，用于标记冲突
bool col[8], diag1[16], diag2[16]; // 分别标记列和两个方向的对角线是否有皇后
string board[8]; // 棋盘，'*'表示不能放置皇后的位置
int ans = 0; // 存储解的数量

// 递归函数来解决八皇后问题
void solve(int x) {
    if (x == 8) { // 如果已经成功放置了8个皇后
        ans++; // 增加解的计数
        return;
    }
    for (int i = 0; i < 8; i++) { // 尝试在当前行的每一列放置皇后
        // 检查当前位置是否可以放置皇后
        if (col[i] || diag1[i - x + 7] || diag2[i + x] || board[x][i] == '*') continue;
        
        // 放置皇后，并标记冲突
        col[i] = diag1[i - x + 7] = diag2[i + x] = 1;
        solve(x + 1); // 递归处理下一行
        // 回溯，撤销皇后的放置
        col[i] = diag1[i - x + 7] = diag2[i + x] = 0;
    }
}

int main() {
    for (int i = 0; i < 8; i++) {
        cin >> board[i]; // 输入棋盘的每一行
    }
    
    solve(0); // 从第一行开始解决问题
    cout << ans; // 输出解的数量

    return 0;
}
```

---

* Link: https://github.com/justonehe/Algorithm/issues/26
* Labels: `递归`, `usaco`, `dfs`
* Creation Date: 2024-01-06T01:35:22Z
