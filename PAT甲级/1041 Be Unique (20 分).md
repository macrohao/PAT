# 1041 Be Unique (20 分)

Being unique is so important to people on Mars that even their lottery is designed in a unique way. The rule of winning is simple: one bets on a number chosen from [1,104]. The first one who bets on a unique number wins. For example, if there are 7 people betting on { 5 31 5 88 67 88 17 }, then the second one who bets on 31 wins.

### Input Specification:

Each input file contains one test case. Each case contains a line which begins with a positive integer *N* (≤105) and then followed by *N* bets. The numbers are separated by a space.

### Output Specification:

For each test case, print the winning number in a line. If there is no winner, print `None` instead.

### Sample Input 1:

```in
7 5 31 5 88 67 88 17



结尾无空行
```

### Sample Output 1:

```out
31



结尾无空行
```

### Sample Input 2:

```in
5 888 666 666 888 888



结尾无空行
```

### Sample Output 2:

```out
None



结尾无空行
```

```
#include<iostream>
using namespace std;
int number[100010]={0};
int name[100100];
int main(){
    int n;
    scanf("%d",&n);
    for(int i=0;i<n;i++){
        scanf("%d",&name[i]);
        number[name[i]]++;
    }
    int flag = -1;
    for(int i=0;i<n;i++){
        if(number[name[i]]==1){
            flag = name[i];
            break;
        }
        
    }
    if(flag==-1)printf("None");
    else printf("%d",flag);
    return 0;
}
```

