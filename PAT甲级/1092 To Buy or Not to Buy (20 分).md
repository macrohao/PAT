# 1092 To Buy or Not to Buy (20 分)

Eva would like to make a string of beads with her favorite colors so she went to a small shop to buy some beads. There were many colorful strings of beads. However the owner of the shop would only sell the strings in whole pieces. Hence Eva must check whether a string in the shop contains all the beads she needs. She now comes to you for help: if the answer is `Yes`, please tell her the number of extra beads she has to buy; or if the answer is `No`, please tell her the number of beads missing from the string.

For the sake of simplicity, let's use the characters in the ranges [0-9], [a-z], and [A-Z] to represent the colors. For example, the 3rd string in Figure 1 is the one that Eva would like to make. Then the 1st string is okay since it contains all the necessary beads with 8 extra ones; yet the 2nd one is not since there is no black bead and one less red bead.

![figbuy.jpg](https://images.ptausercontent.com/b7e2ffa6-8819-436d-ad79-a41263abe914.jpg)

Figure 1

### Input Specification:

Each input file contains one test case. Each case gives in two lines the strings of no more than 1000 beads which belong to the shop owner and Eva, respectively.

### Output Specification:

For each test case, print your answer in one line. If the answer is `Yes`, then also output the number of extra beads Eva has to buy; or if the answer is `No`, then also output the number of beads missing from the string. There must be exactly 1 space between the answer and the number.

### Sample Input 1:

```in
ppRYYGrrYBR2258
YrR8RrY结尾无空行
```

### Sample Output 1:

```out
Yes 8



结尾无空行
```

### Sample Input 2:

```in
ppRYYGrrYB225
YrR8RrY结尾无空行
```

### Sample Output 2:

```out
No 2



结尾无空行
```

```
#include<iostream>
#include<algorithm>
#include<string.h>
using namespace std;
int  hashtable[100]={0},miss=0;
int change(char c){
    int temp;
    if(c>='0'&&c<='9') temp=c-'0';
    if(c>='A'&&c<='Z') temp=c-'A'+10;
    if(c>='a'&&c<='z') temp=c-'a'+36;
    return temp;
}
int main(){
    char str1[1010],str2[1010];
    scanf("%s%s",str1,str2);
    int len1=strlen(str1);
    int len2=strlen(str2);
    for(int i=0;i<len1;i++){
        char c = str1[i];
        hashtable[change(c)]++;
    }
     for(int i=0;i<len2;i++){
        char c = str2[i];
        hashtable[change(c)]--;
         if(hashtable[change(c)]<0) miss++;
    }
    
    if(miss<=0){
        printf("Yes %d",len1-len2);
    }else{
        printf("No %d",miss);
    }
    return 0;
}
```

