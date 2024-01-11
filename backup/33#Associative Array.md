# Associative Array

https://judge.yosupo.jp/problem/associative_array

```c++
#include<bits/stdc++.h>
using namespace std;
map<long long, long long> s;
int n;
int main(){
		int q;
	cin>>n;
	while(n--){
	
		cin>>q;
		if(q==0) {
			long long k,v;
		cin>>k>>v;
		s[k]=v;
	}
		else
		{
			long long k;
		 cin>>k;
		 cout<<s[k]<<endl;
	}
		
}

return 0;
}
```

---

* Link: https://github.com/justonehe/Algorithm/issues/33
* Labels: `usaco`, `queue`
* Creation Date: 2024-01-11T05:11:30Z
