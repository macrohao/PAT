# 1028 List Sorting (25 分)

Excel can sort records according to any column. Now you are supposed to imitate this function.

### Input Specification:

Each input file contains one test case. For each case, the first line contains two integers *N* (≤105) and *C*, where *N* is the number of records and *C* is the column that you are supposed to sort the records with. Then *N* lines follow, each contains a record of a student. A student's record consists of his or her distinct ID (a 6-digit number), name (a string with no more than 8 characters without space), and grade (an integer between 0 and 100, inclusive).

### Output Specification:

For each test case, output the sorting result in *N* lines. That is, if *C* = 1 then the records must be sorted in increasing order according to ID's; if *C* = 2 then the records must be sorted in non-decreasing order according to names; and if *C* = 3 then the records must be sorted in non-decreasing order according to grades. If there are several students who have the same name or grade, they must be sorted according to their ID's in increasing order.

### Sample Input 1:

```in
3 1
000007 James 85
000010 Amy 90
000001 Zoe 60
```

### Sample Output 1:

```out
000001 Zoe 60
000007 James 85
000010 Amy 90
```

### Sample Input 2:

```in
4 2
000007 James 85
000010 Amy 90
000001 Zoe 60
000002 James 98
```

### Sample Output 2:

```out
000010 Amy 90
000002 James 98
000007 James 85
000001 Zoe 60
```

### Sample Input 3:

```in
4 3
000007 James 85
000010 Amy 90
000001 Zoe 60
000002 James 9
```

### Sample Output 3:

```out
000002 James 9
000001 Zoe 60
000007 James 85
000010 Amy 90
```

**鸣谢用户 wangzhj 补充数据！**

```
#include<iostream>
#include<algorithm>
#include<string.h>
using namespace std;
struct student{
    int id;
    char name[10];
    int score;
} stu[100010];

bool cmp1(student a,student b){
    return a.id<b.id;
}
bool cmp2(student a,student b){
    int s=strcmp(a.name,b.name);
    if(s!=0) return strcmp(a.name,b.name)<1;
    else return a.id<b.id;
}

bool cmp3(student a,student b){
    if(a.score!=b.score) return a.score<b.score;
    else return a.id<b.id;
}
int main(){
    int n,c;
    scanf("%d%d",&n,&c);
    for(int i=0;i<n;i++){
        scanf("%d%s%d",&stu[i].id,stu[i].name,&stu[i].score);
    }
    if(c==1) sort(stu,stu+n,cmp1);
    if(c==2) sort(stu,stu+n,cmp2);
    if(c==3) sort(stu,stu+n,cmp3);
    for(int i=0;i<n;i++){
        printf("%06d %s %d\n",stu[i].id,stu[i].name,stu[i].score);
    }
    return 0;
}
```

