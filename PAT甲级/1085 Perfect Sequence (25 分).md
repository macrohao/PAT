# 1085 Perfect Sequence (25 分)

Given a sequence of positive integers and another positive integer *p*. The sequence is said to be a **perfect sequence** if *M*≤*m*×*p* where *M* and *m* are the maximum and minimum numbers in the sequence, respectively.

Now given a sequence and a parameter *p*, you are supposed to find from the sequence as many numbers as possible to form a perfect subsequence.

### Input Specification:

Each input file contains one test case. For each case, the first line contains two positive integers *N* and *p*, where *N* (≤105) is the number of integers in the sequence, and *p* (≤109) is the parameter. In the second line there are *N* positive integers, each is no greater than 109.

### Output Specification:

For each test case, print in one line the maximum number of integers that can be chosen to form a perfect subsequence.

### Sample Input:

```in
10 8
2 3 20 4 5 1 6 7 8 9结尾无空行
```

### Sample Output:

```out
8



结尾无空行
```

```
#include<iostream>
#include<algorithm>
using namespace std;
int a[100010];
int n;
long long p;
int twodiv(int i,long long x){
    if(a[n-1]< x) return n;
    int l = i+1;
    int r = n-1;
    while(l<r){
        int mid = (r+l)/2;
        if(a[mid]>x) r = mid ;
        else l = mid +1;
    }
    return l;
}
int main(){
   
    scanf("%d%lld",&n,&p);
    for(int i=0;i<n;i++){
        scanf("%d",&a[i]);
    }
   sort(a,a+n);
    int ans =0;
    for(int i=0;i<n;i++){
        int j = twodiv(i,(long long)p*a[i]);
        ans = max(ans,j - i);
    }
    printf("%d\n",ans);
    
    return 0;
}
```

