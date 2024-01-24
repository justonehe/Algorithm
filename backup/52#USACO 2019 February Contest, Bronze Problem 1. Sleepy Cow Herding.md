# USACO 2019 February Contest, Bronze Problem 1. Sleepy Cow Herding

http://www.usaco.org/index.php?page=viewproblem2&cpid=915&lang=zh
Farmer John的三头获奖奶牛Bessie、Elsie和Mildred，总是会迷路走到农场上遥远的地方去！他需要你帮助将她们一起赶回来。
农场的草地大体是一块狭长的区域——我们可以将其想象成一条数轴，奶牛可以占据数轴上的任意整数位置。这3头奶牛现在正位于不同的整数位置，Farmer John想要移动她们，使得她们占据三个相邻的位置（例如，位置6、7、8）。

不幸的是，奶牛们现在很困，Farmer John要让她们集中精力听从命令移动并不容易。任意时刻，他只能使得一头处在“端点”（在所有奶牛中位置最小或最大）位置的奶牛移动。当他移动奶牛时，他可以命令她走到任意一个未被占用的整数位置，只要在新的位置上她不再是一个端点。可以看到随着时间的推移，这样的移动可以使奶牛们趋向越来越近。

请求出使得奶牛们集中到相邻位置所进行的移动次数的最小和最大可能值。
···
#include<bits/stdc++.h>
using namespace std;
int main(){
	int a,b,c,d,e,f;
	cin>>a>>b>>c;
	d=min(min(a,b),c);
	f=max(max(a,b),c);
	e=a+b+c-d-f;
	int minn,maxn;
	if(f-d==2) minn=0;
	else if(e-d==2||f-e==2) minn=1;
	else minn=2;
	maxn=max(e-d,f-e)-1;
	cout<<minn<<endl;
	cout<<maxn;

return 0;
}
···

---

* Link: https://github.com/justonehe/Algorithm/issues/52
* Labels: `模拟`, `usaco`
* Creation Date: 2024-01-24T02:22:37Z
