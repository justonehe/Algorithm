# USACO 2020 February Contest, Bronze Problem 2. Mad Scientist

http://www.usaco.org/index.php?page=viewproblem2&cpid=1012&lang=zh
```c++
#include<bits/stdc++.h>
using namespace std;
int main(){
	long long n;
	cin>>n;
	string a,b;
	cin>>a>>b;
	bool notmatch=false;
	int cnt=0;
	for(long long i=0;i<n;i++){
		if(a[i]!=b[i]){
			if(notmatch==false){
				notmatch=true;
				cnt++;
			}
			
		}
		else notmatch=false;
	}
	cout<<cnt;

return 0;
}
```

---

* Link: https://github.com/justonehe/Algorithm/issues/44
* Labels: `usaco`, `贪心`
* Creation Date: 2024-01-17T03:29:11Z
