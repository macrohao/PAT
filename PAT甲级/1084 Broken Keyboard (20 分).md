# 1084 Broken Keyboard (20 分)

On a broken keyboard, some of the keys are worn out. So when you type some sentences, the characters corresponding to those keys will not appear on screen.

Now given a string that you are supposed to type, and the string that you actually type out, please list those keys which are for sure worn out.

### Input Specification:

Each input file contains one test case. For each case, the 1st line contains the original string, and the 2nd line contains the typed-out string. Each string contains no more than 80 characters which are either English letters [A-Z] (case insensitive), digital numbers [0-9], or `_` (representing the space). It is guaranteed that both strings are non-empty.

### Output Specification:

For each test case, print in one line the keys that are worn out, in the order of being detected. The English letters must be capitalized. Each worn out key must be printed once only. It is guaranteed that there is at least one worn out key.

### Sample Input:

```in
7_This_is_a_test
_hs_s_a_es结尾无空行
```

### Sample Output:

```out
7TI



结尾无空行
```



```
#include<iostream>
#include<string.h>
#include<algorithm>
using namespace std;
char str1[90],str2[90];
bool hashtable[128] = {false};
int main(){
    scanf("%s %s", str1, str2);
    int len1 = strlen(str1);
    int len2 = strlen(str2);
   for(int i=0;i<len1;i++){
       if(str1[i]>='a'&&str1[i]<='z')
           str1[i] -= 32;
   }
 for(int i=0;i<len2;i++){
   if(str2[i]>='a'&&str2[i]<='z')
       str2[i] -= 32;
   }
    
    for(int i=0;i<len1;i++){
        bool flag = false;
        for(int j=0;j<len2;j++){
            if(str1[i] == str2[j]){
                flag = true;
                break;
            }
        }
        char c = str1[i];
        if(flag == false&&hashtable[c]!=true){
            printf("%c",c);
            hashtable[c] = true;
        }
            
    }
    return 0;
}
```

