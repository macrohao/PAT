# 1082 Read Number in Chinese (25 分)

Given an integer with no more than 9 digits, you are supposed to read it in the traditional Chinese way. Output `Fu` first if it is negative. For example, -123456789 is read as `Fu yi Yi er Qian san Bai si Shi wu Wan liu Qian qi Bai ba Shi jiu`. Note: zero (`ling`) must be handled correctly according to the Chinese tradition. For example, 100800 is `yi Shi Wan ling ba Bai`.

### Input Specification:

Each input file contains one test case, which gives an integer with no more than 9 digits.

### Output Specification:

For each test case, print in a line the Chinese way of reading the number. The characters are separated by a space and there must be no extra space at the end of the line.

### Sample Input 1:

```in
-123456789



结尾无空行
```

### Sample Output 1:

```out
Fu yi Yi er Qian san Bai si Shi wu Wan liu Qian qi Bai ba Shi jiu



结尾无空行
```

### Sample Input 2:

```in
100800



结尾无空行
```

### Sample Output 2:

```out
yi Shi Wan ling ba Bai



结尾无空行
```

```
#include <cstdio>
#include <cstring>
int main()
{
    char digit[10][5] = { "ling", "yi", "er", "san", "si", "wu", "liu", "qi", "ba", "jiu" }, place1[3][5] = { "", " Wan", " Yi" }, place2[4][6] = { "", " Shi", " Bai", " Qian" }, str[10];
    int num;
    scanf("%d", &num);
    if( num <= 0 )
    {
        printf("%s", num < 0 ? "Fu ":"ling");
        num *= -1;
    }
    sprintf(str, "%d", num);
    for( int i = 0, zero = 0, tag = 0, j = strlen(str) - 1; i < strlen(str); ++i, --j )
    {
        if( str[i] == '0' )
            zero = 1;
        else
        {
            printf("%s%s%s%s", i ? " ":"", zero ? "ling ":"", digit[ str[i] - '0' ], place2[j % 4]);
            tag = 1;
            zero = 0;
        }
        if( j % 4 == 0 && tag )
        {
            printf("%s", place1[ j / 4 ]);
            tag = 0;
        }
    }
}


```

