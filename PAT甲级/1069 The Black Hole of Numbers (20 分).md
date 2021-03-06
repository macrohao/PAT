# 1069 The Black Hole of Numbers (20 分)

For any 4-digit integer except the ones with all the digits being the same, if we sort the digits in non-increasing order first, and then in non-decreasing order, a new number can be obtained by taking the second number from the first one. Repeat in this manner we will soon end up at the number `6174` -- the **black hole** of 4-digit numbers. This number is named Kaprekar Constant.

For example, start from `6767`, we'll get:

```
7766 - 6677 = 1089
9810 - 0189 = 9621
9621 - 1269 = 8352
8532 - 2358 = 6174
7641 - 1467 = 6174
... ...
```

Given any 4-digit number, you are supposed to illustrate the way it gets into the black hole.

### Input Specification:

Each input file contains one test case which gives a positive integer *N* in the range (0,104).

### Output Specification:

If all the 4 digits of *N* are the same, print in one line the equation `N - N = 0000`. Else print each step of calculation in a line until `6174` comes out as the difference. All the numbers must be printed as 4-digit numbers.

### Sample Input 1:

```in
6767



结尾无空行
```

### Sample Output 1:

```out
7766 - 6677 = 1089
9810 - 0189 = 9621
9621 - 1269 = 8352
8532 - 2358 = 6174结尾无空行
```

### Sample Input 2:

```in
2222



结尾无空行
```

### Sample Output 2:

```out
2222 - 2222 = 0000



结尾无空行
```

```
#include<iostream>
#include<algorithm>
using namespace std;
bool cmp(int a,int b){
    return a>b;
}
int to_number(int a[]){
    int sum=0;
    for(int i =0;i<4;i++){
        sum = sum*10 +a[i];
    }
    return sum;
}
void to_array(int a[],int n){
    for(int i=0;i<4;i++){
        a[i]=n%10;
        n = n/10;
    }
}
int main(){
    int n,min,max;
    cin>>n;
    while(1){
        int a[4];
        to_array(a,n);
        sort(a,a+4);
        min = to_number(a);
        sort(a,a+4,cmp);
        max=to_number(a);
        n=max-min;
        printf("%04d - %04d = %04d\n",max,min,max-min);
        if(n==0||n==6174)
            break;
           
    }
    
}
```

