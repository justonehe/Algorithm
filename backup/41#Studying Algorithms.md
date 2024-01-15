# Studying Algorithms

https://codeforces.com/gym/102951/problem/B
Steph wants to improve her knowledge of algorithms over winter break. She has a total of X (1≤X≤10^4) minutes to dedicate to learning algorithms. There are N (1≤N≤100) algorithms, and each one of them requires ai (1≤ai≤100) minutes to learn. Find the maximum number of algorithms she can learn.
```c++
#include<bits/stdc++.h>
using namespace std;
int main(){
	int n,x,a[110];
	cin>>n>>x;
	for(int i=0;i<n;i++) cin>>a[i];
	sort(a,a+n);
	int cnt=0;
	for(int i=0;i<=n;i++){
		cnt+=a[i];
		if(cnt>x){
			cout<<i;
			return 0;
		}
	}
cout<<n;
return 0;
}
```

---

* Link: https://github.com/justonehe/Algorithm/issues/41
* Labels: `usaco`, `贪心`
* Creation Date: 2024-01-15T12:20:25Z
