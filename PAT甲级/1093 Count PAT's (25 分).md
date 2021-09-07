# 1093 Count PAT's (25 分)

The string `APPAPT` contains two `PAT`'s as substrings. The first one is formed by the 2nd, the 4th, and the 6th characters, and the second one is formed by the 3rd, the 4th, and the 6th characters.

Now given any string, you are supposed to tell the number of `PAT`'s contained in the string.

### Input Specification:

Each input file contains one test case. For each case, there is only one line giving a string of no more than 105 characters containing only `P`, `A`, or `T`.

### Output Specification:

For each test case, print in one line the number of `PAT`'s contained in the string. Since the result may be a huge number, you only have to output the result moded by 1000000007.

### Sample Input:

```in
APPAPT



结尾无空行
```

### Sample Output:

```out
2



结尾无空行
```

```
#include<iostream>
#include<string.h>
using namespace std;
char a[100010];
int leftp[100010]={0};
int rightt[100010]={0};

int main(){
    scanf("%s",a);
    int len = strlen(a);
    int ans = 0;
    int p=0,t=0;
    for(int i = 0 ;i < len ;i++){
        if(a[i]=='P') p++;
        if(a[i]=='A') leftp[i]=p;
    }
      for(int i = len-1 ;i >=0 ;i--){
        if(a[i]=='T') t++;
        if(a[i]=='A') rightt[i]=t;
    }
      for(int i = 0 ;i < len ;i++){
        if(left[i]!=0) ans =(ans+ leftp[i]*rightt[i])%1000000007;
    }
    cout<<ans;
    return 0;
}
```

