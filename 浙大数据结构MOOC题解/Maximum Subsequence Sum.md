# Maximum Subsequence Sum

Given a sequence of K integers { N1, N2, …, NK }. A continuous subsequence is defined to be { Ni, Ni+1, …, Nj } where 1≤i≤j≤K. The Maximum Subsequence is the continuous subsequence which has the largest sum of its elements. For example, given sequence { -2, 11, -4, 13, -5, -2 }, its maximum subsequence is { 11, -4, 13 } with the largest sum being 20.
Now you are supposed to find the largest sum, together with the first and the last numbers of the maximum subsequence.

### Input:

Each input file contains one test case. Each case occupies two lines. The first line contains a positive integer K (≤10000). The second line contains K numbers, separated by a space.

### Output:

For each test case, output in one line the largest sum, together with the first and the last numbers of the maximum subsequence. The numbers must be separated by one space, but there must be no extra space at the end of a line. In case that the maximum subsequence is not unique, output the one with the smallest indices i and j (as shown by the sample case). If all the K numbers are negative, then its maximum sum is defined to be 0, and you are supposed to output the first and the last numbers of the whole sequence.

### Solution：

* 最大子列和只需要用累加的子列和`int sum = 0`去和最大子列和`int maxsum = 0`比较大小，如果`sum`大就更新子列和，如果`sum < 0`就重新计数。
* 最大子列和的所在子列第一个数和最后一个数记为`first`和`last`。
* 最初`first`和`last`都应该记为数组第一个数
* 随着累加，当`sum < 0`时，`first`和`last`应更新为当前所累加的数字的21下一个数`a[i + 1]`,当`maxsum < sum`时，应更新`last`为当前所累加的数字`a[i]`

### Answer:

```

#include<stdio.h>
int a[100010] = {0};
int main(){
    int n;
    scanf("%d",&n);
    
    int sum = 0,maxsum = 0;
    int first =a[0],last = a[0]; 
    
    int i = 0;
    for(i = 0;i < n; i++){
    	scanf("%d",&a[i]);
	}
	
    for(i = 0;i < n; i++){
        sum += a[i];
        if(maxsum < sum){
            maxsum = sum;
            last = a[i];
        }else if(sum < 0){
           sum = 0; 
           first = a[i+1];
           last = a[i+1];
        }
    }
    if(maxsum == 0){
    	printf("%d %d %d",maxsum,a[0],a[n-1]);
	}else{
		printf("%d %d %d",maxsum,first,last);
	}
    
    return 0;
}
```

