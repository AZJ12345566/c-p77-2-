# c-p77-2-
c语言学习笔记p77文件预处理（2）

汇编(gcc-c test.s)将test.c文件转换为test.o文件
把汇编代码转换成了二进制代码（二进制指令）
1.形成符号表
列出符号名和地址


test.o通过连接器链接转化为test.exe分为两步
1.合并段表
每个目标文件空间分为很多段，将两个文件对应的段合并在一起就称为合并段表
elf为一种文件格式，用于组织各个.o文件，生成可执行程序的格式也是elf格式

2.符号表的合并和重定位
当两个文件夹有相同的符号，合并的时候取有效地址合并



运行环境
运行过程：
1.程序必须载入内存中，在有操作系统的环境中：一般这个操作由系统完成，在独立的系统中，程序的载入必须由手工安排，也可能是通过可执行代码置入只读来完成
2.程序的执行便开始，接着便调用main函数
3.开始执行程序代码。这个时候程序将使用一个运行时堆栈（开辟空间），存储函数的局部变量和返回地址。程序同时也可以使用静态内存，存储于静态内存中的变量在程序的整个执行过程一直保留他们的值。
4.终止程序。正常终止main函数；也有可能意外终止。


下面主要记录预编译阶段
预编译符号
#define MAX 100(这不是预定义符号)
//预定义符号
#include<stdio.h>
int main()
{
      printf("%s\n",__FILE__);//(__FILE__文件全名)
      printf("%d\n",__LINE__);//(__LINE__文件行数)
      printf("%s\n",__DATE__);//(文件日期)
      printf("%s\n",__TIME__);//(文件时间)
      
      //写日志文件
      int i=0;
      int arr[10]={0};
      FILE* pf=fopen("log.txt","w")
      for(i=0;i,10;i++)
      {
            arr[i]=i; 
            fprintf(pf,"file:%s line:%d date:%s time:%s i=%d\n",--FILE--,--LINE--,--DATE--,--TIME--,i);
      }
      for(i=0;i<10;i++)
      {
            priintf("%d",arr[i]);
      }
      return 0;
}


int main()
{
      printf("%d\n",__STDC__);//严格遵循的编译器C标准，其值为1，否则未定义
      return 0;
}



#define，#include， #pragma pack（4），#if，#ifdef，#line(这种#开头的为预处理指令)
#可以定义标识符和宏


#定义标识符 
#define MAX 100(定义数字)
#define STR "hehe"（定义字符）
#define reg register
#define do_forever for(;;)
int mian()
{
      reg int a;
      register int a;
      int main=MAX;
      int max=100;
      printf("%d\n",max);
      printf("%s\n",STR);
      return 0;
}


#define do_forever for(;;)
int main()
{
      do_forever(这是定义for循环，但是循环的是return 所以直接跳出循环)
      return 0;
}








