# 1065 A+B and C (64bit) (20 分)

Given three integers *A*, *B* and *C* in (−263,263), you are supposed to tell whether *A*+*B*>*C*.

### Input Specification:

The first line of the input gives the positive number of test cases, *T* (≤10). Then *T* test cases follow, each consists of a single line containing three integers *A*, *B* and *C*, separated by single spaces.

### Output Specification:

For each test case, output in one line `Case #X: true` if *A*+*B*>*C*, or `Case #X: false` otherwise, where *X* is the case number (starting from 1).

### Sample Input:

```in
3
1 2 3
2 3 4
9223372036854775807 -9223372036854775808 0结尾无空行
```

### Sample Output:

```out
Case #1: false
Case #2: true
Case #3: false结尾无空行
```

```
#include<iostream>
using namespace std;
int main(){
    int cnt;
    cin>>cnt;
    for(int i=1;i<=cnt;i++){
        long long a,b,c;
        scanf("%lld%lld%lld",&a,&b,&c);
        bool flag;
        long long res=a+b;
        if(a > 0 && b > 0 && res < 0)
            flag = true;
        else if(a < 0 && b < 0 && res >= 0){
            flag = false;
        }else if(res>c){
            flag = true;
        }else
            flag = false;
        if(flag == true){
            printf("Case #%d: true\n",i);
        }else{
            printf("Case #%d: false\n",i);
        }
    }
    return 0;
}
```

```