# USACO 2018 February Contest, Bronze Problem 3. Taming the Herd

http://www.usaco.org/index.php?page=viewproblem2&cpid=809
一大清早，Farmer John就被木材破裂的声音吵醒了。是这些奶牛们干的，她们又逃出牛棚了！
Farmer John已经厌烦了奶牛在清晨出逃，他觉得受够了：是时候采取强硬措施了。他在牛棚的墙上钉了一个计数器，追踪从上次出逃开始经过的天数。所以如果某一天早上发生了出逃事件，这一天的计数器就为0；如果最近的出逃是3天前，计数器读数就为3。Farmer John一丝不苟地记录了每一天计数器的读数。

年末到了，Farmer John准备做一些统计。他说，你们这些奶牛会付出代价的！然而意想不到的是，他的记录的一些条目竟然丢失了！

Farmer John确信他是在发生出逃的某一天开始记录的。请帮助他确定，在所有与残留记录条目一致的事件序列中，基于记录的时间，最少和最多可能发生的出逃次数。

输入格式（文件名：taming.in）：
输入的第一行包含一个整数N（1≤N≤100），表示从Farmer John开始对奶牛出逃计数器进行计数以来已经经过的天数。第二行包含N个空格分隔的整数。第i个整数是−1，表示第i天的记录丢失了，或者是一个非负整数ai（不超过100），表示在第i天计数器的数字是ai。

输出格式（文件名：taming.out）：
如果没有事件序列与Farmer John的残留记录以及他所确定的奶牛在第1天清晨出逃这一事实相一致，输出一个整数−1。否则，输出两个空格分隔的整数m和M，其中m为所有事件序列中出逃的最少次数，M为最多次数。
```c++
#include<bits/stdc++.h>
using namespace std;
int n;
int a[100010];
int main(){
	
	cin>>n;
	
	for(int i=0;i<n;i++) cin>>a[i];
	if(a[0]>0){
		cout<<-1;
		return 0;
	}
	a[0]=0;
	int t=-1;
	int req=0,pos=0;
	for(int i=n-1;i>=0;i--){
		if(t!=-1&&a[i]!=-1&&a[i]!=t){
			cout<<-1;
			return 0;
		}
		if(t==-1) t=a[i];
		if(a[i]==-1) a[i]=t;
		if(a[i]==0) req++;
		if(a[i]==-1) pos++;
		if(t>-1) t--;
	}
	cout<<req<<' '<<req+pos;

return 0;
}
```

---

* Link: https://github.com/justonehe/Algorithm/issues/54
* Labels: `模拟`, `usaco`
* Creation Date: 2024-01-25T06:56:30Z
