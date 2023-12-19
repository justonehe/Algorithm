# USACO 2016 February Contest, Bronze Problem 2. Circular Barn

Being a fan of contemporary architecture, Farmer John has built a new barn in the shape of a perfect circle. Inside, the barn consists of a ring of n
 rooms, numbered clockwise from 1…n
 around the perimeter of the barn (3≤n≤1,000
). Each room has doors to its two neighboring rooms, and also a door opening to the exterior of the barn.
Farmer John wants exactly ri
 cows to end up in each room i
 (1≤ri≤100
). To herd the cows into the barn in an orderly fashion, he plans to unlock the exterior door of a single room, allowing the cows to enter through that door. Each cow then walks clockwise through the rooms until she reaches a suitable destination. Farmer John wants to unlock the exterior door that will cause his cows to collectively walk a minimum total amount of distance. Please determine the minimum total distance his cows will need to walk, if he chooses the best such door to unlock. The distance walked by a single cow is the number of interior doors through which she passes.

INPUT FORMAT (file cbarn.in):
The first line of input contains n
. Each of the remaining n
 lines contain r1…rn
.
OUTPUT FORMAT (file cbarn.out):
Please write out the minimum total amount of distance the cows collectively need to travel.
```c++
#include<bits/stdc++.h>
using namespace std;
int main(){
	int n,a[1100],sum=0,minm=100000000,cnt;
	cin>>n;
	for(int i=0;i<n;i++) cin>>a[i];
	for(int i=0;i<n;i++){
		sum=0;
		for(int j=0;j<n;j++){
			sum+=j*a[(i+j)%n];
//			cout<<sum<<endl;
		}
//		cout<<sum<<endl;
		if(sum<minm){
			minm=sum;
			cnt=i;
		}
		
	}
	cout<<minm;
	

return 0;
}
```

---

* Link: https://github.com/justonehe/Algorithm/issues/4
* Labels: `模拟`
* Creation Date: 2023-12-19T07:56:49Z
