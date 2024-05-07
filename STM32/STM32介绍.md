半主机模式
半主机是作用于ARM目标的一种机制，可以将来自STM32单片机应用程序的输入与输出请求传送至运行仿真器的PC主机上。使用此机制可以启用C库中的函数，如printf()和scanf()等输入与输出函数，使得PC主机的屏幕和键盘。

简单来说：**MDK上开启半主机模式需要SWO线（也就是说需要使用JTAG仿真器），通过PC电脑与STM32进行输入与输出。当目标板脱离仿真器单独运行时，需要退出半主机模式，通过串口进行输入与输出，否则程序会出现卡死等现象。（“https://www.cnblogs.com/jzcn/p/16280769.html”）

MicroLIB（微库）
	1. **来自ARM-MDK官方的解释：**MicroLib 是一个高度优化的库，适用于用 C 编写的基于 ARM 的嵌入式应用程序。与 ARM 编译器工具链中包含的标准 C 库相比，MicroLib 提供了许多嵌入式系统所需的显着代码大小优势。
	1. MicroLib 和标准 C 库之间的主要区别是：
		- MicroLib 专为深度嵌入式应用而设计。
		- MicroLib 经过优化，可以使用比使用 ARM 标准库更少的代码和数据存储器。
		- MicroLib 设计为无需操作系统即可工作，但这并不妨碍它与任何操作系统或 RTOS（例如 Keil RTX）一起使用。
		- MicroLib 不包含文件 I/O 或宽字符支持。
		- 由于 MicroLib 已经过优化以最小化代码大小，因此某些函数的执行速度将比 ARM 编译工具中可用的标准 C 库例程更慢。
		- MicroLib 和 ARM 标准库都包含在 Keil MDK-ARM 中。
	2. 使用MicroLib的优缺点
		- 使用MicroLIB，简化嵌入式开发操作，例如你用printf()函数的时候，就会从串口1输出字符串，当然也可以重定义到其他串口；
		- 使用MicroLIB会优化代码空间，但会降低某些程序的执行效率(比如: memcpy())，效率换空间；
		- 由于MicroLIB不支持浮点运算，所以在有FPU单元的MCU上，使用MicroLIB并开启FPU会让程序死机或跑飞。
		- Microlib不支持C++，在使用C++开发MCU时，首要条件是不能使用Microlib；