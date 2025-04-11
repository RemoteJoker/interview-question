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

6.请问以下代码有什么问题：
int main()
{
char a;
char *str=& a;
strcpy(str,"hello");
printf(str);
return 0;
}
答案：没有为str分配内存空间，将会发生异常问题出在将一个字符串复制进一个字符变量指针所指地址。虽然可以正确输出结果，但因为越界进行内在读写而导致程序崩溃。

7.请问以下代码有什么问题：
char * s ="AAA";
printf("%s",s);
s[0]='B';
printf("%s",s);
有什么错？
答案：“AAA” 是字符串常量。s是指针，指向这个字符串常量，所以声明s的时候就有问题。cosnt char * s =“AAA”;然后又因为是常量，所以对是s[0] 的赋值操作是不合法的。

8.int (*s[10])(int)  表示的是什么
答案：int (*s[10])(int) 函数指针数组，每个指针指向一个int func ( int param) 的函数。（或一个有10个指针的数组，每个指针指向一个函数，该函数有一个整型参数并返回一个整型数）

9.c和c++ 中的struct有什么不同？
1
答案：c和c++ 中struct的主要区别是c中的struct不可以含有成员函数，而c++ 中的struct可以。c++ 中struct和class的主要区别在于默认的存取权限不同，struct默认为public ，而class默认为private

10.void getmemory(char *p)
{
	p=(char *) malloc(100);
	strcpy(p,“hello world”);
}
int main( )
{
	char *str=NULL;
	getmemory(str);
	printf(“%s/n”,str);
	free(str);
	return 0;
} 会出现什么问题？
1
2
3
4
5
6
7
8
9
10
11
12
13
答案：程序崩溃，getmemory中的malloc 不能传递动态内存，所以str一直是NULL，free ()对str操作很危险。

11.char szstr[10];
strcpy(szstr,"0123456789");
产生什么结果？为什么？
1
2
3
答案：长度不一样，出现段错误。字符串多一个’\0’结束符。

12.数组和链表的区别？
1
答案：
数组：数据顺序存储，固定大小；
链表：数据可以随机存储，大小可动态改变。

13.void main()
{
	char aa[10];
	printf(“%d”,strlen(aa));
}                                          
会出现什么问题？打印结果是是多少？
1
2
3
4
5
6
答案：sizeof()和初不初始化没有关系，strlen()和初始化有关，打印结果值未知。

14.给定结构
struct A
{
	char t:4;
	char k:4;
	unsigned short i:8;
	unsigned long m;
}; 问sizeof(A) = ?
1
2
3
4
5
6
7
8
答案：8
详解：char t:4;是代表使用位域结构，表示使用char的其中四位，char k:4;刚好可以把剩下四位用掉（假如不够则要重新使用一个char），所以一共是char(1)+short(2)+long(4)=7,字节对齐（char和short占一个字，long占一个字）后为8。

15.struct name1
{
	char str;
	short x;
	int num;
} ;求sizeof(name1)?
1
2
3
4
5
6
答案：8
详解：char(1)+short(2)+int(4)=7，字节对齐（char和short占一个字，int占一个字）后为8。

16.struct name2
{
	char str;
	int num;
	short x;
}; 求sizeof(name2)？
1
2
3
4
5
6
答案：12
详解：char(1)占第一个字中的1，第一个字剩下3不够int(4)，所以为了对齐，重新用一个字，int(4)刚好占满这第二个字，所以short(2)又要重新用一个字（其实只用了前2），一共是4+4+4=12。

17.程序哪里有错误
wap( int *p1,int *p2 )
{
	int  *p;
	*p = *p1;
	*p1 = *p2;
	*p2 = *p;
}
1
2
3
4
5
6
7
8
答案：申请p的时候没有初始化，所以p为野指针。

19.(void *)ptr 和(*(void**))ptr 的结果是否相同？其中ptr为同一个指针。
1
答案：(void )ptr 和((void**))ptr 值是相同的
详解：个人理解，void前面的*是取该地址内容的，所以本质一样。

20.要对绝对地址0x100000赋值，我们可以用
(unsigned int*)0x100000 = 1234;
那么要是想让程序跳转到绝对地址是0x100000去执行，应该怎么做？
1
2
3
答案：((void ()( ))0x100000 ) ( );首先要将0x100000强制转换成函数指针,即:
(void (*)())0x100000
然后再调用它:
((void ()())0x100000)();

