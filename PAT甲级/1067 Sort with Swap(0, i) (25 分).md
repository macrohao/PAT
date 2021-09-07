# 1067 Sort with Swap(0, i) (25 分)

Given any permutation of the numbers {0, 1, 2,..., *N*−1}, it is easy to sort them in increasing order. But what if `Swap(0, *)` is the ONLY operation that is allowed to use? For example, to sort {4, 0, 2, 1, 3} we may apply the swap operations in the following way:

```
Swap(0, 1) => {4, 1, 2, 0, 3}
Swap(0, 3) => {4, 1, 2, 3, 0}
Swap(0, 4) => {0, 1, 2, 3, 4}
```

Now you are asked to find the minimum number of swaps need to sort the given permutation of the first *N* nonnegative integers.

### Input Specification:

Each input file contains one test case, which gives a positive *N* (≤105) followed by a permutation sequence of {0, 1, ..., *N*−1}. All the numbers in a line are separated by a space.

### Output Specification:

For each case, simply print in a line the minimum number of swaps need to sort the given permutation.

### Sample Input:

```in
10
3 5 7 2 6 4 9 0 8 1结尾无空行
```

### Sample Output:

```out
9



结尾无空行
```

```
#include<iostream>
#include<algorithm>
using namespace std;
int pos[100010];
int main(){
    int n,num,ans=0;
    scanf("%d",&n);
    int left = 0;
    for(int i=0;i<n;i++){
        scanf("%d",&num);
        pos[num]=i;
        if(num!=i&num!=0) left++;
    }
    int k=1;
    while(left>0){
        if(pos[0]==0){
            while(k<n){
                if(pos[k]!=k){
                    swap(pos[0],pos[k]);
                    ans++;
                    break;
                }
                k++;
            }
        }
        while(pos[0]!=0){
            swap(pos[0],pos[pos[0]]);
            ans++;
            left--;
            break;
        }
    }
    printf("%d",ans);
    return 0;
}
```

