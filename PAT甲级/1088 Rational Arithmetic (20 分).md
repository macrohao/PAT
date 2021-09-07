# 1088 Rational Arithmetic (20 分)

For two rational numbers, your task is to implement the basic arithmetics, that is, to calculate their sum, difference, product and quotient.

### Input Specification:

Each input file contains one test case, which gives in one line the two rational numbers in the format `a1/b1 a2/b2`. The numerators and the denominators are all in the range of long int. If there is a negative sign, it must appear only in front of the numerator. The denominators are guaranteed to be non-zero numbers.

### Output Specification:

For each test case, print in 4 lines the sum, difference, product and quotient of the two rational numbers, respectively. The format of each line is `number1 operator number2 = result`. Notice that all the rational numbers must be in their simplest form `k a/b`, where `k` is the integer part, and `a/b` is the simplest fraction part. If the number is negative, it must be included in a pair of parentheses. If the denominator in the division is zero, output `Inf` as the result. It is guaranteed that all the output integers are in the range of **long int**.

### Sample Input 1:

```in
2/3 -4/2



结尾无空行
```

### Sample Output 1:

```out
2/3 + (-2) = (-1 1/3)
2/3 - (-2) = 2 2/3
2/3 * (-2) = (-1 1/3)
2/3 / (-2) = (-1/3)结尾无空行
```

### Sample Input 2:

```in
5/3 0/6



结尾无空行
```

### Sample Output 2:

```out
1 2/3 + 0 = 1 2/3
1 2/3 - 0 = 1 2/3
1 2/3 * 0 = 0
1 2/3 / 0 = Inf结尾无空行
```

```
#include<iostream>
#include<algorithm>
using namespace std;
typedef long long ll;

ll gcd(ll a,ll b){
    return b==0?a:gcd(b,a%b);
    
}

struct fraction{
    ll up,down;
};

fraction reduction(fraction result){
    if(result.down<0){
        result.up = -result.up;
        result.down = -result.down;
    }
    if(result.up==0){
        result.down = 1;
    } else{
        int d = gcd (abs(result.up),abs(result.down));
        result.up = result.up/d;
        result.down = result.down/d;
    }
    return result;
}

fraction add(fraction a,fraction b){
    fraction result;
    result.up = a.up * b.down + a.down * b.up;
    result.down = a.down * b.down;
    
    return reduction(result);
}

fraction minus1(fraction a,fraction b){
    fraction result;
    result.up = a.up * b.down - a.down * b.up;
    result.down = a.down * b.down;

    return reduction(result);
}

fraction divid(fraction a,fraction b){
    fraction result;
    result.up = a.up * b.down; 
    result.down = a.down * b.up;
    
    return reduction(result);
}

fraction multi(fraction a,fraction b){
    fraction result;
    result.up = a.up * b.up; 
    result.down = a.down * b.down;

    return reduction(result);
}

void showresult(fraction a){
    a = reduction(a);
    if(a.up<0) printf("(");
    if(a.down==1) printf("%lld",a.up);
    else if(abs(a.up)>a.down){
            printf("%lld %lld/%lld",a.up/a.down,abs(a.up)%a.down,a.down);
    }else  printf("%lld/%lld",a.up,a.down);
   if(a.up<0) printf(")");
}

int main(){
    fraction a,b,ans1,ans2,ans3,ans4;
   scanf("%lld/%lld",&a.up,&a.down);
   scanf("%lld/%lld",&b.up,&b.down);
    reduction(a);
    reduction(b);
    
    ans1 = add(a,b);
    ans2 = minus1(a,b);
    ans3 = multi(a,b);
    ans4 = divid(a,b);
    showresult(a); printf(" + ");showresult(b);printf(" = ");showresult(ans1);printf("\n");
    showresult(a); printf(" - ");showresult(b);printf(" = ");showresult(ans2);printf("\n");
    showresult(a); printf(" * ");showresult(b);printf(" = ");showresult(ans3);printf("\n");
    showresult(a); printf(" / ");showresult(b);printf(" = ");if(reduction(ans4).up==0) printf("Inf");else showresult(ans4);printf("\n");
}
```

