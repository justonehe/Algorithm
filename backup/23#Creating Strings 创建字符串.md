# Creating Strings 创建字符串

https://cses.fi/problemset/task/1622
Given a string, your task is to generate all different strings that can be created using its characters.
Input
The only input line has a string of length n. Each character is between a–z.
Output
First print an integer k: the number of strings. Then print k lines: the strings in alphabetical order.
Constraints
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
