# USACO 2019 January Contest, Bronze Problem 3. Guess the Animal

http://www.usaco.org/index.php?page=viewproblem2&cpid=893
奶牛Bessie和她的朋友Elsie厌倦了她们的坚果壳游戏，她们想要玩另一个叫做“猜动物”的常见游戏。
游戏开始时，Bessie会想好一种动物（大部分时候，她想的都是奶牛，这使得游戏相当无聊，但是偶尔Bessie也能有些新意，想一些别的）。随后Elsie会通过问一些问题来猜出Bessie选择的动物。每个问题都是询问这种动物是否具有某个特定的特征，Bessie对于每个问题回答“是”或“不是”。例如：

Elsie：“这种动物是能飞的吗？”
Bessie：“不是。”
Elsie：“这种动物是吃草的吗？”
Bessie：“是。”
Elsie：“这种动物是能产奶的吗？”
Bessie：“是。”
Elsie：“这种动物是会哞哞叫的吗？”
Bessie：“是。”
Elsie：“这样的话我想这种动物是奶牛。”
Bessie：“猜对了！”
如果我们将所有具备符合Elsie到目前为止所提出的问题的特征的动物的集合称为“可行集”，那么Elsie会持续进行提问直到可行集仅包含一种动物，然后她会把这种动物作为她的答案。对于每个问题，Elsie会选择某种动物的一个特征进行询问（即使这个特征并不能进一步帮助她缩小可行集）。她不会关于同一个特征询问两次。

给定Bessie和Elsie知道的所有动物以及它们的特征，请求出Elsie在猜出正确的动物之前能够得到的“是”的回答的最大数量。

输入格式（文件名：guess.in）：
输入的第一行包含动物的数量N（2≤N≤100）。以下N行每行描述了一种动物。每一行开始是这种动物的名称，接下来是一个整数K（1≤K≤100），接下来是这种动物的K个特征。动物的名称和特征是至多20个小写字母（a..z）组成的字符串。没有两种动物具有完全相同的特征。
输出格式（文件名：guess.out）：
输出游戏结束之前Elsie可能得到的“是”的回答的最大数量。
输入样例：
4
bird 2 flies eatsworms
cow 4 eatsgrass isawesome makesmilk goesmoo
sheep 1 eatsgrass
goat 2 makesmilk eatsgrass
输出样例：
3
在这个例子中，Elsie可能在对话中获得3个“是”的回答（题目中的例子），并且不可能进行包含超过3个“是”的回答的对话。
```c++
#include<bits/stdc++.h>
using namespace std;
int main(){
	int N;
	cin>>N;
	vector <vector<string>> feature(N);
	for(int i=0;i<N;++i){
		string name;
		cin>>name;
		
		int k;
		cin>>k;
		for(int j=0;j<k;++j){
			string f;
			cin>>f;
			
			feature[i].push_back(f);
		
		}
	
	}
	int cnt=0;
	for(int i=0;i<N;++i){
		for(int j=i+1;j<N;++j){
			int common=0;
			for(const auto &f1:feature[i]){
				for(const auto &f2:feature[j]){
					if(f1==f2){
						common++;
						
						break;
					}
				}
			}
			cnt=max(cnt,common);
		}
	}
	cout<<cnt+1;
return 0;
}
```

---

* Link: https://github.com/justonehe/Algorithm/issues/11
* Labels: `usaco`, `暴力`, `vector`
* Creation Date: 2023-12-25T13:54:20Z
