# USACO 2018 December Contest, Bronze Problem 3. Back and Forth

http://www.usaco.org/index.php?page=viewproblem2&cpid=857&lang=zh
Farmer John有两个挤奶棚，每个挤奶棚里各有一个奶罐和一个装有10个各种尺寸的桶的储物柜。他喜欢将在两个挤奶棚之间来回运送牛奶作为一种锻炼方式。
周一，Farmer John量了恰好1000加仑的牛奶放在第一个挤奶棚的奶罐里，又量了恰好1000加仑的牛奶放在第二个挤奶棚的奶罐里。

周二，他从第一个挤奶棚里取出一个桶，并装满牛奶，然后将牛奶运到第二个挤奶棚，并将牛奶倒进奶罐。他把这个桶留在了第二个挤奶棚。

周三，他从第二个挤奶棚里取出一个桶（可能是周二留在这里的），并装满牛奶，然后将牛奶运到第一个挤奶棚，并将牛奶倒进奶罐。他把这个桶留在了第一个挤奶棚。

周四，他从第一个挤奶棚里取出一个桶（可能是周三留在这里的），并装满牛奶，然后将牛奶运到第二个挤奶棚，并将牛奶倒进奶罐。他把这个桶留在了第二个挤奶棚。

周五，他从第二个挤奶棚里取出一个桶（可能是周二或周四留在这里的），并装满牛奶，然后将牛奶运到第一个挤奶棚，并将牛奶倒进奶罐。他把这个桶留在了第一个挤奶棚。

此时Farmer John测量了第一个挤奶棚的奶罐里的牛奶。他总共可能得到多少种不同的读数？
#### 算法和解释
好的，这段代码是为了解决农夫约翰在两个谷仓之间搬运牛奶的问题。每个谷仓初始都有1000加仑的牛奶，以及10个不同大小的桶。农夫约翰会交替使用这些桶从一个谷仓搬运牛奶到另一个谷仓。代码的目标是找出农夫约翰活动后第一个谷仓中可能的不同牛奶量。下面是对代码的解释和注释：

```cpp
#include<bits/stdc++.h> // 包含所有标准库

using namespace std;
using ll = long long; // 定义 'll' 为 'long long' 类型的别名
set<ll> possible; // 用集合存储所有可能的最终牛奶量

// 递归函数来模拟搬运过程
void solve(ll trips_left, const vector<ll>& buckets_here, const vector<ll>& buckets_there, ll tank_here, ll tank_there){
    if(trips_left == 0){
        possible.insert(tank_here); // 如果没有剩余行程，则将当前量加入集合
    }
    else{
        // 遍历当前位置的所有桶
        for(ll taken_idx = 0; taken_idx < buckets_here.size(); taken_idx++){
            ll bucket = buckets_here[taken_idx]; // 当前桶的容量
            vector<ll> new_buckets_dest(buckets_there); // 目的地的新桶列表
            new_buckets_dest.push_back(bucket); // 将当前桶添加到目的地
            vector<ll> new_buckets_src; // 源地的新桶列表
            // 将除了当前桶以外的所有桶添加到源地的新桶列表
            for(ll i = 0; i < buckets_here.size(); i++){
                if(i != taken_idx){
                    new_buckets_src.push_back(buckets_here[i]);
                }
            }
            ll new_tank_dest = tank_there + bucket; // 目的地谷仓的新牛奶量
            ll new_tank_src = tank_here - bucket; // 源地谷仓的新牛奶量
            // 递归处理下一次搬运
            solve(trips_left - 1, new_buckets_dest, new_buckets_src, new_tank_dest, new_tank_src);
        }
    }
}

int main() {
    vector<ll> buckets_here; // 当前谷仓的桶列表
    for(ll i = 0; i < 10; i++){
        ll bucket;
        cin >> bucket; // 输入桶的大小
        buckets_here.push_back(bucket);
    }
    vector<ll> buckets_there; // 另一个谷仓的桶列表
    for(ll i = 0; i < 10; i++){
        ll bucket;
        cin >> bucket; // 输入桶的大小
        buckets_there.push_back(bucket);
    }
    // 开始解决问题，初始两个谷仓都有1000加仑牛奶
    solve(4, buckets_here, buckets_there, 1000, 1000);
    cout << possible.size() << endl; // 输出可能的不同牛奶量数量

    return 0;
}
```

这个代码通过递归来模拟农夫约翰在四天内使用不同桶搬运牛奶的所有可能情况，并计算第一个谷仓最终可能的牛奶量。它考虑了每天使用的不同桶，以及牛奶的流动，最后统计出所有可能的牛奶量的数量。

---

* Link: https://github.com/justonehe/Algorithm/issues/28
* Labels: `递归`, `usaco`
* Creation Date: 2024-01-08T12:36:31Z