27.关键字volatile有什么含意? 并给出三个不同的例子。
1
答案：一个定义为volatile的变量是说这变量可能会被意想不到地改变，这样，编译器就不会去假设这个变量的值了。精确地说就是，优化器在用到这个变量时必须每次都小心地重新读取这个变量的值，而不是使用保存在寄存器里的备份。下面是volatile变量的几个例子：
1). 并行设备的硬件寄存器（如：状态寄存器）
2). 一个中断服务子程序中会访问到的非自动变量(Non-automatic variables)
3). 多线程应用中被几个任务共享的变量

28.嵌入式系统经常具有要求程序员去访问某特定的内存位置的特点。在某工程中，要求设置一绝对地址为0x67a9的整型变量的值为0xaa66。编译器是一个纯粹的ANSI编译器。写代码去完成这一任务。
1
答案：这一问题测试你是否知道为了访问一绝对地址把一个整型数强制转换（typecast ）为一指针是合法的。这一问题的实现方式随着个人风格不同而不同。典型的类似代码如下：
int * ptr;
ptr= (int *)0x67a9;
*ptr = 0xaa66;

29.头文件中的ifndef/define/endif 干什么用？
1
答案：防止该头文件被重复引用。

30.#include  <filename.h>    和	#include  “filename.h” 有什么区别？
1
答案：对于#include <filename.h> ，编译器从标准库路径开始搜索filename.h ; 对于#include “filename.h” ，编译器从用户的工作路径开始搜索filename.h 。

31.const   有什么用途？（请至少说明两种）
1
答案：(1)可以定义const 常量（2）const 可以修饰函数的参数、返回值，甚至函数的定义体。被const 修饰的东西都受到强制保护，可以预防意外的变动，能提高程序的健壮性。

32.static有什么用途？（请至少说明两种）
1
答案：
1 限制变量的作用域（static全局变量）；
2 设置变量的存储域（static局部变量）。

33.堆栈溢出一般是由什么原因导致的？
1
答案：没有回收垃圾资源。

34.如何引用一个已经定义过的全局变量？
1
答案：可以用引用头文件的方式，也可以用extern 关键字，如果用引用头文件方式来引用某个在头文件中声明的全局变理，假定你将那个变量写错了，那么在编译期间会报错，如果你用extern 方式引用时，假定你犯了同样的错误，那么在编译期间不会报错，而在连接期间报错。

35.全局变量可不可以定义在可被多个.C 文件包含的头文件中？为什么？
1
答案：可以，在不同的C 文件中以static形式来声明同名全局变量。可以在不同的C文件中声明同名的全局变量，前提是其中只能有一个C文件中对此变量赋初值，此时连接不会出错。

36.队列和栈有什么区别？
1
答案：队列先进先出，栈后进先出。

37.Heap与stack的差别。
1
答案：Heap是堆，stack是栈。Stack的空间由操作系统自动分配/释放，Heap上的空间手动分配/释放。Stack空间有限，Heap是很大的自由存储区C 中的malloc 函数分配的内存空间即在堆上,C++中对应的是new 操作符。程序在编译期对变量和函数分配内存都在栈上进行,且程序运行过程中函数调用时参数的传递也在栈上进行。

38.用宏定义写出swap（x，y），即交换两数。
1
答案：
#define swap(x, y) (x)=(x)+(y);(y)=(x)–(y);(x)=(x)–(y);

39.写一个“标准”宏，这个宏输入两个参数并返回较小的一个。
1
答案：
#define Min(X, Y) ((X)>(Y)?(Y):(X))// 结尾没有 ;

40.带参宏与带参函数的区别(至少说出5点)？
1
答案：

	  带参宏	    带参函数
1
处理时间------编译时------- 运行时

参数类型 ----- 无-------------需定义

程序长度 ------变长----------不变

占用存储空间-否 ----------- 是

运行时间-------不占运行时间–调用和返回时占

41.关键字volatile有什么含意？
1
答案：提示编译器对象的值可能在编译器未监测到的情况下改变。

42.int main()
{
	int x=3;
	printf("%d",x);
	return 1;
}
问函数既然不会被其它函数调用，为什么要返回1？
1
2
3
4
5
6
7
答案：mian中，c标准认为0表示成功，非0表示错误。具体的值是某中具体出错信息。

43.已知一个数组table ，用一个宏定义，求出数据的元素个数。
1
答案：
#define NTBL(table) (sizeof(table)/sizeof(table[0]))

