# USACO 2019 January Contest, Silver Problem 1. Grass Planting

http://www.usaco.org/index.php?page=viewproblem2&cpid=894
到了一年中Farmer John在他的草地里种草的时间了。整个农场由N块草地组成（1≤N≤105），方便起见编号为1…N，由N−1条双向的小路连接，每块草地都可以经过一些小路到达其他所有的草地。
Farmer John当然可以在每块草地里种不同种类的草，但是他想要使得使用的草的种类数最小，因为他用的草的种类数越多，他就需要负担更高的花费。

不幸的是，他的奶牛们对选择农场上的草表现得十分苛刻。如果两块相邻（由一条小路直接相连）的草地种了同一种草，或者即使是两块接近相邻（均可由一条小路直接连向同一块草地）的草地，那么奶牛们就会抱怨她们进餐的选择不够多样。Farmer John能做的只能是抱怨这些奶牛，因为他知道她们不能被满足的时候会制造多大的麻烦。

请帮助Farmer John求出他的整个农场所需要的最少的草的种类数。
```c++
#include<bits/stdc++.h>
using namespace std;
int main(){
	int n;
	cin>>n;
	vector<int> degree(n);
	int a,b;
	for(int i=1;i<n;i++){
		cin>>a>>b;
		degree[a-1]++;
		degree[b-1]++;
	}
	int ans=0;
	for(int i=0;i<n;i++)
		ans=max(ans,degree[i]);
	cout<<ans+1;

return 0;
}

```

---

* Link: https://github.com/justonehe/Algorithm/issues/50
* Labels: `usaco`, `图论`
* Creation Date: 2024-01-22T05:27:47Z
