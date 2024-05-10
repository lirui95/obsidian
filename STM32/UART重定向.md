1、
#include <stdio.h>
int fputc(int ch, FILE* stream)
{
	//USART_SendData(USART1, (unsigned char) ch);
	//while (!(USART1->SR & USART_FLAG_TXE));
	USART_SendChar(USART1, (uint8_t)ch);
	return ch;
}
