# 1006 Sign In and Sign Out (25 分)

At the beginning of every day, the first person who signs in the computer room will unlock the door, and the last one who signs out will lock the door. Given the records of signing in's and out's, you are supposed to find the ones who have unlocked and locked the door on that day.

### Input Specification:

Each input file contains one test case. Each case contains the records for one day. The case starts with a positive integer *M*, which is the total number of records, followed by *M* lines, each in the format:

```
ID_number Sign_in_time Sign_out_time
```

where times are given in the format `HH:MM:SS`, and `ID_number` is a string with no more than 15 characters.

### Output Specification:

For each test case, output in one line the ID numbers of the persons who have unlocked and locked the door on that day. The two ID numbers must be separated by one space.

Note: It is guaranteed that the records are consistent. That is, the sign in time must be earlier than the sign out time for each person, and there are no two persons sign in or out at the same moment.

### Sample Input:

```in
3
CS301111 15:30:28 17:00:10
SC3021234 08:00:00 11:25:25
CS301133 21:45:00 21:58:40结尾无空行
```

### Sample Output:

```out
SC3021234 CS30113
```

```
#include<iostream>
using namespace std;

struct time{
    char id[20];
    int hour1,minute1,second1;
    int hour2,minute2,second2;
} temp,earlist,latst;

bool early(struct time a,struct time b){
    if(a.hour1!=b.hour1)
        return a.hour1 < b.hour1;
    else if(a.minute1 != b.minute1)
        return a.minute1 < b.minute1;
    else
    	return a.second1 < b.second1;
}

bool late(struct time a,struct time b){
    if(a.hour2!=b.hour2)
        return a.hour2 > b.hour2;
    else if(a.minute2 != b.minute2)
        return a.minute2 > b.minute2;
    else
    	return a.second2 > b.second2;
}

int main(){
    int n;
    cin>>n;
    earlist.hour1=24;
    earlist.minute1=60;
    earlist.second1=60;
    latst.hour2=0;
    latst.minute2=0;
    latst.second2=0;
 
    while(n--){
        scanf("%s %d:%d:%d %d:%d:%d",temp.id ,&temp.hour1 ,&temp.minute1 ,&temp.second1 ,&temp.hour2 ,&temp.minute2 ,&temp.second2);
        if(late(temp,latst))
            latst = temp;
        if(early(temp,earlist))
            earlist = temp;
    }
    printf("%s %s",earlist.id,latst.id);
  
    return 0;
}
```

