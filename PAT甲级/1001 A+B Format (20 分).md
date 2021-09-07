# 1001 A+B Format (20 分)

Calculate *a*+*b* and output the sum in standard format -- that is, the digits must be separated into groups of three by commas (unless there are less than four digits).

### Input Specification:

Each input file contains one test case. Each case contains a pair of integers *a* and *b* where −106≤*a*,*b*≤106. The numbers are separated by a space.

### Output Specification:

For each test case, you should output the sum of *a* and *b* in one line. The sum must be written in the standard format.

### Sample Input:

```in
-1000000 9



结尾无空行
```

### Sample Output:

```out
-999,991



结尾无空行
```

```
#include<iostream>
using namespace std;
int main(){
    int a,b;
    scanf("%d %d",&a,&b);
    int sum=a+b;
    int answer[20],n=0;
    if(sum<0){
        printf("-");
        sum=-sum;
    }
    int len=0,num[10];
    if(sum==0) num[len++]=0;
    while(sum){
        num[len++]=sum%10;
        sum /= 10;
    }
    for(int i=len-1;i>=0;i--){
        printf("%d",num[i]);
        if(i>0&&i%3==0)
            printf(",");
    }
    return 0;
}
```

