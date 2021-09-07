# 1015 Reversible Primes (20 分)

A **reversible prime** in any number system is a prime whose "reverse" in that number system is also a prime. For example in the decimal system 73 is a reversible prime because its reverse 37 is also a prime.

Now given any two positive integers *N* (<105) and *D* (1<*D*≤10), you are supposed to tell if *N* is a reversible prime with radix *D*.

### Input Specification:

The input file consists of several test cases. Each case occupies a line which contains two integers *N* and *D*. The input is finished by a negative *N*.

### Output Specification:

For each test case, print in one line `Yes` if *N* is a reversible prime with radix *D*, or `No` if not.

### Sample Input:

```in
73 10
23 2
23 10
-2结尾无空行
```

```
#include<iostream>
#include<algorithm>
using namespace std;
bool isprime(int m){
    if(m<=1) return false;
    for(int i=2;i*i<=m;i++){
        if(m%i==0) return false;
    }
    return true;
}

int reverse(int m,int n){
    int a[100],num=0;
    while(m){
        a[num++]=m % n;
        m = m / n;
    }
    int temp=0;
    for(int i=0;i<num;i++){
        temp = temp * n + a[i];
    }
    return temp;
}
int main(){
    int m,n;
    while(scanf("%d %d",&m,&n)&&m>0){
        if(isprime(m)==false){
            printf("No\n");
            continue;
        }else{
            if(isprime(reverse(m,n))==true){
                printf("Yes\n");
            }else{
                printf("No\n");
            }
        }
        
    }
    
    return 0;
}



```

