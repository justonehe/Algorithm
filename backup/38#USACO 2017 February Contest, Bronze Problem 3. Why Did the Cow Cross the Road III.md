# USACO 2017 February Contest, Bronze Problem 3. Why Did the Cow Cross the Road III

http://www.usaco.org/index.php?page=viewproblem2&cpid=713
Farmer John, in his old age, has unfortunately become increasingly grumpy and paranoid. Forgetting the extent to which bovine diversity helped his farm truly flourish over the years, he has recently decided to build a huge fence around the farm, discouraging cows from neighboring farms from visiting, and completely prohibiting entry from a handful of neighboring farms. The cows are quite upset by this state of affairs, not only since they can no longer visit with their friends, but since it has caused them to cancel participation in the International Milking Olympiad, an event to which they look forward all year.
Neighboring cows that still have the ability to enter Farmer John's property find the process has become more arduous, as they can enter only through a single gate where each cow is subject to intense questioning, often causing the cows to queue up in a long line.

For each of the N
 cows visiting the farm, you are told the time she arrives at the gate and the duration of time required for her to answer her entry questions. Only one cow can be undergoing questioning at any given time, so if many cows arrive near the same time, they will likely need to wait in line to be processed one by one. For example, if a cow arrives at time 5 and answers questions for 7 units of time, another cow arriving at time 8 would need to wait until time 12 to start answering questions herself.

Please determine the earliest possible time by which all cows are able to enter the farm.

INPUT FORMAT (file cowqueue.in):
The first line of input contains N, a positive integer at most 100. Each of the next N lines describes one cow, giving the time it arrives and the time it requires for questioning; each of these numbers are positive integers at most 1,000,000.
OUTPUT FORMAT (file cowqueue.out):
Please determine the minimum possible time at which all the cows could have completed processing.
####题解
用ector<pair<int, int>> cow(n) 来存储每头牛的到达时间和排队时长。并通过sort来重新排序，然后用贪心按顺序计算每头牛等待的时间即可。
```C++
#include<bits/stdc++.h>
using namespace std;


int n;
int main(){
	cin>>n;
	vector<pair<int, int>> cow(n);
	for(int i=0;i<n;i++){
		 cin>>cow[i].first>>cow[i].second;
	}
	sort(cow.begin(),cow.end());
	int time=0;
	for(int i=0;i<n;i++){
		cow[i].first=max(cow[i].first,time);
		time=cow[i].first+cow[i].second;
	}
cout<<time;
return 0;
}
```

---

* Link: https://github.com/justonehe/Algorithm/issues/38
* Labels: `usaco`, `贪心`, `排序`
* Creation Date: 2024-01-14T07:48:07Z
