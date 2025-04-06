1.请写出bool flag  与“零值”比较的if  语句:
答案:
if (flag);
if (!flag)
2.请写出float  x   与“零值”比较的if  语句:
答案:
const float EPSINON = 0.00001;
if ((x >= - EPSINON) && (x <= EPSINON))
3.请写出char  *p   与“零值”比较的if  语句:
答案:
if(p= =NULL);
if(p!=NULL)
4.以下为Linux下的32 位C 程序，请计算sizeof 的值。
char str[] = “Hello” ;                               
char *p = str ;                                      
int  n = 10;
请计算:
(1)sizeof(str) =                  
(2)sizeof(p) =                 
(3)sizeof(n) =
(4)void Func(char str[100])                           
{                                          
	…… ;                                                            
}                                          
请计算sizeof( str ) = 
(5)void *p=malloc(100);
sizeof( p )=
结果:
(1)sizeof(str)=6
(2)sizeof(p)=4
(3)sizeof(n)=4
(4)sizeof(str)=4
(5)sizeof(p)=4
4.用变量a 给出下面的定义
--一个有10个指针的数组，该指针是指向一个整型数的;
--一个指向有10个整型数数组的指针;
--一个指向函数的指针，该函数有一个整型参数并返回一个整型数;
--一个有10个指针的数组，每个指针指向一个函数，该函数有一个整型参数并返回一个整型数;
答案:
--int * a[10];
--int (*a)[10]
--int (*a)(int);
--int (*a[10])(int)
5.设有以下说明和定义：
typedef union 
{
	long i; 
	int k[5]; 
	char c;
} DATA;
struct data 
{ 
	int cat; 
	DATA cow; 
	double dog;
} too;
DATA max;
printf("%d",sizeof(struct data)+sizeof(max));
答案:
52/64
