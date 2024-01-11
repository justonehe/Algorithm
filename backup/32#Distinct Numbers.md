# Distinct Numbers

https://cses.fi/problemset/task/1621
You are given a list of n integers, and your task is to calculate the number of distinct values in the list.
Input
The first input line has an integer n: the number of values.
The second line has n integers x_1,x_2,\dots,x_n.
Output
Print one integers: the number of distinct values.

```c++
#include<bits/stdc++.h>
using namespace std;
//You are given a list of n integers, and your task is to calculate the number of distinct values in the list.
int main()
{
    int n;
    cin>>n;
    int a[n];
    for(int i=0;i<n;i++)
    {
        cin>>a[i];
    }
    sort(a,a+n);
    int count=0;
    for(int i=0;i<n;i++)
    {
        if(a[i]!=a[i+1])
        {
            count++;
        }
    }
    cout<<count;
}
```

---

* Link: https://github.com/justonehe/Algorithm/issues/32
* Labels: `usaco`, `排序`
* Creation Date: 2024-01-11T04:40:54Z
