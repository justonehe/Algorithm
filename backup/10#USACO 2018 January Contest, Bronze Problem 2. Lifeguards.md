# USACO 2018 January Contest, Bronze Problem 2. Lifeguards

http://www.usaco.org/index.php?page=viewproblem2&cpid=784
Farmer John has opened a swimming pool for his cows, figuring it will help them relax and produce more milk.
To ensure safety, he hires N cows as lifeguards, each of which has a shift that covers some contiguous interval of time during the day. For simplicity, the pool is open from time t=0 until time t=1000 on a daily basis, so each shift can be described by two integers, giving the time at which a cow starts and ends her shift. For example, a lifeguard starting at time t=4 and ending at time t=7 covers three units of time (note that the endpoints are "points" in time).
Unfortunately, Farmer John hired 1 more lifeguard than he has the funds to support. Given that he must fire exactly one lifeguard, what is the maximum amount of time that can still be covered by the shifts of the remaining lifeguards? An interval of time is covered if at least one lifeguard is present.
### 最后一个得分点错了
```c++
#include<bits/stdc++.h>
using namespace std;
int t[1100],t1[1100],l[100],r[100];
int n,maxt=0,cnt=0;
int main(){
	cin>>n;
	for(int i=1;i<=n;i++){
		cin>>l[i]>>r[i];
		for(int j=l[i];j<r[i];j++){
		
			t[j]++;
			
		}
	
	}

	for(int i=1;i<=n;i++){
		
		for(int j=1;j<=1000;j++) t1[j]=t[j];
		
		for(int j=l[i];j<r[i];j++){
			t1[j]--;
		}
		cnt=0;
		for(int i=1;i<=1000;i++) 
	{
	
		if(t1[i]!=0) cnt++;
	}
	maxt=max(maxt,cnt);
}
cout<<maxt;
return 0;
}
```

---

* Link: https://github.com/justonehe/Algorithm/issues/10
* Labels: `usaco`, `需修改`, `暴力`
* Creation Date: 2023-12-24T00:31:21Z
