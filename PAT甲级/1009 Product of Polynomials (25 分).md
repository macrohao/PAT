# 1009 Product of Polynomials (25 分)

This time, you are supposed to find *A*×*B* where *A* and *B* are two polynomials.

### Input Specification:

Each input file contains one test case. Each case occupies 2 lines, and each line contains the information of a polynomial:

*K* *N*1 *a**N*1 *N*2 *a**N*2 ... *N**K* *a**N**K*

where *K* is the number of nonzero terms in the polynomial, *N**i* and *a**N**i* (*i*=1,2,⋯,*K*) are the exponents and coefficients, respectively. It is given that 1≤*K*≤10, 0≤*N**K*<⋯<*N*2<*N*1≤1000.

### Output Specification:

For each test case you should output the product of *A* and *B* in one line, with the same format as the input. Notice that there must be **NO** extra space at the end of each line. Please be accurate up to 1 decimal place.

### Sample Input:

```in
2 1 2.4 0 3.2
2 2 1.5 1 0.5结尾无空行
```

### Sample Output:

```out
3 3 3.6 2 6.0 1 1.6



结尾无空行
```

```
#include<iostream>
using namespace std;
double a[1010]={0},b[1010]={0},c[2020]={0};
int main(){
    int m,n,x,cnt=0;
    double y;
    cin>>m;
    for(int i=0;i<m;i++){
       scanf("%d %lf",&x,&y);
        a[x]=y;
    }  
    cin>>n;
    for(int i=0;i<n;i++){
       scanf("%d %lf",&x,&y);
        b[x]=y;
    } 
    int j;
    for(int i=0;i<=1000;i++){
      for(j=0;j<=1000;j++){
          if(a[i]!=0&&b[j]!=0){
              c[i+j] += a[i]*b[j];
          }
      }
    }
     for(int i=0;i<=2000;i++){
     	if(c[i])
		 cnt++;
	 }
    printf("%d",cnt);
    for(int i=2000;i>=0;i--){
    	if(c[i]!=0) 
        	printf(" %d %.1f",i,c[i]);
    }
    return 0;
}
```

