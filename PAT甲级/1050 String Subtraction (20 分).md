# 1050 String Subtraction (20 分)

Given two strings *S*1 and *S*2, *S*=*S*1−*S*2 is defined to be the remaining string after taking all the characters in *S*2 from *S*1. Your task is simply to calculate *S*1−*S*2 for any given strings. However, it might not be that simple to do it **fast**.

### Input Specification:

Each input file contains one test case. Each case consists of two lines which gives *S*1 and *S*2, respectively. The string lengths of both strings are no more than 104. It is guaranteed that all the characters are visible ASCII codes and white space, and a new line character signals the end of a string.

### Output Specification:

For each test case, print *S*1−*S*2 in one line.

### Sample Input:

```in
They are students.
aeiou结尾无空行
```

### Sample Output:

```out
Thy r stdnts.



结尾无空行
```

```
#include<iostream>
#include<string>
using namespace std;
int main(){
    string s1;
    string s2;
    getline(cin,s1);
    getline(cin,s2);
    int len1 = s1.length();
    int len2 = s2.length();
    for(int i=0;i<len1;i++){
        bool flag = true;
        for(int j=0;j<len2;j++){
            if(s1[i]==s2[j])
                flag = false;
        }
        if(flag) printf("%c",s1[i]);
        else continue;
    }
    
    return 0;
}
```

