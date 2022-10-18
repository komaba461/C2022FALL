# 2022秋 C语言程序设计 作业01


## A1-1 分支结构练习：三数排序
```c
#include <stdio.h>
#include <math.h>

int main() {
	int a, b, c, t;
	scanf("%d %d %d", &a, &b, &c);
	if (a < b) {
		t = a;
		a = b;
		b = t;
	}
	if (a < c) {
		t = a;
		a = c;
		c = t;
	}
	if (b < c) {
		t = b;
		b = c;
		c = t;
	}

	printf("%d %d %d", a, b, c );
	return 0;
}
```

## A1-2 分支结构练习：三数的特征值
```c
#include <stdio.h>
#include <math.h>

int main() {
	int a, b, c;
	scanf("%d %d %d", &a, &b, &c);
	int mid, max;
	if (a < b) {
		int t = a;
		a = b;
		b = t;
	}
	if (a < c) {
		int t = a;
		a = c;
		c = t;
	}
	if (b < c) {
		int t = b;
		b = c;
		c = t;
	}
	printf("%d %d", b, a);
	return 0;
}
```

## A2-1 循环结构入门：数列求和
```c
#include <stdio.h>

int main() {
	int a, b;
	int sum = 0;
	scanf("%d %d", &a, &b);
	for (int i = a; i <= b; i++) {
		sum += i;
	}
	printf("%d", sum);
	return 0;
}
```

## A4-3 回文数专题：回文数判断
```c
#include <stdio.h>
#include <math.h>

int main() {
	int a, b, ret = 0;
	scanf("%d", &a);
	int A = a;
	do {
		b = a % 10;
		ret = ret * 10 + b;
		a /= 10;
	} while (a > 0);
	if (ret == A) {
		printf("Yes");
	} else {
		printf("No");
	}
	return 0;
}
```

## A6-3 最大公约数专题：多个分数的加法
```c
#include<stdio.h>
int gcd(int a, int b){//最大公因数

	while (b != 0){
		int r = a % b;
		a = b, b = r;
	}
	return a;
}
int main() {
	int n;
	scanf("%d", &n);
	int a[100000] = { 0 };
	int b[100000] = { 0 };
	for (int i = 0; i < n; i++){
		int x, y;
		scanf("%d", &x);
		scanf("%d",&y);
		a[i] = x;
		b[i] = y;
	}

	int mu = 1;
	int zi = 1;

	for (int i=0;i < n;i++)
		mu = mu * b[i];
	
    int sum = 0;
	for (int i = 0; i < n; i++){
		zi = a[i] * mu / b[i];
		sum = sum + zi;
	}
	int final = gcd(sum, mu);
	int final_zi = sum / final;
	int final_mu = mu / final;
	printf("%d %d", final_zi, final_mu);
	return 0;
}
```

## A4-1 回文数专题：数字之和
```c
#include<stdio.h>
int main(){
	int a;
	scanf("%d", &a);
	int temp = 0;
	int sum = 0;
	while (a != 0){
		temp = a % 10;
		sum = sum + temp;
		a = a / 10;
	}
	printf("%d", sum);
	return 0;
}
```

## A2-2 循环结构入门：斐波拉契数列
```c
#include<stdio.h>
int main(){
	int n, a = 2, b =3;
	scanf("%d", &n);
	if (n == 1) printf("1");
	else if (n == 2) printf("1 1");
	else if (n >= 3){
		printf("1 1 ");
		for (int i = 3; i <= n; i++){
			if (i % 2 == 1){
				printf("%d ", a);
				a = a + b;
			}
			else if (i % 2 == 0){
				printf("%d ", b);
				b = a + b;
			}
		}
	}
	return 0;
}
```

## P1080 xf1-3进制转换1
```c
#include<stdio.h>
int main()
{
	int n;
	scanf("%d", &n);
	int sum = 0;
	int a[100000];
	//sum为n能被2除的次数，也是输出的位数
	printf("1");

	int i = 0;
	while (n != 1)
	{
		sum++;
		int temp=0;
		temp = n % 2;
		a[i] = temp;
		i++;
		n = n / 2;
	}
	
	for (int i = sum-1; i >= 0; i--)
		printf("%d", a[i]);

	return 0;
}
```

## P1079 xf1-2最大公倍数与最小公因数
```c
#include <stdio.h>

int main()
{
    int x1,x2;
	scanf("%d %d",&x1,&x2);
	int t=x1*x2;
	while(x2!=0)
	{
		int r=x1%x2;
		x1=x2,x2=r;
	}
	int m=x1;
	int l=t/m;
	printf("%d %d",m,l);
	
	return 0;
}
```

## P1078 xf1-1两数和、积、余
```c
#include <stdio.h>

int main(){
    long int x1,x2,y1,y2,y3;
	while(scanf("%ld%ld",&x1,&x2)==2){
		y1=x1+x2;
		y2=x1*x2;
		y3=x1%x2;
	}
	printf("%ld\n%ld\n%ld\n",y1,y2,y3);
	return 0;
}
```

## P1081 xf1-4进制转换2
```c
/*
注意：此道题目二进制数x（x的长度范围1-20），即x最大可取到10^20，而long long int的范围为[-9223372036854775808,9223372036854775807],如用long long int会超出范围导致程序不通过，有两种思路：
1. 使用unsigned long long，该数据类型的范围为[0, 18446744073709551615]，满足x的长度范围要求；
2. 使用字符串输入，然后对字符串string中每一位字符char进行 char-'0' 得到每一位的值（0或1），然后进行进制转换。
*/
#include<stdio.h>
#include<string.h>
int mypow(int x, int n){
	int result=1;
	for (int i = 1; i <= n; i++) 
        result = result * x;

	return result;
}

int main(){
	char str[25];
	gets(str);
	int len = strlen(str);
	int sum = 0;
	for (int i = 0; i < len; i++)
		sum = sum + (str[len - i - 1] - 48) * mypow(2, i);

	printf("%d", sum);
	return 0;
}
```
