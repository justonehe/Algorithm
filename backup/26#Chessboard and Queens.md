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
#include<bits/stdc++.h>
using namespace std;

// 初始化数组来记录列、对角线和棋盘
bool col[8],diag1[16],diag2[16];
string board[8];
int ans=0;

// 递归函数来解决问题
void solve(int x){
    // 如果我们已经放置了所有8个皇后，则增加答案计数并返回
    if(x==8) {
        ans++;
        return;
    }
    // 遍历当前行的所有列
    for(int i=0;i<8;i++){
        // 如果此列已经被占用或者放置一个皇后在这里将导致对另一个皇后的攻击，请继续转到下一列
        if(col[i]==1 || diag1[i-x+7]==1 || diag2[i+x]==1 || board[x][i]=='*') continue;
        // 否则，标记此列和对角线为占用，并转到下一行
        col[i]=1,diag1[i-x+7]=1,diag2[i+x]=1;
        solve(x+1);
        // 回溯并取消标记此列和对角线
        col[i]=0,diag1[i-x+7]=0,diag2[i+x]=0;
    }
}

int main(){
    // 读取棋盘的初始状态
    for(int i=0;i<8;i++){
        cin>>board[i];
    }

    // 开始解决问题
    solve(0);
    cout<<ans;

    return 0;
}
```

---

* Link: https://github.com/justonehe/Algorithm/issues/26
* Labels: `递归`, `usaco`, `dfs`
* Creation Date: 2024-01-06T01:35:22Z
