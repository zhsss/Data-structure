#include<stdio.h>
#include<stdlib.h>
void minmax(int a[], int len, int *max, int *min);

int main() {
	int a[] = { 1,2,3,4,5,6,7,8,9,12,13,14,16,17,21,23,55 };
	int min, max;
	minmax(a, sizeof(a) / sizeof(a[0]), &min, &max);
	printf("%d", a[0]);
	return 0;

}

void minmax(int a[], int len, int *max, int *min)//int a[]是指针，=int *a,本质上a是常量指针

{
	int i;

	printf("minamx sizeof=%lu\n", sizeof(a));
	printf("minmax=%p\n", a);

	*min = *max = a[0];

	a[0] = 100;




	int i;
	const int *p1 = &i;//值不能被修改，即i不能改变
	int const *p2 = &i;//同上
	int *const p3 = &i;//指针不能被修改，即片i可以改值，但是指针不能指向其它地方

	int *p = a;
	*(p + 1);//本质就是加上4个字节，sizeof(4),移到a[1],等于a[1]


	*p++;//提高硬件速度，=  *（p+1）

}

/*%
p表示输出这个指针，本质是字节,
%d表示后面的输出类型为有符号的10进制整形，
%u表示无符号10进制整型，
%lu表示输出无符号长整型整数 (long unsigned)*/

/************************************************************************************************
*************************************************************************************************
*************************************************************************************************/

void f(int *&x,int *y) 
{
	++x;
	++y;
}

int main()
{
	int i=1,j=1;
	int *a = &i;
	int *b = &j;
	printf("%p %p\n", a, b);
	f(a, b);
	printf("%p %p", a, b);//a发生变化，b不发生变化，a 直接引用指针本身，y是和b指向同一地方的指针，x就是a的别名
	system("pause");
}