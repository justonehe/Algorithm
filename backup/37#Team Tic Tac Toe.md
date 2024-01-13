# Team Tic Tac Toe

http://www.usaco.org/index.php?page=viewproblem2&cpid=831&lang=zh
Farmer John有26头奶牛，恰好她们名字都以不同的字母开头，所以Farmer John用每头奶牛的名字的首字母来指代她——一个A…Z之间的字母。
这些奶牛最近沉迷于井字游戏，但是由于她们并不满足只有两头奶牛可以一起玩，她们改编了这个游戏，可以让许多奶牛可以一块儿玩！就像常规的井字游戏一样，这个游戏是在一块3×3的棋盘上进行的，只是与仅用X和O不同，每个格子用一个A…Z之间的字母标记，表示占有这个格子的奶牛名字的首字母。

以下是一个棋盘的例子：

COW
XXO
ABC
这些奶牛会在她们迷惑于如何判断胜负之前就占满这九个格子。显然，就像常规的井字游戏一样，如果任何一头奶牛占有了一整行、一整列，或是一整条对角线，那么这头奶牛就获胜了。然而，由于奶牛认为多牛游戏中这并不容易出现，所以她们决定允许奶牛组成两牛一队，如果某一行、一列，或是一条对角线仅包含一队的两头奶牛的字母，并且同时包含了这两头奶牛（不仅仅是一头）的字母，那么这一队就获胜。

请帮助奶牛们判断有多少头奶牛或是两头奶牛组成的队伍可以获胜。注意棋盘上的同一个格子可能在不同奶牛或队伍的获胜中均被用到。
```c++
#include<bits/stdc++.h>
using namespace std;
char a[3][3];
int checkletter(char ch){
	        if(a[0][0]==ch&&a[1][1]==ch&&a[2][2]==ch){
            return 1;
        }
        if(a[0][2]==ch&&a[1][1]==ch&&a[2][0]==ch){
            return 1;
        }
            for(int i=0;i<3;i++){
        if(a[i][0]==a[i][1]&&a[i][1]==a[i][2]&&a[i][0]==ch){
            return 1;
        }
        if(a[0][i]==a[1][i]&&a[1][i]==a[2][i]&&a[0][i]==ch){
            return 1;
        }
    }
    return 0;
}
bool check3(char ch1,char ch2, char a, char b,char c){
	if(a!=ch1&&a!=ch2) return false;
	if(b!=ch1&&b!=ch2) return false;
	if(c!=ch1&&c!=ch2) return false;
	if(a!=ch1&&b!=ch1&&c!=ch1) return false;
	if(a!=ch2&&b!=ch2&&c!=ch2) return false;
	return true;
}
int team(char ch1, char ch2){
	if(check3(ch1,ch2,a[0][0],a[1][1],a[2][2])) return 1;
	if(check3(ch1,ch2,a[0][2],a[1][1],a[2][0])) return 1;
	for(int i=0;i<3;i++){
		if(check3(ch1,ch2,a[0][i],a[1][i],a[2][i])) return 1;
		if(check3(ch1,ch2,a[i][0],a[i][1],a[i][2])) return 1;
	}
	return 0;
}
int main(){
    //读入一个3*3的字符矩阵
    for(int i=0;i<3;i++){
        for(int j=0;j<3;j++){
            cin>>a[i][j];
        }
    }
    //判断这个矩阵每一行每一列是否有3个相同字符，如果有，计算字符个数
    int ans=0;
    for(char ch='A';ch<='Z';ch++){
    	ans+=checkletter(ch);
	}

//计算两条对角线上的字符

    
    int ans2=0;
	for(char ch1='A';ch1<='Z';ch1++){
		for(char ch2=ch1+1;ch2<='Z';ch2++){
			ans2+=team(ch1,ch2);
		}
	}

    cout<<ans<<endl;
    cout<<ans2<<endl;
    return 0;
}
```

---

* Link: https://github.com/justonehe/Algorithm/issues/37
* Labels: `usaco`, `暴力`
* Creation Date: 2024-01-13T10:17:03Z
