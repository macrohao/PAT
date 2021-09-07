# 1081 Rational Sum (20 分)

Given *N* rational numbers in the form `numerator/denominator`, you are supposed to calculate their sum.

### Input Specification:

Each input file contains one test case. Each case starts with a positive integer *N* (≤100), followed in the next line *N* rational numbers `a1/b1 a2/b2 ...` where all the numerators and denominators are in the range of **long int**. If there is a negative number, then the sign must appear in front of the numerator.

### Output Specification:

For each test case, output the sum in the simplest form `integer numerator/denominator` where `integer` is the integer part of the sum, `numerator` < `denominator`, and the numerator and the denominator have no common factor. You must output only the fractional part if the integer part is 0.

### Sample Input 1:

```in
5
2/5 4/15 1/30 -2/60 8/3结尾无空行
```

### Sample Output 1:

```out
3 1/3



结尾无空行
```

### Sample Input 2:

```in
2
4/3 2/3结尾无空行
```

### Sample Output 2:

```out
2



结尾无空行
```

### Sample Input 3:

```in
3
1/3 -1/6 1/8结尾无空行
```

### Sample Output 3:

```out
7/24



结尾无空行
```

```
#include<iostream>
#include<algorithm>
#include<stdio.h>
using namespace std;
typedef long long ll;
ll gcd(ll a,ll b){
    return b==0 ? a : gcd(b,a%b);
}
struct fraction{
   ll up,down;
} ;


fraction reduction (fraction a){
    if(a.down<0){
        a.up = -a.up;
        a.down = -a.down;
    }
    if(a.up==0){
        a.down=1;
    }else{
        int d = gcd(abs(a.up),abs(a.down));
        a.up = a.up/d;
        a.down = a.down/d;
    }
    return a;
}

fraction add(fraction a,fraction b){
    fraction temp;
    temp.up=a.up * b.down + a.down * b.up;
    temp.down = a.down * b.down;
    return reduction(temp);
}

void showresult(fraction a){
    reduction(a);
    if(a.down==1) printf("%lld\n",a.up);
    else if(abs(a.up)>a.down)
        printf("%lld %lld/%lld\n",a.up/a.down,abs(a.up)%a.down,a.down);
    else
        printf("%lld/%lld\n",a.up,a.down);
}
int main(){
    int n;
    cin>>n;
    fraction result,temp;
    result.up=0;
    result.down=1;
    for(int i=0;i<n;i++){
        scanf("%lld/%lld",&temp.up,&temp.down);
        result = add(result,temp);
    }
    showresult(result);
    return 0;
    
}
```

