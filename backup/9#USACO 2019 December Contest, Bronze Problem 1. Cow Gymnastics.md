# USACO 2019 December Contest, Bronze Problem 1. Cow Gymnastics

http://www.usaco.org/index.php?page=viewproblem2&cpid=963
为了提高健康水平，奶牛们开始进行体操训练了！Farmer John 选定了他最喜爱的奶牛 Bessie 来执教其他 N头奶牛，同时评估她们学习不同的体操技术的进度。
K次训练课的每一次（1≤K≤10），Bessie 都会根据 N头奶牛的表现给她们进行排名（1≤N≤20）。之后，她对这些排名的一致性产生了好奇。称一对不同的奶牛是一致的，如果其中一头奶牛在每次训练课中都表现得都比另一头要好。

请帮助 Bessie 计算一致的奶牛的对数。

输入格式（文件名：gymnastics.in）：
输入的第一行包含两个正整数 K 和 N。以下 K 行每行包含整数 1…N的某种排列，表示奶牛们的排名（奶牛们用编号 1…N进行区分）。如果在某一行中 A出现在 B之前，表示奶牛 A表现得比奶牛 B要好。
输出格式（文件名：gymnastics.out）：
输出一行，包含一致的奶牛的对数。
输入样例：
3 4
4 1 2 3
4 1 3 2
4 2 1 3
输出样例：
4
一致的奶牛对为 (1,4)、(2,4)、(3,4) 和 (1,3)
### 本题采用了一个二位数组来记录每一对奶牛的排序（1，3）（3，1）数量，本质上还是一个桶计数。只有当该排序对计数等于k次才表示这对奶牛是符合题意的一致对。
```c++
#include<bits/stdc++.h>
using namespace std;
int a[12][22],b[22][22];
int main(){
	int K,n,cnt=0;
	cin>>K>>n;
	for(int i=0;i<K;i++){
		for(int j=0;j<n;j++){
		
		cin>>a[i][j];
		a[i][j]--;}
	}
	for(int i=0;i<K;i++){
		for(int j=0;j<n;j++){
			for(int k=j+1;k<n;k++){
				b[a[i][j]][a[i][k]]++;
			}
		}
	}
	for(int i=0;i<n;i++){
		for(int j=0;j<n;j++)
		if(b[i][j]==K) cnt++;
	}
	cout<<cnt;
return 0;
}
```

---

* Link: https://github.com/justonehe/Algorithm/issues/9
* Labels: `usaco`, `暴力`, `桶计数`
* Creation Date: 2023-12-23T12:48:46Z
