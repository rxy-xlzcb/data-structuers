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

![image](https://github.com/user-attachments/assets/b32adbee-fae5-4112-9b07-35715ac0e796)
 
5.顺序表——添加元素（插入元素和循环遍历）
#include<stdio.h>

#define MAXSIZE 100
typedef int ElemType;

//定义一个顺序表结构体
typedef struct {
ElemType data[MAXSIZE]; //占用内存字节 int相当于4*100=400
	int length;
} SeqList;

//初始化顺序表
void initlist(SeqList* L)
{
	L->length = 0;//长度占用
}
//在尾部添加元素e
int appendElem(SeqList* L, ElemType e)
{
if (L->length >= MAXSIZE)
{
	printf("表已经满\n");//表的元素大于最大限度
	return 0;
}
L->data[L->length] = e;
L->length++;
return 1;
	}
//循环遍历
void listElem(SeqList* L)
{
	for (int i = 0; i < L->length; i++)
	{
		printf("%d", L->data[i]);
	}
	printf("\n");
	}
//插入元素e
	int insertElem(SeqList*L,int pos,ElemType e)//传入顺序表的指针定义位置position和传入一个新元素e
	{
		//一些预先判断表
		if (L->length >= MAXSIZE)
		{
			printf("表已经满\n");//表的元素大于最大限度
			return 0;
		}
		if (pos<1 || pos>L->length)//插入位置小于1或者大于数据表元素个数
		{
			printf("插入位置错误\n");
			return 0;
		}
		if (pos <= L->length)  //插入的位置小于等于数据表元素的个数才可以插入
		{
			for (int i = L->length - 1; i >= pos - 1; i--)
				L->data[i + 1] = L->data[i];//方括号表示下标
		}
		L->data[pos - 1] = e;//从一开始数，如要插入第五个位置数组下标是4（减1）
		L->length++;
			return 0;
		}
	
	int main()
	{
//声明一个线性表并初始化
	SeqList list; //声明 定义顺序表
	initlist(&list); //初始化顺序表 看第10行
	printf("长度占用%d\n", list.length);
	printf("占用内存%zu字节\n", sizeof(list.data));
	appendElem(&list, 88);
	appendElem(&list, 45);
	appendElem(&list, 43);
	appendElem(&list, 17);
	listElem(&list);//原来未插入的
	insertElem(&list, 2, 18);
	listElem(&list);//插入18后的
	return 0;
}
 ![image](https://github.com/user-attachments/assets/3f1a860c-a810-4a5f-be3d-8724b1f622c6)

顺序表插入最好的时间复杂度是：O（1）插入在最后面的位置，只执行一次，只有一个数据向后挪，一共挪1次
顺序表插入最坏的时间复杂度是：O（n）最最坏插入在第一个位置，所有数据都要向后挪，一共挪n次




