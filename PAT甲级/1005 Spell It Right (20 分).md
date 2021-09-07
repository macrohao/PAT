# 1005 Spell It Right (20 分)

Given a non-negative integer *N*, your task is to compute the sum of all the digits of *N*, and output every digit of the sum in English.

### Input Specification:

Each input file contains one test case. Each case occupies one line which contains an *N* (≤10100).

### Output Specification:

For each test case, output in one line the digits of the sum in English words. There must be one space between two consecutive words, but no extra space at the end of a line.

### Sample Input:

```in
12345



结尾无空行
```

### Sample Output:

```out
one five



结尾无空行
```

```
/*
思路：
分解求和，逆序到数组内，再引用数组输出
*/

#include<cstring>
#include<cstdio>
char num[10][10]={"zero","one","two","three","four","five","six","seven","eight","nine"};
int digit[10];
char s[111];
int main(){
    scanf("%s",s);
    int len=strlen(s),sum=0,numLen=0;
    for(int i=0;i<len;i++){
        sum += (s[i]-'0');
    }
    if(sum==0) printf("%s",num[0]);
    else 
    {
        while(sum){
            digit[numLen++] = sum%10;
            sum /= 10;
        }
        for(int i=numLen-1;i>=0;i--){
            printf("%s",num[digit[i]]);
            if(i!=0) printf(" ");
        }   
    }
    
    
    
    return 0;
}
```

