# USACO 2021 January Contest, Bronze Problem 2. Even More Odd Photos

http://www.usaco.org/index.php?page=viewproblem2&cpid=1084&lang=zh
Farmer John 正再一次尝试给他的 N 头奶牛拍照（2≤N≤1000）。
每头奶牛有一个范围在 1…100之内的整数的「品种编号」。Farmer John 对他的照片有一个十分古怪的构思：他希望将所有的奶牛分为不相交的若干组（换句话说，将每头奶牛分到恰好一组中）并将这些组排成一行，使得第一组的奶牛的品种编号之和为偶数，第二组的编号之和为奇数，以此类推，奇偶交替。

Farmer John 可以分成的最大组数是多少？

输入格式（从终端/标准输入读入）：
输入的第一行包含 N。下一行包含 N 个空格分隔的整数，为 N 头奶牛的品种编号。
输出格式（输出至终端/标准输出）：
输出 Farmer John 的照片中的最大组数。可以证明，至少存在一种符合要求的分组方案。
#### 本题重点在于找到奇偶数字个数和最终结果的关系。具体的每个牛的编号数字不重要。
```c++
#include<bits/stdc++.h>
using namespace std;
int N,ans;
int cow[1010]; 
int groupcow(int e, int o){
	int diff=o-e;
	if(diff==0) return o+e;
	else if(diff==1) return o+e-2;
	else if(diff==2) return o+e-1;
	else{
	
		o-=2;
		e++;
		
	}
	return groupcow(e,o);
}
int main(){
	cin>>N;
	int tmp,oddc=0,evenc=0;
	for(int i=0;i<N;i++){
		cin>>tmp;
		if(tmp%2==0) evenc++;
		else oddc++;
	}

	if(evenc>oddc) ans=oddc*2+1;
	else{
		ans=groupcow(evenc,oddc);
	}
	cout<<ans;

return 0;
}
```

---

* Link: https://github.com/justonehe/Algorithm/issues/47
* Labels: `usaco`, `贪心`
* Creation Date: 2024-01-19T14:09:07Z
