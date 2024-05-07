printf函数调用fput来发送数据 
所以实际上是fputc重定向 
（为保证效率 以寄存器完成）以下为判断是否发送完毕
![[Pasted image 20240507170231.png]]
int fputc(int ch, FILE *stream)
{
    /* 堵塞判断串口是否发送完成 */
    while((USART1->ISR & 0X40) == 0);

    /* 串口发送完成，将该字符发送 */
    USART1->TDR = (uint8_t) ch;

    return ch;
}

标准库函数
printf 函数使用了半主机模式，所以直接使用标准库会导致程序无法运行，因此必须提前告知编译器不使用半主机模式： 什么是半主机模式？
	#pragma import(__use_no_semihosting) /* 定义 _sys_exit() 以避免使用半主机模式 */ void _sys_exit(int x) { x = x; }
#if 1
#include <stdio.h>

/* 告知连接器不从C库链接使用半主机的函数 */
#pragma import(__use_no_semihosting)

/* 定义 _sys_exit() 以避免使用半主机模式 */
void _sys_exit(int x)
{
    x = x;
}
/* 标准库需要的支持类型 */
struct __FILE
{
    int handle;
};
FILE __stdout;
/*  */
int fputc(int ch, FILE *stream)
{
    /* 堵塞判断串口是否发送完成 */
    while((USART1->ISR & 0X40) == 0);

    /* 串口发送完成，将该字符发送 */
    USART1->TDR = (uint8_t) ch;

    return ch;
}

#endif

