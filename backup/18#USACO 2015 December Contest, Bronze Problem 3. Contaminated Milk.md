# USACO 2015 December Contest, Bronze Problem 3. Contaminated Milk

http://www.usaco.org/index.php?page=viewproblem2&cpid=569
Farmer John, known far and wide for the quality of the milk produced on his farm, is hosting a milk-tasting party for N of his best friends (1≤N≤50). Unfortunately, of the M types of milk featured at the party (1≤M≤50), exactly one of them has gone bad, but Farmer John does not know which one! Anyone who drinks the bad milk will later become sick, either during the remainder of the party or afterward.
You are given a transcript of the party -- who drinks what when, and also who gets sick when. Based on this information, you can deduce which of the milks could possibly be the bad one. Using this knowledge, help Farmer John determine the minimum number of doses of medicine he will need to obtain in order to guarantee that he can cure all of the individuals who become sick, either during or after the party.

INPUT FORMAT (file badmilk.in):
The first line of the input contains integers N, M, D, and S.
The next D lines (1≤D≤1000) each contain three integers p,m,t, indicating that person p drank milk m at time t. The value of p is in the range 1…N, m is in the range 1…M, and t is in the range 1…10. A person may drink the same milk several times, and may also drink several types of milk at the same point in time.

The next s lines (1≤S≤N) each contain two integers p,t, indicating that person p gets sick at time t. The value of p is in the range 1…N, and t is in the range 1…100. Each person gets sick at most once, and they only get sick because they drank the bad milk at some strictly earlier point in time.
### 代码有问题，需修改，只有80分
```c++
#include<bits/stdc++.h> // 包含标准库
using namespace std;

// 声明全局变量
int n, m, d, s; // 分别代表人数、牛奶种类数、饮用事件数量、生病的人数

// 数组用于存储饮用和生病的数据
int personDrink[1001], milkDrink[1001], timeDrink[1001]; // 存储每个饮用事件的相关数据
int personSick[51], timeSick[51]; // 存储每个生病事件的相关数据

// 检查某人在某时间之前是否喝过某种牛奶
bool drinkbefore(int person, int milk, int time) {
    for (int i = 0; i < d; i++) {
        if (personDrink[i] == person && milkDrink[i] == milk && timeDrink[i] < time) 
            return true;
    }
    return false;
}

// 检查某种牛奶是否可能是致病源
bool milkBad(int x) {
    for (int i = 0; i < s; i++) {
        // 如果有生病的人在生病前没有喝这种牛奶，则这种牛奶不可能是致病源
        if (!drinkbefore(personSick[i], x, timeSick[i])) return false;
    }
    return true;
}

// 计算喝了某种牛奶的人数
int count(int milk) {
    bool drink[51] = {0};
    for (int i = 0; i < d; i++) {
        if (milkDrink[i] == milk) drink[personDrink[i]] = 1;
    }
    int cnt = 0;
    for (int i = 0; i < 50; i++) {
        cnt += drink[i]; 
    }
    return cnt;
}

int main() {
    cin >> n >> m >> d >> s; // 输入人数、牛奶种类数、饮用事件数量、生病的人数
    for (int i = 0; i < d; i++) {
        cin >> personDrink[i] >> milkDrink[i] >> timeDrink[i]; // 输入饮用事件数据
    }
    for (int i = 0; i < s; i++) {
        cin >> personSick[i] >> timeSick[i]; // 输入生病事件数据
    }
    int ans = 0;
    for (int i = 0; i < m; i++) {
        // 检查每种牛奶是否可能是致病源，并计算相应的人数
        if (milkBad(i)) ans = max(ans, count(i));
    }
    cout << ans; // 输出结果
    return 0;
}

```

---

* Link: https://github.com/justonehe/Algorithm/issues/18
* Labels: `usaco`, `需修改`, `暴力`
* Creation Date: 2024-01-01T03:28:58Z