44.A.c 和B.c两个c文件中使用了两个相同名字的static变量,编译的时候会不会有问题?
这两个static变量会保存到哪里（栈还是堆或者其他的）?
1
2
答案：static的全局变量，表明这个变量仅在本模块中有意义，不会影响其他模块。他们都放在静态数据区，但是编译器对他们的命名是不同的。如果要使变量在其他模块也有意义的话，需要使用extern 关键字。

45.static全局变量与普通的全局变量有什么区别？
1
答案： 作用域不同，static全局变量只初使化一次，防止在其他文件单元中被引用。

46.static局部变量和普通局部变量有什么区别？
1
答案：static局部变量只被初始化一次，下一次依据上一次结果值。

47.static函数与普通函数有什么区别？
1
答案：static函数在内存中只有一份，普通函数在每个被调用中维持一份拷贝。
参考：https://blog.csdn.net/qq_22238021/article/details/79533711

48.程序的局部变量存在于（）中，全局变量存在于 （）中，动态申请数据存在于（）中。
1
答案：程序的局部变量存在于栈(stack) 中，全局变量存在于静态数据区中，动态申请数据存在于堆（heap）中。

49.什么是预编译，何时需要预编译？
1
答案：
１、总是使用不经常改动的大型代码体。
２、程序由多个模块组成，所有模块都使用一组标准的包含文件和相同的编译选项。在这种情况下，可以将所有包含文件预编译为一个预编译头。

50.用两个栈实现一个队列的功能？要求给出算法和思路！
1
答案：设2个栈为A,B, 一开始均为空.
入队:
将新元素push入栈A;
出队:
(1)判断栈B 是否为空；
(2)如果不为空，则将栈A中所有元素依次pop 出并push到栈B；
(3)将栈B 的栈顶元素pop 出；
详解：队列：先进先出，栈：先进后出

51.对于一个频繁使用的短小函数,在C 语言中应用什么实现,在C++ 中应用什么实现?
1
答案：c用宏定义，c++ 用inline

52.用预处理指令#define  声明一个常数，用以表明1年中有多少秒（忽略闰年问题）
1
答案：#define SECONDS_PER_YEAR (60 * 60 * 24 * 365)UL
详解：UL无符号长整形

53.Typedef 在C 语言中频繁用以声明一个已经存在的数据类型的同义字。
也可以用预处理器做类似的事。例如，思考一下下面的例子：
#define dPS struct s*
typedef struct s* tPS;
以上两种情况的意图都是要定义dPS 和tPS 作为一个指向结构s指针。
哪种方法更好呢？（如果有的话）为什么？
1
2
3
4
5
6
答案：第二种更好，因为在实际替换中可能出现意想不到的问题。
如：
dPS p1,p2;
tPS p3,p4;
第一个扩展为struct s * p1, p2;上面的代码定义p1为一个指向结构的指，p2为一个实际的结构，这也许不是你想要的。第二个例子正确地定义了p3 和p4 两个指针。

54.在 C++  程序中调用被C 编译器编译后的函数，为什么要加extern “C”？
1
答案：extern "C"的主要作用就是为了能够正确实现C++代码调用其他C语言代码。加上extern "C"后，会指示编译器这部分代码按C语言（而不是C++）的方式进行编译。由于C++支持函数重载，因此编译器编译函数的过程中会将函数的参数类型也加到编译后的代码中，而不仅仅是函数名；而C语言并不支持函数重载，因此编译C语言代码的函数时不会带上函数的参数类型，一般只包括函数名。

56.语句for( ; 1 ;) 有什么问题？它是什么意思？
1
答案：死循环，和while(1)相同。

57.do……while和while……do有什么区别？
1
答案：前一个循环一遍再判断，后一个判断以后再循环。

