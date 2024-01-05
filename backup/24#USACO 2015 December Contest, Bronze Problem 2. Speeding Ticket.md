# USACO 2015 December Contest, Bronze Problem 2. Speeding Ticket

http://www.usaco.org/index.php?page=viewproblem2&cpid=568
Always the troublemaker, Bessie the cow has stolen Farmer John's tractor and taken off down the road!
The road is exactly 100 miles long, and Bessie drives the entire length of the road before ultimately being pulled over by a police officer, who gives Bessie a ticket for exceeding the speed limit, for having an expired license, and for operating a motor vehicle while being a cow. While Bessie concedes that the last two tickets are probably valid, she questions whether the police officer was correct in issuing the speeding ticket, and she wants to determine for herself if she has indeed driven faster than the speed limit for part of her journey.

The road is divided into N segments, each described by a positive integer length in miles, as well as an integer speed limit in the range 1…100 miles per hour. As the road is 100 miles long, the lengths of all N segments add up to 100. For example, the road might start with a segment of length 45 miles, with speed limit 70, and then it might end with a segment of length 55 miles, with speed limit 60.

Bessie's journey can also be described by a series of segments, M of them. During each segment, she travels for a certain positive integer number of miles, at a certain integer speed. For example, she might begin by traveling 50 miles at a speed of 65, then another 50 miles at a speed of 55. The lengths of all M segments add to 100 total miles. Farmer John's tractor can drive 100 miles per hour at its fastest.

#### 思路
本题根据给出的每段路程的限速和实际速度，穷举出100mile（数组）中每一段的限速和实际速度并依次比较。因为数据量小（小于100），直接穷举即可。
```c++
#include<bits/stdc++.h>
using namespace std;
int n,m;
vector <int> v1,d1,v2,d2;
int s1[105],s2[105];
int main(){
	cin>>n>>m;
	v1.resize(n+1);
	d1.resize(n+1);
	v2.resize(m+1);
	d2.resize(m+1);
	for(int i=1;i<=n;i++) cin>>d1[i]>>v1[i];
	for(int i=1;i<=m;i++) cin>>d2[i]>>v2[i];
	int a=0,b=0;
	for(int i=1;i<=n;i++){
		a+=d1[i-1];
		b+=d1[i-1]+d1[i];
		for(int j=a;j<b;j++) s1[j]=v1[i];
	}
	a=0,b=0;
	for(int i=1;i<=m;i++){
		a+=d2[i-1];
		b+=d2[i-1]+d2[i];
		for(int j=a;j<b;j++) s2[j]=v2[i];
	}
	int ans=0;
	for(int i=0;i<100;i++){
		ans=max(ans,s2[i]-s1[i]);
	}
cout<<ans;
return 0;
}
```

---

* Link: https://github.com/justonehe/Algorithm/issues/24
* Labels: `模拟`, `usaco`
* Creation Date: 2024-01-05T12:29:12Z
