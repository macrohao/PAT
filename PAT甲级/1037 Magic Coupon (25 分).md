# 1037 Magic Coupon (25 分)

The magic shop in Mars is offering some magic coupons. Each coupon has an integer *N* printed on it, meaning that when you use this coupon with a product, you may get *N* times the value of that product back! What is more, the shop also offers some bonus product for free. However, if you apply a coupon with a positive *N* to this bonus product, you will have to pay the shop *N* times the value of the bonus product... but hey, magically, they have some coupons with negative *N*'s!

For example, given a set of coupons { 1 2 4 −1 }, and a set of product values { 7 6 −2 −3 } (in Mars dollars M$) where a negative value corresponds to a bonus product. You can apply coupon 3 (with *N* being 4) to product 1 (with value M$7) to get M$28 back; coupon 2 to product 2 to get M$12 back; and coupon 4 to product 4 to get M$3 back. On the other hand, if you apply coupon 3 to product 4, you will have to pay M$12 to the shop.

Each coupon and each product may be selected at most once. Your task is to get as much money back as possible.

### Input Specification:

Each input file contains one test case. For each case, the first line contains the number of coupons *N**C*, followed by a line with *N**C* coupon integers. Then the next line contains the number of products *N**P*, followed by a line with *N**P* product values. Here 1≤*N**C*,*N**P*≤105, and it is guaranteed that all the numbers will not exceed 230.

### Output Specification:

For each test case, simply print in a line the maximum amount of money you can get back.

### Sample Input:

```in
4
1 2 4 -1
4
7 6 -2 -3结尾无空行
```

### Sample Output:

```out
43



结尾无空行
```

```
#include<iostream>
#include<algorithm>
using namespace std;
bool cmp(int a,int b){
    return a > b;
}
int c[100010],p[100010];
int main(){
    int nc,np;
    scanf("%d",&nc);
    for(int i=0;i<nc;i++){
        scanf("%d",&c[i]);
    }
    scanf("%d",&np);
    for(int i=0;i<np;i++){
        scanf("%d",&p[i]);
    }
    sort(c,c+nc,cmp);
    sort(p,p+np,cmp);
    int sum=0;
    for(int i=0,j=0;c[i]>=0&&p[j]>=0;i++,j++){
        int temp = c[i]*p[j];
        if(temp>0) sum+=temp;
        else break;
    }
    for(int i=nc-1,j=np-1;c[i]<0&&p[j]<0;i--,j--){
        int temp = c[i]*p[j];
        if(temp>0) sum+=temp;
        else break;
    }
    printf("%d",sum);
    return 0;
}
```

