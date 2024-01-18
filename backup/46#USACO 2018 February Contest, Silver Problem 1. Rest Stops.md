# USACO 2018 February Contest, Silver Problem 1. Rest Stops

http://www.usaco.org/index.php?page=viewproblem2&cpid=810
Farmer John和他的私人教练Bessie正在徒步攀登温哥牛山。基于他们的目的（也是你的目的），这座山可以用一条长为L
米（1≤L≤106）的长直路径表示。Farmer John会沿着这条路径以每米rF秒（1≤rF≤100）的固定速度攀登。由于他正在训练他的耐力，他在途中不会进行任何的休息。然而Bessie可以在休息站休息，在那里她能够找到一些美味的嫩草。当然，她也不能在任何地方都休息！在路径上总共有N个休息站（1≤N≤105）；第i个休息站距离路径的起点xi米（0<xi<L），美味值为ci（1≤ci≤106）。如果Bessie在休息站i休息了t秒，她能够得到ci⋅t个美味单位。

不在休息站的时候，Bessie会以每米rB秒（1≤rB≤106）的固定速度攀登。由于Bessie年轻而健康，rB严格小于rF
。

Bessie想要吃到最多的美味嫩草。然而她也担心Farmer John；她认为如果在任何时候她位于Farmer John身后，Farmer John可能就会失去前进的动力了！

帮助Bessie求出，在确保Farmer John能够完成登山的情况下，她能够获得的最多的美味单位。
#### 和2023年CSP-J公路题高度相似
```c++
#include<bits/stdc++.h>
using namespace std;
long long L,N,rf,rb;
long long x[100010],c[100010];
bool mark[100010];
int main(){
	freopen("reststops.in","r",stdin);
	freopen("reststops.out","w",stdout);
	cin>>L>>N>>rf>>rb;
	for(int i=0;i<N;i++){
		cin>>x[i]>>c[i];

	}
	int max=0;
	for(int i=N-1;i>=0;i--){
		mark[i]=false;
		if(c[i]>max){
			mark[i]=true;
			max=c[i];
		}
	}
	long long ans=0,prev=0;
	for(int i=0;i<N;i++){
		if(mark[i]){
			long long dis=x[i]-prev;
			long long tf=dis*rf, tb=dis*rb;
			ans+=(tf-tb)*c[i];
			prev=x[i];
		}
	}
cout<<ans;
return 0;
}
```

---

* Link: https://github.com/justonehe/Algorithm/issues/46
* Labels: `usaco`, `贪心`
* Creation Date: 2024-01-18T08:08:37Z
