# Creating Strings 创建字符串

https://cses.fi/problemset/task/1622
Given a string, your task is to generate all different strings that can be created using its characters.
Input
The only input line has a string of length n. Each character is between a–z.
Output
First print an integer k: the number of strings. Then print k lines: the strings in alphabetical order.
Constraints
##### 解释
在 C++ 中，生成全排列通常可以使用标准库中的 next_permutation 函数。这个函数属于 <algorithm> 头文件，能够将容器中的元素重新排列为下一个字典序更大的排列。如果当前排列已经是最大的排列，函数返回 false，否则返回 true。
在生成全排列之前，需要对字符串进行排序，否则将会从当前排序开始按照字典序生成，即会丢掉当前排序前面的排序组合。
```C++
#include<bits/stdc++.h>
using namespace std;
int main(){
    string s;
    vector <string> v;
    cin>>s;
    sort(s.begin(),s.end());
    int cnt=0;
    //use next_permutation to generate all permutations of the string s, add to vector v
    do{
        v.push_back(s);
        cnt++;
    }while(next_permutation(s.begin(),s.end()));
    cout<<cnt<<endl;
    for(int i=0;i<v.size();i++){
        cout<<v[i]<<endl;
    }
    
    return 0;
}
```

---

* Link: https://github.com/justonehe/Algorithm/issues/23
* Labels: `usaco`, `全排列`
* Creation Date: 2024-01-05T02:53:19Z
