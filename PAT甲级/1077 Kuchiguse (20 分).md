# 1077 Kuchiguse (20 分)

The Japanese language is notorious for its sentence ending particles. Personal preference of such particles can be considered as a reflection of the speaker's personality. Such a preference is called "Kuchiguse" and is often exaggerated artistically in Anime and Manga. For example, the artificial sentence ending particle "nyan~" is often used as a stereotype for characters with a cat-like personality:

- Itai nyan~ (It hurts, nyan~)
- Ninjin wa iyada nyan~ (I hate carrots, nyan~)

Now given a few lines spoken by the same character, can you find her Kuchiguse?

### Input Specification:

Each input file contains one test case. For each case, the first line is an integer *N* (2≤*N*≤100). Following are *N* file lines of 0~256 (inclusive) characters in length, each representing a character's spoken line. The spoken lines are case sensitive.

### Output Specification:

For each test case, print in one line the kuchiguse of the character, i.e., the longest common suffix of all *N* lines. If there is no such suffix, write `nai`.

### Sample Input 1:

```in
3
Itai nyan~
Ninjin wa iyadanyan~
uhhh nyan~结尾无空行
```

### Sample Output 1:

```out
nyan~



结尾无空行
```

### Sample Input 2:

```in
3
Itai!
Ninjinnwaiyada T_T
T_T结尾无空行
```

### Sample Output 2:

```out
nai



结尾无空行
```

```
#include<iostream>
#include<string>
#include<algorithm>
using namespace std;
int main(){
    int n,ans=0;
    cin>>n;
    int len = 256;
    string str[110];
    cin.get();
    for(int i=0;i<n;i++){
        getline(cin,str[i]);
        if(str[i].size()<len) len = str[i].size();
        reverse(str[i].begin(),str[i].end());
    }
    for(int i=0;i<len;i++){
        char c = str[0][i];
        int sign=1;
        for(int j=0;j<n;j++){
            if(c!=str[j][i]){
                sign=0;
                break;
            }
        }
        if(sign) ans++;
        else  break;
    }
    if(ans==0){
        printf("nai");
    }else{
        for(int i=ans-1;i>=0;i--){
            printf("%c",str[0][i]);
        }
    }
    return 0;
}
```

