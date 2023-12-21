# P3612 [USACO17JAN] Secret Cow Code S

# [USACO17JAN] Secret Cow Code S

## 题面翻译

奶牛正在试验秘密代码，并设计了一种方法来创建一个无限长的字符串作为其代码的一部分使用。

给定一个字符串，让后面的字符旋转一次（每一次正确的旋转，最后一个字符都会成为新的第一个字符）。也就是说，给定一个初始字符串，之后的每一步都会增加当前字符串的长度。

给定初始字符串和索引，请帮助奶牛计算无限字符串中位置 $N$ 的字符。

第一行输入一个字符串。该字符串包含最多 $30$ 个大写字母，数据保证 $N \leq 10^{18}$ 。

第二行输入 $N$。请注意，数据可能很大，放进一个标准的 $32$ 位整数可能不够，所以你可能要使用一个 $64$ 位的整数类型（例如，在 C/C++ 中是 `long long`）。

请输出从初始字符串生成的无限字符串中的位置的字符。第一个字符是 $N=1$.。

感谢@y\_z\_h 的翻译

### 本题数据量大，直接模拟会MLE，所以需要倒推出n对应在原始字符串中的位置


```c++
#include<bits/stdc++.h>
using namespace std;
int main(){
	string s,s1;
	char ans;
	long long n,len;
	cin>>s>>n;
	len=s.size();
	while(len<n){
		len=len*2;
	}
//	cout<<len;
//cout<<len/2<<' '<<n-len/2-1;
	while(len>s.size()){
		
		if(n==len/2+1) n=len/2;
		else if(n>len/2) n=n-len/2-1;
		len/=2;
	//	cout<<len<<' '<<n<<endl;
	}
	cout<<s[n-1];
	

return 0;
}
```

---

* Link: https://github.com/justonehe/Algorithm/issues/7
* Labels: `洛谷`, `usaco`, `递推`
* Creation Date: 2023-12-21T07:41:14Z
