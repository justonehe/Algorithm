# USACO 2019 February Contest, Bronze Problem 3. Measuring Traffic

Farmer John的农场边上的高速公路最近出现了引人注目的流量上升，或者至少Farmer John看起来是这样的。为了证实这件事，他打算用一组传感器测量公路上的车流量，每个传感器被用来测量一小段路面上的车流量的数值。
不幸的是，某一天经过牛棚的时候，Farmer John被绊倒了，装有传感器的盒子掉进了一个巨大的奶缸，之后它们就不能正常工作了。比起之前可以产生一个精确的车流量读数，现在每个传感器只能输出一个可能结果的范围。例如，一个传感器可能会给出范围[7,13]
，表示在这段路面上的车流量不小于7，并且不大于13。

高速公路经过农场的这一段长N
英里，车辆仅从一个方向通过公路，从第1英里驶向第N
英里。Farmer John想要安装N
个传感器——每一个监测高速公路上1英里长的路段。在其中某些路段上，有能够使得车辆进入高速公路的上匝道；在所有这样的路段上，Farmer John会将传感器装在上匝道上，测量流入的（近似）车流量。在某些路段上有能够使得车辆离开高速公路的下匝道；在所有这样的路段上，Farmer John会将传感器装在下匝道上。每一个路段包含至多一个匝道。如果在公路的一个路段上没有上匝道或下匝道，Farmer John就将传感器装在高速公路的主路上。

给定Farmer John的N
个传感器的读数
```c++
#include<bits/stdc++.h>
using namespace std;
int main(){
	int N,l[110],r[110],a=-999999999,b=999999999;
	string s[110];
	cin>>N;
	for(int i=0;i<N;i++){
		cin>>s[i]>>l[i]>>r[i];
	}
	for(int i=N-1;i>=0;i--){
		if(s[i]=="none"){
			a=max(a,l[i]);
			b=min(b,r[i]);
			}
		if(s[i]=="off"){
			a=a+l[i];
			b=b+r[i];
		}
		if(s[i]=="on"){
			a=a-r[i];
			b=b-l[i];
			a=max(0,a);
		}

		
	}
	cout<<a<<' '<<b<<endl;

a=-999999999,b=999999999;
for(int i=0;i<N;i++){
		if(s[i]=="none"){
			a=max(a,l[i]);
			b=min(b,r[i]);
			}

		if(s[i]=="on"){
			a+=l[i];
			b+=r[i];
			
		}
		if(s[i]=="off"){
			a-=r[i];
			b-=l[i];
			a=max(0,a);
		}
		
	}
	cout<<a<<' '<<b<<endl;

return 0;
}
```

---

* Link: https://github.com/justonehe/Algorithm/issues/6
* Labels: `模板`, `usaco`
* Creation Date: 2023-12-21T02:08:47Z
