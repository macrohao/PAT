# 1031 Hello World for U (20 分)

Given any string of *N* (≥5) characters, you are asked to form the characters into the shape of `U`. For example, `helloworld` can be printed as:

```
h  d
e  l
l  r
lowo
```

That is, the characters must be printed in the original order, starting top-down from the left vertical line with *n*1 characters, then left to right along the bottom line with *n*2 characters, and finally bottom-up along the vertical line with *n*3 characters. And more, we would like `U` to be as squared as possible -- that is, it must be satisfied that *n*1=*n*3=*ma**x* { *k* | *k*≤*n*2 for all 3≤*n*2≤*N* } with *n*1+*n*2+*n*3−2=*N*.

### Input Specification:

Each input file contains one test case. Each case contains one string with no less than 5 and no more than 80 characters in a line. The string contains no white space.

### Output Specification:

For each test case, print the input string in the shape of U as specified in the description.

### Sample Input:

```in
helloworld!



结尾无空行
```

### Sample Output:

```out
h   !
e   d
l   l
lowor结尾无空行
```

```
#include<iostream>
using namespace std;
#include<string>
int main(){
    string str;
    cin>>str;
    int n1=(str.length()+2)/3;
    int n2=str.length()+2-n1-n1;
    for(int i=1;i<=n1-1;i++){
        printf("%c",str[i-1]);
        for(int j=1;j<=n2-2;j++){
            printf(" ");
        }
        printf("%c",str[str.length()-i]);
        printf("\n");
    }
    for(int k=n1-1;k<=str.length()-n1;k++){
        printf("%c",str[k]);
    }
}
```

