# 1038 Recover the Smallest Number (30 分)

Given a collection of number segments, you are supposed to recover the smallest number from them. For example, given { 32, 321, 3214, 0229, 87 }, we can recover many numbers such like 32-321-3214-0229-87 or 0229-32-87-321-3214 with respect to different orders of combinations of these segments, and the smallest number is 0229-321-3214-32-87.

### Input Specification:

Each input file contains one test case. Each case gives a positive integer *N* (≤104) followed by *N* number segments. Each segment contains a non-negative integer of no more than 8 digits. All the numbers in a line are separated by a space.

### Output Specification:

For each test case, print the smallest number in one line. Notice that the first digit must not be zero.

### Sample Input:

```in
5 32 321 3214 0229 87



结尾无空行
```

### Sample Output:

```out
22932132143287



结尾无空行
```

```
#include<iostream>
#include<string>
#include<algorithm>
using namespace std;
string str[10010];
bool cmp(string a,string b){
    return a+b < b+a;
}

int main(){
    int n;
    cin>>n;
    for(int i=0;i<n;i++){
        cin>>str[i];
    }
    sort(str,str+n,cmp);
    string ans;
    for(int i=0;i<n;i++){
        ans+=str[i];
    }
    while(ans.size()>0&&ans[0]=='0'){
        ans.erase(ans.begin());
    }
    if(ans.size()==0) cout<<0;
    else cout<<ans;
    
    return 0;
}
```

