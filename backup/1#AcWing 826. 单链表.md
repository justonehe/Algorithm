# AcWing 826. 单链表

实现一个单链表，链表初始为空，支持三种操作：

向链表头插入一个数；
删除第 k个插入的数后面的数；
在第 k个插入的数后插入一个数。
现在要对该链表进行 M次操作，进行完所有操作后，从头到尾输出整个链表。

注意:题目中第 k个插入的数并不是指当前链表的第 k个数。例如操作过程中一共插入了 n个数，则按照插入的时间顺序，这 n个数依次为：第 1个插入的数，第 2个插入的数，…第 n个插入的数。

输入格式
第一行包含整数 M，表示操作次数。

接下来 M行，每行包含一个操作命令，操作命令可能为以下几种：

H x，表示向链表头插入一个数 x。
D k，表示删除第 k个插入的数后面的数（当 k为 0时，表示删除头结点）。
I k x，表示在第 k个插入的数后面插入一个数 x（此操作中 k均大于 0）。
输出格式
共一行，将整个链表从头到尾输出。

数据范围
1≤M≤100000

所有操作保证合法。

输入样例：
10
H 9
I 1 1
D 1
D 0
H 6
I 3 6
I 4 5
I 4 5
I 3 4
D 6
输出样例：
6 4 6 5

```C++
#include<bits/stdc++.h>

using namespace std;
const int N=100010;
int head,e[N],ne[N],idx;
void init(){
	head=-1;
	idx=0;
}
void add_to_head(int x){
	e[idx]=x;
	ne[idx]=head;
	head=idx;
	idx++;
}
void add(int k, int x){
	e[idx]=x;
	ne[idx]=ne[k];
	ne[k]=idx;
	idx++;
}
void remove(int k){
	ne[k]=ne[ne[k]];
}
int main(){
	int m;
	cin>>m;
	init();
	while(m--){
		int k,x;
		char op;
		cin>>op;
		if(op=='H'){
			cin>>x;
			add_to_head(x);
		}
		else if(op=='D'){
			cin>>k;
			if(!k) head=ne[head];
			remove(k-1);
		}
		else if(op=='I'){
			cin>>k>>x;
			add(k-1,x);
		}
	}
	for (int i=head;i!=-1;i=ne[i]) cout<<e[i]<<' ';
	cout<<endl;
	
return 0;
}

```

---

* Link: https://github.com/justonehe/Algorithm/issues/1
* Labels: `单链表`, `模板`
* Creation Date: 2023-12-16T02:39:59Z
