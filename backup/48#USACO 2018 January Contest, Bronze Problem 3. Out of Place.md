# USACO 2018 January Contest, Bronze Problem 3. Out of Place

http://www.usaco.org/index.php?page=viewproblem2&cpid=785
Feeling ambitious, Farmer John plans to attempt something that never seems to go quite right: he wants to take a photograph of his entire herd of cows.
To make the photograph look nice, he wants the cows to line up in a single row from shortest to tallest. Unfortunately, right after he has the cows line up this way, Bessie the cow, always the troublemaker, steps out of line and re-inserts herself at some other location in the lineup!

Farmer John would like to swap pairs of cows so the entire herd is again lined up properly. Please help him determine the minimum number of swaps he needs to make between pairs of cows in order to achieve this goal.
```c++
#include<bits/stdc++.h>
using namespace std;
int N,c[110],s[110]; 
int main(){
	cin>>N;
	for(int i=0;i<N;i++) {
		cin>>c[i];
		s[i]=c[i];
	}
	sort(s,s+N);
	int cnt=0;
	for(int i=0;i<N;i++){
		if(c[i]!=s[i]) cnt++;
	}
	cout<<max(0,cnt-1);
return 0;
}
```

---

* Link: https://github.com/justonehe/Algorithm/issues/48
* Labels: `usaco`, `贪心`, `排序`
* Creation Date: 2024-01-20T01:41:26Z
