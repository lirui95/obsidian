1、
#include <stdio.h>
int fputc(int ch, FILE* stream)
{
	USART_SendData(USART1, (unsigned char) ch);
	while (!(USART1->ISR & USART_FLAG_TXE));
	（SR寄存器指示串口状态）
	USART_SendChar(USART1, (uint8_t)ch);
	return ch;
}


2、使用微库
#pragma 
import(__use_no_semihosting) /* 定义 _sys_exit() 以避免使用半主机模式 */
void _sys_exit(int x)
{ x = x; }
			#if 1 #include <stdio.h> /* 告知连接器不从C库链接使用半主机的函数 */ 
#pragma import(__use_no_semihosting) /* 定义 _sys_exit() 以避免使用半主机模式 */ 
		void _sys_exit(int x) { x = x; } /* 标准库需要的支持类型 */
struct __FILE { int handle; }; FILE __stdout; /* */ 
		int fputc(int ch, FILE *stream) { /* 堵塞判断串口是否发送完成 */ 
	while((USART1->ISR & 0X40) == 0); /* 串口发送完成，将该字符发送 */ 
USART1->TDR = (uint8_t) ch; return ch; } #endif