58.请写出下列代码的输出内容
#include <stdio.h>
int main()
{
	int a,b,c,d;
	a=10;
	b=a++;
	c=++a;
	d=10*a++;
	printf("b，c ，d：%d，%d，%d"，b，c，d ）;
	return 0;
}
1
2
3
4
5
6
7
8
9
10
11
12
答案：10，12，120
详解：
b=a++;可以拆解为
b=a;
a++;
所以这一句运行后b=10;a=11;
c=++a;可以拆解为
++a;
c=a;
所以这一句运行后b=10;a=12;c=12;
d=10a++;可以拆解为
d=10a;
a++;
所以最后a=13;b=10;c=12;d=120;

59.unsigned char *p1;
unsigned long *p2;
p1=(unsigned char *)0x801000;
p2=(unsigned long *)0x810000;
请问p1+5= ;
p2+5= ;
1
2
3
4
5
6
答案：
p1+5=0x801005;
p2+5=0x810014;

60.main()
{
	int a[5]={1,2,3,4,5};
	int * ptr=(int*)(&a+1);
	printf(“%d，%d”,*(a+1),*(ptr-1));
}
请问输出：
1
2
3
4
5
6
7
答案：2，5
详解：a代表数组首地址，即* a=1，* (a+1)=2
&a代表数组指针，其类型为int (*)[5]，所以&a+1可以理解为在数组指针的基础上偏移为5，然后强制转换为int类型的指针赋给ptr，所以是下个数组的首地址，ptr-1即为上个数组的最后一位，所以是a[4]=5

61.请问下面程序有什么错误?
int a[60][250][1000],i,j,k;
for(k=0;k<=1000;k++)
for(j=0;j<250;j++)
for(i=0;i<60;i++)
a[i][j][k]=0;
1
2
3
4
5
6
2022-12-28：感谢评论区反馈
答案：
对于k的判断多了一个等号，会导致溢出。正确的应该如下：
int a[60][250][1000],i,j,k;
for(k=0;k<1000;k++)
for(j=0;j<250;j++)
for(i=0;i<60;i++)
a[i][j][k]=0;

62.以下是求一个数的平方的程序,请找出错误:
#define SQUARE(a)((a)*(a))
int a=5;
int b;
b=SQUARE(a++);
1
2
3
4
5
答案：在替换后b=((a++) * (a++))，算得b=(5 * 6)=30。可能在不同编译器下得到不同答案。

63.#define Max_CB 500
void LmiQueryCSmd(StructMSgCB * pmsg)
{
	unsigned char ucCmdNum;
	......  
	for(ucCmdNum=0;ucCmdNum<Max_CB;ucCmdNum++)
	{
		......;
	}                                          
} 这段代码执行有什么问题？
1
2
3
4
5
6
7
8
9
10
答案：死循环，因为unsigned char 的取值范围在0~255之间，所以ucCmdNum永远小于Max_CB。

64.嵌入式系统中经常要用到无限循环，你怎么用C编写死循环。
1
答案：while(1);或者for ( ;1;) ;

67.
int x;
int modifyvalue()
{ 
	return(x+=10);
}
int changevalue(int x)
{
	return(x+=1);
}
void main()
{
	int x =10;
	x++;
	changevalue(x);
	x++;
	modifyvalue();
	printf("First output:%dn",x);
	x++;
	changevalue(x);
	printf("Second output:%dn",x);
	modifyvalue();
	printf("Thirdoutput:%dn",x);
}输出?

1
2
3
4
5
6
7
8
9
10
11
12
13
14
15
16
17
18
19
20
21
22
23
24
答案：12,13,13
详解：modifyvalue()里面的x相当于全局变量x，而不是main()函数内的局部变量x。而changevalue()函数我们可以理解为：
int changevalue( int x)
{
int a;
a=x;
return(a+=1);
}
函数内部参与运算的是形参，所以实参没有改变。

68.不能做switch()的参数类型是：
1
答案：switch 的参数不能为实型。

69.请写出下列代码的输出内容
＃include <stdio.h>
main()
{
	int a,b,c,d;
	a=10;
	b=a++;
	c=++a;
	d=10*a++;
	printf("b，c ，d：%d，%d，%d"，b，c，d ）;
	return 0;
}
1
2
3
4
5
6
7
8
9
10
11
12
答案：10，12，120

71.一语句实现x是否为2 的若干次幂的判断。
1
答案：
void main()
{
int a;
scanf(“%d”,&a);
printf(“%c”,(a)&(a-1)?’n’:’y’); // 若是打印y，否则n
}
详解：(a)&(a-1)?‘n’:‘y’;意思是(a)&(a-1)结果为1则输出n，结果为0则输出y

72.中断是嵌入式系统中重要的组成部分，这导致了很多编译开发商提供一种扩展—让标准C 支持中断。具代表事实是，产生了一个新的关键字__interrupt 。下面的代码就使用了__interrupt 关键字去定义了一个中断服务子程序(ISR)，请评论一下这段代码的。
__interrupt double compute_area (double radius)
{
	double area = PI * radius * radius;
	printf(" Area = %f", area);
	return area;
}
1
2
3
4
5
6
7
答案：
（1）中断不能有入参和返回值；
（2）在许多的处理器/编译器中，浮点一般都是不可重入的。有些处理器/编译器需要让额外的寄存器入栈，有些处理器/编译器就是不允许在ISR 中做浮点运算。此外，ISR 应该是短而有效率的，在ISR 中做浮点运算是不明智的；
（3）与第三点一脉相承，printf() 经常有重入和性能上的问题。

73.下面的代码输出是什么，为什么？
void foo(void)
{
	unsigned int a = 6;
	int b = -20;
	(a+b> 6)? puts("> 6") : puts("<= 6");
}
1
2
3
4
5
6
7
答案：>6
详解：当有符号和无符号运算时，统一转换为无符号，而在有符号的情况下是将最高位置1来表示负数，所以负数转为无符号时将会是一个很大的数。

74.评价下面的代码片断：
unsigned int zero = 0;
unsigned int compzero =  0xFFFF;
/*1‘s complement of zero */
1
2
3
4
答案：当int不是32位环境下，不能符合预期结果。正确的应该时unsigned int compzero = ~0;

75.下面的代码片段的输出是什么，为什么？
char *ptr;
if ((ptr = (char *)malloc(0)) == NULL)
	puts("Gota null pointer");
else
	puts("Gota valid pointer");
1
2
3
4
5
6
答案：Gota valid pointer

76.编写strcpy 函数
已知strcpy 函数的原型是 char *strcpy(char *strDest, const char *strSrc);其中strDest是目的字符串，strSrc 是源字符串。
1
2
答案：

char *strcpy(char *strDest, const char *strSrc)
{    
	char *p=strDest;    
	assert(strDest!=NULL&&strSrc!=NULL);    
	while((*p++=*strSrc++)!='\0');    
	return strDest;
}

77.写出二分查找的代码。
答案：

int binary_search(int* arr, int key, int n)
{    
	int low=0;    
	int high=n-1;    
	int mid;     
	while(low<=high)    
	{        
		mid=(low+high)/2;        
		if(key>arr[mid])        
		{            
			low=mid+1;        
		}        
		else if(key<arr[mid])        
		{            
			high=mid-1;        
		}       
	 	else        
	 	{            
	 		return mid;        
	 	}            
	}    
	return -1;
}
1
2
3
4
5
6
7
8
9
10
11
12
13
14
15
16
17
18
19
20
21
22
23
78.请编写一个C 函数，该函数给出一个字节中被置1 的位的个数。
答案：

int sum(unsigned char byte)
{    
	int n=0;    
	for(int i=0;i<8;i++)    
	{        
		if(byte&1<<i)        
		n++;    
	}    
	return n;
}
1
2
3
4
5
6
7
8
9
10
79.请编写一个C 函数，该函数将给定的一个字符串转换成整数。
答案：

int strtonum(char *str)
{    
	int num=0;    
	assert(str!=NULL);    
	while((*str)!='\0')    
	{        
		num=num*10;        
		num=num+(*str-48);        
		str++;    
	}    
	return num;
	}
1
2
3
4
5
6
7
8
9
10
11
12
80.请编写一个C 函数，该函数将给定的一个整数转换成字符串。
答案：int numtostr(int n,char *s)
{    
	int len=0;    
	int oldn=n;    
	assert(s!=NULL);    
	while(n!=0)    
	{        
		n=n/10;        
		len++;    
	}    
	*(s+len)='\0';    
	for(;len>0;len--)    
	{        
		*(s+len-1)=oldn%10+'0';       
		oldn=oldn/10;    
	}    
	return 0;
	}
81.实现strcmp 函数。
答案：

int strcmp(const char *str1,const char *str2)
{    /*不可用while(*str1++==*str2++)来比较，当不相等时仍会执行一次++，    return返回的比较值实际上是下一个字符。应将++放到循环体中进行。*/    
	while(*str1 == *str2)    
	{                
		assert((str1 != NULL) && (str2 != NULL));                        
		if(*str1 == '\0')            
		return 0;                
		str1++;        
		str2++;    
	}    
	return *str1 - *str2;
}
1
2
3
4
5
6
7
8
9
10
11
12
82.请编写一个C 函数，该函数将一个字符串逆序。
答案：

int AntitoneValue(char *father,char *child)
{    
	assert(father!=NULL);    
	char s[100];    
	int i,j;        
	while(father[j]) //放入source ，[j] 为长度    
	{         
		s[j] = father[j];         
		j++;         
		if(j > 99)         
		return -1;     
	}     
	s[j] = '\0';     
	for(i=0; i<j; i++)     
		child[i] = s[j-i-1];  // 反序    
	child[i] = '\0';     
	return 0;
	}
1
2
3
4
5
6
7
8
9
10
11
12
13
14
15
16
17
18
83.请编写一个C 函数，该函数在给定的内存区域搜索给定的字符，并返回该字符所在位置索引值。
答案：

int search(char *head,int n,char key)
{    
	assert(head!=NULL);    
	for(int i=0;i<n;i++)    
	{       
		if(*(head+i)==key)            
		return i;    
	}    
	return -1;
}
1
2
3
4
5
6
7
8
9
10
84.请编写一个C 函数，该函数在一个字符串中找到可能的最长的子字符串，该字符串是由同一字符组成的。

85.怎么判断链表中有环？

int linkringtest(list *head)
{
    list *t1=head;
    list *t2=head;
    while(t1->next&&t2->next){
        t1=t1->next;
        if(t2=t2->next->next==NULL){
            return 0;
        }
        if(t1==t2){
            return 1;
        }
    }
    return 0;
}
1
2
3
4
5
6
7
8
9
10
11
12
13
14
15
86.有一浮点型数组A，用C语言写一函数实现对浮点数组A进行降序排序，并输出结果，要求要以数组A 作为函数的入口。

87.实现双向链表删除一个节点P，在节点P后插入一个节点，写出这两个函数。

88.把一个链表反向。

89.将二维数组行列元素互换，存到另一个数组中。

90.输入一行字符，统计其中有多少个单词。

91.写一个内存拷贝函数，不用任何库函数。

92.有1、2、3、4个数字，能组成多少个互不相同且无重复数字的三位数？都是多少？

93.取一个整数a从右端开始的4~7位。

94.打印出杨辉三角。要求打印出10行。

95.实现strcmp函数。

96.写一个函数，求一个字符串的长度，在main函数中输入字符串，并输出其长度。

int lenofstr(char *s)
{
    int len=0;
    while(*s){
        s++;
        len++;
    }
    return len;
}
1
2
3
4
5
6
7
8
9
97.809*？？=800*？？+9*？？+1其中？？代表两位数，8*？？的结果为两位数，9*？？的结果为三位数。求？？代表的两位数，及809*？？后的结果。
int main()
{
    int i=10;
    while_:
    while(809*i!=800*i+9*i+1){
        if(8*i>9&&8*i<100&&9*i>99&&9*i<1000){
            i++;
        }else{
            printf("There is no satisfactory result!");
            return -1;            
        }
        if(i>99){
            printf("There is no satisfactory result!");
            return -1;
        }
    }
    printf("%d is satisfied!\r",i);
    if(i<100)   goto while_;
    return 0;
}
98.某个公司采用公用电话传递数据，数据是四位的整数，在传递过程中是加密的，加密规则如下：每位数字都加上5，然后用和除以10的余数代替该数字，再将第一位和第四位交换，第二位和第三位交换。

int encryption_num(int data)
{
    int tmp[4];
    int tmp_;
    int i=0;
    for(;i<4;i++){
        tmp[i]=data%10;
        tmp[i]=(tmp[i]+5)%10;
        data=data/10;
    }
    tmp_=tmp[3]+tmp[2]*10+tmp[1]*100+tmp[0]*1000;
    return tmp_;
}
1
2
3
4
5
6
7
8
9
10
11
12
13
99.计算字符串中子串出现的次数。

int lookforstr(char *s1,char *s2)
{
    int s11=0,s22=0;
    int len=0,num=0;
    if(s1==NULL||s2==NULL){
        return -1;
    }else{
        while(*(s2+len)){
            len++;
        }
        while(*s1){
            while(*(s1+s11)==*(s2+s22)&&(*(s2+s22)!=0)){
                s11++;
                s22++;
            }
            if(len==s22){
                num++;
            }
            s11=0;
            s22=0;
            s1++;
        }
    }
    return num;
}
1
2
3
4
5
6
7
8
9
10
11
12
13
14
15
16
17
18
19
20
21
22
23
24
25
100.有两个磁盘文件A和B，各存放一行字母，要求把这两个文件中的信息合并（按字母排序），输出到一个新文件C中。