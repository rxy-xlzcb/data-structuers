# data-structuers
1.顺序表定义：用一组连续的内存单元依次存储线性表的各元素
2.顺序表-存储结构
#include<stdio.h>
#define MAXSIZE=100               //定义最大存储空间
typedef int ElemType;            //定义一个整型数组elemtype
typedef struct{                 //定义一个结构体
	ELemType data[MAXSIZE];
	int length;                     //当前数据表中存储的数据
}SeqList;                       //结构体别名
3.顺序表-初始化
#include<stdio.h>
#define MAXSIZE 100
typedef int ElemType;

typedef struct {
ElemType data[MAXSIZE]; //占用内存字节 int相当于4*100=400
	int length;
} SeqList;

void initlist(SeqList* L)//初始化顺序表
{
	L->length = 0;//长度占用
}
	int main(){
	SeqList list; //声明 定义顺序表
	initlist(&list); //初始化顺序表 看第10行
	printf("长度占用%d\n", list.length);
	printf("占用内存%zu字节", sizeof(list.data));
	return 0;
4.顺序表-在尾部添加元素
 #include<stdio.h>
#define MAXSIZE 100
typedef int ElemType;

typedef struct {
ElemType data[MAXSIZE]; //占用内存字节 int相当于4*100=400
	int length;
} SeqList;

void initlist(SeqList* L)//初始化顺序表
{
	L->length = 0;//长度占用
}
	int appendElem(SeqList*L,ElemType e)//传入顺序表的指针和传入一个新元素e
	{
		if (L->length >= MAXSIZE)
		{
			printf("顺序表满");
			return 0;
		}
	L->data[L->length] = e;
	L->length++;
	return 1;
	}
	int main()
	{
	SeqList list; //声明 定义顺序表
	initlist(&list); //初始化顺序表 看第10行
	printf("长度占用%d\n", list.length);
	printf("占用内存%zu字节", sizeof(list.data));
	appendElem(&list, 8);
	return 0;
}



