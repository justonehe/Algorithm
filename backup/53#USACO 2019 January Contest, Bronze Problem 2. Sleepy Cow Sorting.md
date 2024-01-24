# USACO 2019 January Contest, Bronze Problem 2. Sleepy Cow Sorting

http://www.usaco.org/index.php?page=viewproblem2&cpid=892&lang=zh
Farmer John正在尝试将他的N
头奶牛（1≤N≤100），方便起见编号为1…N，在她们前往牧草地吃早餐之前排好顺序。
当前，这些奶牛以p1,p2,p3,…,pN的顺序排成一行，Farmer John站在奶牛p1前面。他想要重新排列这些奶牛，使得她们的顺序变为1,2,3,…,N，奶牛1在Farmer John旁边。

今天奶牛们有些困倦，所以任何时刻都只有直接面向Farmer John的奶牛会注意听Farmer John的指令。每一次他可以命令这头奶牛沿着队伍向后移动k步，k可以是范围1…N−1中的任意数。她经过的k头奶牛会向前移动，腾出空间使得她能够插入到队伍中这些奶牛之后的位置。

例如，假设N=4，奶牛们开始时是这样的顺序：

 FJ: 4, 3, 2, 1 
唯一注意FJ指令的奶牛是奶牛4。当他命令她向队伍后移动2步之后，队伍的顺序会变成：

 FJ: 3, 2, 4, 1 
现在唯一注意FJ指令的奶牛是奶牛3，所以第二次他可以给奶牛3下命令，如此进行直到奶牛们排好了顺序。
```
#include<bits/stdc++.h>
using namespace std;
int main(){
	int n;
	cin>>n;
	int a[110];
	for(int i=0;i<n;i++) cin>>a[i];
	int x=1;
	for(int i=n-2;i>-1&&a[i]<a[i+1];i--) x++;
	
	
	cout<<n-x; 

return 0;
}
```

---

* Link: https://github.com/justonehe/Algorithm/issues/53
* Labels: `usaco`, `排序`
* Creation Date: 2024-01-24T06:07:48Z
