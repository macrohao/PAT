# 1046 Shortest Distance (20 分)

The task is really simple: given *N* exits on a highway which forms a simple cycle, you are supposed to tell the shortest distance between any pair of exits.

### Input Specification:

Each input file contains one test case. For each case, the first line contains an integer *N* (in [3,105]), followed by *N* integer distances *D*1 *D*2 ⋯ *D**N*, where *D**i* is the distance between the *i*-th and the (*i*+1)-st exits, and *D**N* is between the *N*-th and the 1st exits. All the numbers in a line are separated by a space. The second line gives a positive integer *M* (≤104), with *M* lines follow, each contains a pair of exit numbers, provided that the exits are numbered from 1 to *N*. It is guaranteed that the total round trip distance is no more than 107.

### Output Specification:

For each test case, print your results in *M* lines, each contains the shortest distance between the corresponding given pair of exits.

### Sample Input:

```in
5 1 2 4 14 9
3
1 3
2 5
4 1结尾无空行
```

### Sample Output:

```out
3
10
7结尾无空行
```

```
#include <iostream>
#include <vector>
using namespace std;
int main(){
	int n;
	scanf("%d",&n);
	vector<int> dis(n + 1);
	int sum=0,left,right,cnt;
	for(int i = 1; i <= n; i++){
		int temp;
		scanf("%d",&temp);
		sum += temp;
		dis[i] = sum;
	}
	scanf("%d",&cnt); 
	for(int i = 0; i < cnt; i++){
		scanf("%d %d", &left, &right);
		if(left > right)
			swap(left,right);
		int temp = dis[right - 1]-dis[left - 1];
		printf("%d\n",min(temp,sum - temp));
	}
	return 0;
}  
```

